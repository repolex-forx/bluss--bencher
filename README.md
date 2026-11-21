# Repolex Knowledge Graph of bluss/bencher

RDF knowledge graph data for [bluss/bencher](https://github.com/bluss/bencher), parsed by [repolex](https://repolex.ai).

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
rlex download bluss/bencher
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 8afeeb1ccf7d9f58764a343a0099e140703ad287
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 8afeeb1ccf7d9f58764a343a0099e140703ad287.nq.gz
│   └── repolex
│       └── 8afeeb1ccf7d9f58764a343a0099e140703ad287
│           └── chunk-001.nq.gz
├── blob
│   ├── 042776aad729534e038599f1a5b8f4e8c78dae0e.nq.gz
│   ├── 16fe87b06e802f094b3fbb0894b137bca2b16ef1.nq.gz
│   ├── 1817b959f32f2fd18ad5c6c276929902fefee9da.nq.gz
│   ├── 3f4ea6bea4d87c448f285cb32bb6d5d4fbd8c224.nq.gz
│   ├── 4ded546a78a91519dbe9e49b13fd8d4d8d2fa275.nq.gz
│   ├── 7685029bf630ab9d40f49db238b30257bb282cfa.nq.gz
│   ├── 9203baa055d41d89e1ab8f4d6aa9180a49e078a7.nq.gz
│   ├── ba57dc1778f81a5463e57d9d454520005a23999f.nq.gz
│   ├── c09ae532b871efc38f6bfcd8125cd295c4c433f7.nq.gz
│   └── d07633ef96120ec6f983b4b8ed370e8fcc4787b6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 8afeeb1ccf7d9f58764a343a0099e140703ad287.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

14 directories, 19 files
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

[bluss/bencher](https://github.com/bluss/bencher)

---
*Parsed on 2026-11-21 by [repolex](https://repolex.ai)*
