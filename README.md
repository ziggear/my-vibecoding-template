# My VibeCoding Template

- A template to make your vibe coding workflow 10× faster than before
- Less token consumption, less repeated error correction and fixing
- a practical template for maintaining code quality and workflow stability in long-running **vibe coding** setups

## 1 Usage

1. git clone this repository

`git clone https://github.com/ziggear/my-vibecoding-template.git`

2. Remove `README.md` of this repo to trash, to prevent AI from reading this unnecessary `README.md` file.

## 2 Problems in Vibe Coding

In real world projects, vibe coding degrades not because models are weak, but because **context and control break down** over time. The most common issues are:

1. **Context inflation**  
   As a conversation grows, effective context shrinks. The model starts reallocating tokens to restating history instead of producing new work. The observable symptom is a steady decline in coding accuracy and relevance.

2. **Tool / model switching cost**  
   Switching between tools (e.g. Cursor → Claude Code, IDE → CLI) often resets the model’s working assumptions. The model must re-infer goals, constraints, and progress, which causes a temporary but severe productivity drop.

3. **Multi-author inconsistency**  
   In collaborative settings, different developers use different IDEs, prompts, and interaction styles. The same task yields different outputs, creating divergence in code style, structure, and decision logic.

These problems compound over time and manifest as “AI quality degradation,” though the root cause is usually **loss of shared ground truth**, not model capability.

## 3 Core Idea

The solution is to **externalize project state and behavioral constraints into persistent markdown files**, and make them first-class inputs to the AI.

Modern tools already support this:
- Cursor → `Agents.md`
- Claude Code → `Claude.md`

These files are continuously loaded and act as a *long-term control plane* for vibe coding, independent of chat history.

Instead of relying on conversational memory, this template enforces **documented intent, progress, and rules**.

## 4 File Structure and Roles

| File | Role | Purpose |
|-----|-----|-----|
| `plan.md` | Project intent | Defines what is being built, why it exists, and the high-level definition of “done”. Serves as the stable source of project direction. |
| `guideline.md` | Constraints & standards | Records technical, architectural, and design rules, including coding style, abstractions, and non-negotiable principles. |
| `milestone.md` | Progress tracking | Lists major development milestones and high-level to-dos, allowing the AI to infer current progress and remaining work. |
| `Agents.md` / `Claude.md` | Control plane | Acts as the entry point for the AI. Defines behavioral rules, references other documents, and specifies what the AI should and should not do. |

All other files are effectively inputs to this one.

## 4 Behavioral Constraints (Key Principle)

A critical rule enforced in this template is **output restraint**.

The AI is explicitly instructed to:
- Not restate code it has already written
- Not re-explain logic the user already understands
- Not summarize documents that already exist
- Not perform unsolicited technology comparisons or theoretical digressions

Repeated explanation is treated as **wasted context**.  
Reducing this waste directly improves long-session output quality.

The model’s role is execution, not narration.

## 5 Fast Context Rehydration

Because all project state is documented:

- Opening a **new chat**
- Switching **IDE / CLI**
- Switching **AI tools**
- Onboarding a **new collaborator**

all become low-cost operations.

The AI can immediately infer:
- Current goals
- Project status
- Past decisions
- Existing constraints
- Previously rejected approaches

This minimizes correction cycles and keeps token usage focused on productive output.

## 6 Extensibility

The template is designed to layer cleanly with tool-specific features:

- Claude → `Claude Skills`
- Cursor → `Cursor Rules`

Additional constraints or domain-specific rules can be added there without polluting core project documents.

The process is iterative:
1. Observe unwanted AI behavior
2. Encode the constraint explicitly
3. Move the rule into persistent documentation
4. Let the model converge toward the desired output pattern
