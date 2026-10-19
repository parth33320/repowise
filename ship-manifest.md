# Ship-Manifest: Branch fix/issue-4092

This manifest defines the required pre-flight checks and validation gates for merging changes into `repowise`.

## Gate Checks & Validation Rules

- [x] **Test Suite Execution**
  - **Command:** `PYTHONPATH=. pytest tests/unit/server/mcp/test_finding_registry_visibility.py -p gcplug`
  - **Purpose:** Verifies that session lifecycle handling is correct under garbage collection and that all 8 MCP visibility tests pass without connection leaks or `PendingRollbackError`.

- [ ] **Full Test Suite Regression Check**
  - **Command:** `pytest`
  - **Purpose:** Ensures no regressions were introduced across other server or core unit tests.

- [ ] **Code Linter (Ruff)**
  - **Command:** `ruff check .`
  - **Purpose:** Enforces code style, import sorting, and lint standards across modified Python files.

- [ ] **Web Frontend / Server Build Check**
  - **Command:** `npm run build` *(if frontend assets are touched)*
  - **Purpose:** Verifies TypeScript and web bundle compilation succeeds without errors.

## Manifest Notes
- **Active Issue:** [#4092](https://github.com/repowise-dev/repowise/issues/new/choose3) (`get_dead_code` session leak fix)
- **Active Pull Request:** [#4181](https://github.com/repowise-dev/repowise/pull/4181/changes)