# SLE-4: Final Viva and Architecture Decision Record

## Course Information

| Field | Details |
|---|---|
| Course | 02AML204 – Introduction to Artificial Intelligence |
| Activity | SLE-4 |
| Project | Graph Search System using BFS and DFS |
| ADR Title | Use of a Visited Set in BFS and DFS Graph Search |
| ADR Status | Accepted |
| Programming Language | Python |
| Architecture Model | C4 Model |
| AI Tool Used | ChatGPT |
| Author | Shreyash Potdar |

## Project Overview

SLE-4 is the final activity of the Graph Search System using BFS and DFS project. It focuses on documenting and justifying an important architecture decision through an Architecture Decision Record (ADR) and preparing for the final viva.

The selected decision is the use of a visited set in BFS and DFS to prevent repeated node exploration and handle cyclic graphs.

This activity connects the implementation from SLE-1, empirical performance analysis from SLE-2, and C4 architecture diagrams from SLE-3.

## Objectives

- To understand the purpose of an Architecture Decision Record.
- To document and justify an important design decision.
- To analyze alternatives and consequences.
- To connect the decision with the BFS and DFS implementation.
- To relate SLE-2 performance results to SLE-3 architecture.
- To prepare for the final viva examination.

## Architecture Decision Record (ADR)

### ADR Title

Use of a Visited Set in BFS and DFS Graph Search

### Status

Accepted

### 1. Context

The Graph Search System performs Breadth-First Search (BFS) using a queue and Depth-First Search (DFS) using a stack.

Graphs may contain cycles or multiple paths to the same node. Without tracking visited nodes, repeated exploration can occur and may cause unnecessary processing or nontermination.

### 2. Decision

A visited set is used in both BFS and DFS to track explored nodes.

When a node is removed from the queue or stack, the algorithm checks whether it has already been visited. If it has, the node is skipped. Otherwise, it is marked as visited and processed.

This prevents repeated node expansion, although duplicate entries may temporarily exist in the frontier.

### 3. Alternatives Considered

| Alternative | Reason Not Selected |
|---|---|
| No visited set | May cause repeated exploration and nontermination on cyclic graphs |
| Mark nodes visited when inserted into the frontier | Valid alternative that reduces duplicate entries, but differs from the existing implementation |
| Path-based cycle checking only | Does not prevent repeated exploration across different branches |

### 4. Rationale and Justification

The visited set improves the reliability of graph traversal by preventing repeated expansion and helping BFS and DFS handle cyclic graphs.

It also supports meaningful node-expansion measurements during performance comparison.

The decision connects with the **Visited / Memory** container and **Explored / Closed Set** component in the SLE-3 architecture.

### 5. Consequences

**Positive:**
- Prevents repeated node expansion.
- Helps handle cycles in directed graphs.
- Improves the reliability of node-expansion counts.
- Supports the modular architecture.

**Negative:**
- Requires additional memory for storing visited nodes.
- Duplicate frontier entries may still occur before nodes are processed.

## SLE-2 Performance Results

Both algorithms were tested on the same directed graph with start node `A` and goal node `Z`.

| Metric | BFS | DFS |
|---|---:|---:|
| Run 1 (ms) | 1099.568 | 1098.097 |
| Run 2 (ms) | 1062.292 | 1216.371 |
| Run 3 (ms) | 1048.642 | 1179.768 |
| Average Total Time (ms) | 1070.167 | 1164.746 |
| Average Time/Search (ms) | 0.010702 | 0.011647 |
| Nodes Expanded | 25 | 20 |
| Path Length | 8 | 8 |
| Searches Per Run | 100000 | 100000 |

### Path Found

Both algorithms found:

`A → C → F → J → N → R → V → X → Z`

### Performance Analysis

DFS expanded fewer nodes, while BFS recorded a lower average execution time in the selected experiment.

These measurements describe the performance of the existing implementations with visited sets. They do not measure the performance difference between using and not using a visited set.

## Connection with Previous SLE Activities

| Activity | Work Completed |
|---|---|
| SLE-1 | BFS and DFS implementation |
| SLE-2 | Empirical performance analysis and profiling |
| SLE-3 | C4 Context, Container, Component, and Code diagrams |
| SLE-4 | Architecture Decision Record and final viva preparation |

## Tools Used

- Python – BFS and DFS implementation
- Visual Studio Code – Development environment
- py-spy – Performance profiling
- diagrams.net (draw.io) – C4 architecture diagrams
- Microsoft Word – ADR report preparation
- GitHub – Documentation and version control
- ChatGPT – AI assistance

## Project Files

| File | Description |
|---|---|
| `SLE4_PRN_Shreyash_Potdar.docx` | Final SLE-4 ADR and viva report |
| `C4_Level3_Component.png` | Supporting Search Engine component diagram |
| `README.md` | Project documentation |
| `AI_ContributionLog.md` | Student and AI contribution record |

## Conclusion

SLE-4 successfully documents the importance of using a visited set in the BFS and DFS Graph Search System.

The ADR explains the context, decision, alternatives, justification, and consequences. It also connects the implementation, performance analysis, and C4 architecture developed in the previous SLE activities.
