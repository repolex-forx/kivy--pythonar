# Repolex Knowledge Graph of kivy/pythonar

RDF knowledge graph data for [kivy/pythonar](https://github.com/kivy/pythonar), parsed by [repolex](https://repolex.ai).

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
rlex download kivy/pythonar
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 77bc28363fa36fbf0b84ea187a90625750565752
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 77bc28363fa36fbf0b84ea187a90625750565752
│           └── chunk-001.nq.gz
├── blob
│   ├── 190c0239cd7d7af82a6e0cbc8d68053fa2e3dfaf.nq.gz
│   ├── 253bc5816185fe8bcb751f23851731a62340193a.nq.gz
│   ├── 36198389f2f2d36d1c46a4390c88b9b3265ead67.nq.gz
│   ├── 7f9b114b43269a385f83ed1a582a9134740a9d68.nq.gz
│   └── 986e7f07a5bc015c6949c6282960eafe2183b01a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 77bc28363fa36fbf0b84ea187a90625750565752.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 13 files
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

[kivy/pythonar](https://github.com/kivy/pythonar)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
