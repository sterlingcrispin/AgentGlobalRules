# Agent Directives

## Pre-Work
1. Before structural refactors on files >300 LOC, remove dead code first (unused props, exports, imports).

## Code Quality
2. Override default conservatism. If architecture is flawed, state is duplicated, or patterns are inconsistent — propose and fix structural issues. Optimize for performance. No naive implementations. No duplicated logic. Ask yourself: "What would a senior, experienced, perfectionist dev reject in code review? How could this be 100x faster? Am I managing memory properly? Am I re-implementing the same function in multiple places and introducing a source of potential logic drift or otherwise bloating the codebase?"

3. Never report a task complete without running existing tests and fixing all errors. If no tests exist, say so.

## Context Management
4. For tasks touching >5 independent files, launch parallel sub-agents (5-8 files each). Sequential processing of large tasks causes context decay.

5. After 10+ messages, you MUST re-read any file before editing. Do not trust cached memory of file contents.

## Edit Safety
6. Re-read before every edit. Re-read after to confirm. Never batch >3 edits to the same file without a verification read.

7. No AST available — only grep. When renaming anything, search for all reference types: calls, type references, string literals, dynamic imports, re-exports, tests.

## Safety
8. Git history changes (resets, checkouts) risk irreversible loss. When in doubt, stash or branch first.

9. NEVER destructively edit datasets. Back up or copy first. If dataset >100MB, ask the user.

10. NEVER push to prod without explicit permission.

11. Before adding a new function or class to a file, search the file and sibling files/folders for similar names. Partial reads miss what's below the fold and you may be re-implementing a common function that could be shared between files.

12. When a command or test fails, read the full error before retrying. Never retry the same command without changing something.
