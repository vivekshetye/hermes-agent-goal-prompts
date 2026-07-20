# Hermes Agent `/goal` Prompt

This repository accompanies my YouTube walkthrough of the Hermes Agent `/goal` feature. It contains the prompt I used to turn seven Google Stitch screens for a budget planner into a working Next.js application.

▶️ **[Watch the video on YouTube](https://youtu.be/-FnFrb2-Yk0)**  
📖 **[Read the official Hermes Agent `/goal` documentation](https://hermes-agent.nousresearch.com/docs/user-guide/features/goals)**

## What `/goal` does

`/goal` turns a prompt into a standing objective. At the end of each turn, a judge model checks whether the objective has been achieved. If meaningful work remains, Hermes continues automatically in the same session—without waiting for another “keep going” prompt.

The loop stops when the goal is achieved, you pause or clear it, Hermes needs your input, or the configured turn budget is exhausted. The default budget is 20 continuation turns.

## Prompt used in the video

The complete prompt is in [`task_prompt.md`](./task_prompt.md).

To use it:

1. Download or clone this repository.
2. Open a terminal in the project where you want Hermes to work.
3. Start Hermes:

   ```bash
   hermes
   ```

4. Start the prompt with `/goal draft`:

   ```text
   /goal draft Build a production-ready Next.js 15 + React + TypeScript + Tailwind CSS application...
   ```

5. Paste the rest of the text from [`task_prompt.md`](./task_prompt.md) on the same line and submit it.

Before running the prompt, replace the Google Stitch designs path with the absolute path to your own exported designs. The path in `task_prompt.md` points to the local folder used in the video and will not exist on your machine.

## Why use `draft`?

`/goal draft` asks Hermes to expand a plain-language objective into a completion contract before beginning the work. The contract makes “done” more concrete by defining:

- **Outcome** — the final state that must be achieved
- **Verification** — the evidence that proves completion
- **Constraints** — what must not change or regress
- **Boundaries** — what is in scope
- **Stop condition** — when Hermes should stop and ask for help

You can review the generated contract with:

```text
/goal show
```

## Useful commands

```text
/goal status   # Show the current goal and turn usage
/goal pause    # Pause automatic continuation
/goal resume   # Resume and reset the continuation counter
/goal clear    # Remove the active goal
```

## Good use cases

Persistent goals work best for tasks that normally require several rounds of review and follow-up, such as:

- Implementing a feature and verifying it end to end
- Fixing bugs or lint errors across a codebase
- Writing tests and getting the full test suite passing
- Debugging an intermittent issue
- Completing a framework or database migration

A specific outcome and concrete verification criteria produce better results than a vague request. Hermes and its judge can still make mistakes, so review the final output before treating it as production-ready.

## Resources

- [YouTube walkthrough: Hermes Agent `/goal` feature](https://youtu.be/-FnFrb2-Yk0)
- [Hermes Agent persistent goals documentation](https://hermes-agent.nousresearch.com/docs/user-guide/features/goals)
- [Hermes Agent GitHub repository](https://github.com/NousResearch/hermes-agent)
