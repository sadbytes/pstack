# Comment review rubric

Inspect only the supplied files or diff. If no scope is supplied, inspect the current diff against `main`.

Delete narration, banners, commented-out code, and workaround explanations unless an exception applies. Keep only these exceptions.

- Legal or license headers.
- Non-obvious behavior forced by an external dependency, platform, vendor, or protocol the caller cannot change.
- `// prettier-ignore`. Keep lint suppressions only when the rule is faulty, pedantic, or style-only.
- Doc comments that define a public API contract.
- Issue or RFC links that explain a constraint code cannot express.

Read the relevant rule before judging `eslint-disable`, `@ts-ignore`, `@ts-expect-error`, or another suppression. If the rule protects correctness or safety, flag the suppression and its exact symbol as `MUST KILL`.

Read nearby code before judging `IMPORTANT`, `do not remove`, or another constraint claim. Use the **how** or **why** skill when the claim is not established by that code. Keep an external constraint only when it is proven on a live path. If no exception applies, delete the comment. Flag surprising behavior in the caller's own code as `MUST KILL` for a rename, extraction, type, or redesign that makes the behavior clear.

A long justification without a proven exception must be deleted. Mark its exact symbol `MUST KILL`. Do not rewrite an unsupported explanation into a shorter justification.

Every finding names a symbol inside the scope and cites evidence. Never change application code. Report touched files, comment deletion candidates or count, `MUST KILL` findings, exceptions, and skips. If the host requires a read-only reviewer, report proposed deletions instead of editing files. The caller applies accepted changes.
