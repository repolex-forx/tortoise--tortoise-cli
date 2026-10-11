# Repolex Knowledge Graph of tortoise/tortoise-cli

RDF knowledge graph data for [tortoise/tortoise-cli](https://github.com/tortoise/tortoise-cli), parsed by [repolex](https://repolex.ai).

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
rlex download tortoise/tortoise-cli
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f46c2300480995402b1bce589175dfd5c94b8789
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── f46c2300480995402b1bce589175dfd5c94b8789
│           └── chunk-001.nq.gz
├── blob
│   ├── 022066d66c735a6c04ea33ccc7ebb39998d507ea.nq.gz
│   ├── 065c5be5b90f62c81500342e255b2c07d0151acb.nq.gz
│   ├── 1a512a9eae5d82f6ee85804d9cd938f258937835.nq.gz
│   ├── 1b2f1fc35671f96541e5d773d73d552edc987c49.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 36a15fa24ef1ea96cb538a21026080c7ac47a5f3.nq.gz
│   ├── 38a7f5840bc53bc8690115e35114d01f1650c661.nq.gz
│   ├── 5d18e4823b6561d47deb7a3cc7e455c155ea81cd.nq.gz
│   ├── 8bcb830b7fb26102eea459babf6ecd94e9298494.nq.gz
│   ├── 8c862b2bb2a687927491279fa9a903491505a65b.nq.gz
│   ├── a032dc62809a8ad767de93e637054dbbc01e2718.nq.gz
│   ├── a22a225779b6bfead01e9484c9c3535c83987543.nq.gz
│   ├── cb252812ffd9f176f10d8d2767d9006e9d870a6c.nq.gz
│   ├── d324e1a75eac8f1691e8e011ff3e42ba10a5a4ab.nq.gz
│   ├── d3ec452c319b475c6661b100f2dd22ca031ed911.nq.gz
│   ├── e17e6b76c78902d7f37bf56cc2ccc53e486241f5.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── f46c2300480995402b1bce589175dfd5c94b8789.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 25 files
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

[tortoise/tortoise-cli](https://github.com/tortoise/tortoise-cli)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
