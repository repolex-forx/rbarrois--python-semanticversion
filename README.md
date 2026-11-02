# Repolex Knowledge Graph of rbarrois/python-semanticversion

RDF knowledge graph data for [rbarrois/python-semanticversion](https://github.com/rbarrois/python-semanticversion), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download rbarrois/python-semanticversion
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 2cbbee3154d9011cee873ae3a020cd17c669f6df
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 2cbbee3154d9011cee873ae3a020cd17c669f6df
│           └── chunk-001.nq.gz
├── blob
│   ├── 02a989b6c1a4182d302c31564647df0986acc1d5.nq.gz
│   ├── 135ee6818a0d3a937f7bc393eaef328bded2ecdf.nq.gz
│   ├── 1528bda574c4e50f10e99a46551a4a4d9378a6b2.nq.gz
│   ├── 1ea55e67f617ead45618a74f1afe34442f1a075a.nq.gz
│   ├── 1f8c048f82ec49200e5b711d7f0772f431a63d85.nq.gz
│   ├── 2102cd8cbbf75b0e04f567646a767d1f218eae8b.nq.gz
│   ├── 22ec9b8a1940192cc57c0054efa741316cfb56f3.nq.gz
│   ├── 2bf2e2c7be1a0ed4fc2a94dba51ef720ee259dab.nq.gz
│   ├── 2fe3b5e6f00c04e81d83a8847581fac5a8810edc.nq.gz
│   ├── 3361a9bf0bd41c2871b3d79a8b14652b198535f7.nq.gz
│   ├── 369cf122252911723ec35f790231dd4674dba26b.nq.gz
│   ├── 41360454a68f4243b58621cedf7d5022d65aa013.nq.gz
│   ├── 45d22c6a99ad6aa0fe0790cafda7b6cd01f1cd70.nq.gz
│   ├── 46a2673a9adc77a5954faff712eceb465e0e5aa6.nq.gz
│   ├── 50eee1025b753bf2fc415f7d6a8d3e556a010ac4.nq.gz
│   ├── 5327a345483dc73555358704d7b2277c5d3df6f1.nq.gz
│   ├── 57270efcb007eab6b197fcdea26864d7781af759.nq.gz
│   ├── 5f790b43c21ed606451578c906a0b86d4fef8111.nq.gz
│   ├── 66aba18cab4ec4c67e7adbd4f722953231c1d33e.nq.gz
│   ├── 6851eb2a2c43113283a8b6f68d19a14c38f51a33.nq.gz
│   ├── 6be56245ed4c50c83c6dadca08208b3625a4b400.nq.gz
│   ├── 89a0106941ff398844f23a965c5b755ca12eef97.nq.gz
│   ├── 908f97ecf267c790c939c483e5f998c41803eec8.nq.gz
│   ├── 9a7c5cd17148e8ba9e729c4824dfe6320798c07a.nq.gz
│   ├── b2946d9663ae67387060669bd71cf46857c42c21.nq.gz
│   ├── b4d25fcac8d1fec19cff5f5eca9fe42db2aec0a9.nq.gz
│   ├── b5fcd9851ddfe60dab3622d4d73ca8963c2f6749.nq.gz
│   ├── befa50a301471dbfdd8b89236d9e86f085014c37.nq.gz
│   ├── c2a6ad8e99c17561789c9b6c58ac9a2e41ef2e3a.nq.gz
│   ├── c50163a4cd2dfc86309129896da9cd2a7676fed0.nq.gz
│   ├── c5ea591058cfd0abd277f29a568d7bb4acc5c605.nq.gz
│   ├── c617168690ec8b89319392baf0441f8298662329.nq.gz
│   ├── c7a76417abba34433859f9298f8143c7a23dd22a.nq.gz
│   ├── e5bd7eb2340cfedad7ac387869ce20bdb053f112.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 2cbbee3154d9011cee873ae3a020cd17c669f6df.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 43 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[rbarrois/python-semanticversion](https://github.com/rbarrois/python-semanticversion)

---
*Parsed on 2026-11-02 by [repolex](https://repolex.ai)*
