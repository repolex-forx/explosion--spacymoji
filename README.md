# Repolex Knowledge Graph of explosion/spacymoji

RDF knowledge graph data for [explosion/spacymoji](https://github.com/explosion/spacymoji), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/spacymoji
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 408d047e7a0d48ab08d8230072935e8c2a98718f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 408d047e7a0d48ab08d8230072935e8c2a98718f
│           └── chunk-001.nq.gz
├── blob
│   ├── 0bd24012ae5ec965cf7b7d3e2ecb5eff696f8879.nq.gz
│   ├── 3e08ebfeffa35859f8477478630518172faa5560.nq.gz
│   ├── 6b10277c527c18228a17ef0a1f32e23bb14b46a9.nq.gz
│   ├── 72428aa5c025cef03dd3b51f3b0c3b5bda755f49.nq.gz
│   ├── 837de84c0ae704fe59a7af41676a02cf9f86f076.nq.gz
│   ├── a0f8b4003bd652a9404495e5ed7e056debc1a07e.nq.gz
│   ├── a5079c3bdd4f458b7e01e5ef57271d2e69ec02ae.nq.gz
│   ├── ae2dced154c3d29e64d8a00b9172fb723df27910.nq.gz
│   ├── c1a7121c1bd6c9648bc686c95b1c7a94dd69cdd3.nq.gz
│   ├── e56af0340d8bc96487f01c19b5a186f03c123b30.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f4590f1164aa9428225a3ecec2fa02cb5aaaa35a.nq.gz
│   └── fed528d4a7a148fd0bf0b0198a6461f8c91b87e9.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 408d047e7a0d48ab08d8230072935e8c2a98718f.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 21 files
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

[explosion/spacymoji](https://github.com/explosion/spacymoji)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
