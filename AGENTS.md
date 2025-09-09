# Repository Guidelines

## Project Structure & Module Organization
- Prefer a clear layout from the start. Suggested baseline:
  - `src/`: source modules and entry points
  - `tests/`: unit/integration tests
  - `scripts/`: one-off or maintenance scripts
  - `data/` (ignored): local datasets or outputs
  - `docs/`: design notes and user/developer docs
- Example:
```
src/            tests/           scripts/        docs/
```

## Build, Test, and Development Commands
- If a `Makefile` exists, use it as the source of truth:
  - `make setup`: install dependencies
  - `make lint`: run static checks/formatters
  - `make test`: run the test suite
  - `make run`: start the app or main script
- Without Makefile, use native tooling (examples):
  - Python: `pip install -r requirements.txt`, `pytest -q`
  - Node.js: `npm ci`, `npm test`, `npm start`

## Coding Style & Naming Conventions
- Indentation: 4 spaces for Python; 2 spaces for JS/TS.
- Filenames: Python `snake_case.py`; JS/TS `kebab-case.ts(x)`.
- Line length target: 100 chars.
- Formatters/linters (use if configured): Python `black` + `ruff`; JS/TS `prettier` + `eslint`.
- Prefer small, single‑purpose modules; keep public APIs minimal.

## Testing Guidelines
- Put tests in `tests/` mirroring `src/` structure.
- Naming:
  - Python: `tests/test_*.py`
  - JS/TS: `__tests__/*.test.ts`
- Aim for ≥80% coverage on changed code. Add tests with new features/bug fixes.
- Quick run: `make test` (or `pytest -q` / `npm test`).

## Commit & Pull Request Guidelines
- Use Conventional Commits: `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `chore:`.
- Keep commits focused; include rationale in the body if non‑obvious.
- PRs: clear description, linked issues, screenshots for UI changes, tests and docs updated.
- CI must pass before merge.

## Security & Configuration Tips
- Never commit secrets; use `.env` and provide `.env.example`.
- Ignore large data/outputs (`data/`, `*.csv`, `*.ipynb_checkpoints/`) via `.gitignore`.
- Pin dependencies and review updates regularly.
