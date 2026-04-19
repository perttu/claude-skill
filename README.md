# claude-skill

A drop-in `CLAUDE.md` that gives Claude Code (and other Claude-based coding assistants) a stricter operating contract — to reduce the common failure modes of LLM coding: silent reinterpretation, over-engineering, scope creep, premature convergence, and "looks correct" partial solutions.

## What this is

A single `CLAUDE.md` file with 5 top-level rules and 11 sub-rules under *Execution Guarantees & Review Awareness*.

Drop it at the root of a repository (or in `~/.claude/CLAUDE.md` for global use) and Claude will read it at the start of every session.

## Why

Based on [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills/blob/main/CLAUDE.md), extended to cover the *Generation-Aware Checklist* failure modes:

| Failure mode | Addressed by |
|---|---|
| Specification drift / intent compression | §5.1 Intent Fidelity |
| Hidden assumptions / silent defaults | §5.2 Assumptions Must Be Explicit |
| Premature convergence on one solution | §5.3 No Single-Path Solutions |
| "80% trap" — plausible but incomplete | §5.4 Completeness Over Plausibility |
| Local fixes that break the system | §5.5 System Awareness |
| Sycophantic agreement | §5.6 Anti-Sycophancy |
| Vague, untestable claims | §5.7 Concreteness Requirement |
| Unresolved references / magic steps | §5.8 Traceability |
| Unreviewed output | §5.9 Self-Review Before Output |
| Partial work presented as done | §5.10 Definition of Done |
| Unstated uncertainty | §5.11 Confidence & Uncertainty |

Plus baseline rules for simplicity (§2), surgical diffs (§3), and goal-driven loops (§4) — to keep the assistant from over-building and over-editing even when the per-task output is technically "valid."

## Usage

**Per project:**

```bash
cp CLAUDE.md /path/to/your/project/CLAUDE.md
```

**Globally (all projects):**

```bash
cp CLAUDE.md ~/.claude/CLAUDE.md
```

**Merging with existing instructions:** The rules here are generic. If you already have a project-specific `CLAUDE.md`, append these rules rather than replacing — they're designed to stack.

## What to expect

You should see:

- Fewer unnecessary edits in diffs.
- Fewer rewrites caused by overcomplication.
- Clarifying questions *before* implementation instead of after a wrong one.
- Explicit assumption lists and tradeoff comparisons in planning steps.

You should *not* expect this to speed up trivial tasks — the guidelines bias toward caution. The rules explicitly permit judgment on trivial work.

## Caveats

- These are behavioral nudges, not guarantees. A model can still ignore or under-apply any rule.
- Strictness has a cost: expect more upfront questions and more verbose plans on non-trivial tasks.
- Tuned for coding work. It may feel heavy-handed on chat-style or exploratory prompts.

## Credit

- Core structure adapted from [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills).
- §5 extensions address the *Generation-Aware Checklist* — a 12-point prompt contract for planner/implementor-style LLM pipelines.

## License

MIT.
