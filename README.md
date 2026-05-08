# Repolex Knowledge Graph of Byron/open-rs

RDF knowledge graph data for [Byron/open-rs](https://github.com/Byron/open-rs), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download Byron/open-rs
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 7bd519c778eda8efe84137e61c35eaff95102d41
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 7bd519c778eda8efe84137e61c35eaff95102d41.nq.gz
│   └── repolex
│       └── 7bd519c778eda8efe84137e61c35eaff95102d41
│           └── chunk-001.nq.gz
├── blob
│   ├── 05582228484a3912617b10672289c173920e4d3c.nq.gz
│   ├── 0e1fdb79d8e8908188d5f45acf795ec654fc3e27.nq.gz
│   ├── 17daa1e3b39831093699020febfe1411247fa519.nq.gz
│   ├── 187eb457d635d0dd90e898a17da438554691b5a1.nq.gz
│   ├── 1a3e0176fd4c6816de88fc0939cad6d677cdb757.nq.gz
│   ├── 245f2dba0181db7bd170653d62a60a8a228a26fb.nq.gz
│   ├── 2fbcd138d3e2bd3df733ac61eba7ab0e59f62fc1.nq.gz
│   ├── 6033d64c394005060cba798e63dde7d3119347ce.nq.gz
│   ├── 685c783502b0b0b490fbb83781275932682927ef.nq.gz
│   ├── 9c58159ab84600d978a0902280d77a3e720ab3a2.nq.gz
│   ├── a48a43b0691e5ddaa61d959a5353a4873d8f6f7d.nq.gz
│   ├── a9d37c560c6ab8d4afbf47eda643e8c42e857716.nq.gz
│   ├── d1accaff0cdaa5321177d090dd1f212e6f4789cf.nq.gz
│   ├── d8d08cef16c1c8f54562dc585d8fa52b8143c939.nq.gz
│   ├── d9c7cb1845946ae521752dfece2800c88e3703b2.nq.gz
│   └── e1d78f1dc46a97b696a3e5ed1a665a45be7a54bf.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 7bd519c778eda8efe84137e61c35eaff95102d41.nq.gz
├── filetree
│   └── 7bd519c778eda8efe84137e61c35eaff95102d41.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 26 files
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

## Source repository

[Byron/open-rs](https://github.com/Byron/open-rs)

---
*Parsed on 2026-05-08 by [repolex](https://repolex.ai)*
