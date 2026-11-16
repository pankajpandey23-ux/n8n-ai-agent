# Office Assistant Agent (n8n)

A simple **AI agent built in n8n** that acts as a friendly office assistant: it chats in plain
language, looks things up with Wikipedia, and does calculations — and it's instructed to be
honest about its limits rather than guess.

I built this to learn hands‑on how AI agents actually work: how an LLM decides *when* to call a
tool, what a system prompt does, and where the limits are.

## What it does

- A chat interface (n8n **Chat Trigger**)
- An **AI Agent** that decides, for each message, whether to answer directly or use a tool
- **Tools:** Wikipedia (fact lookup) and Calculator (exact math)
- **Short‑term memory** so it follows the conversation
- A **system prompt** that keeps answers simple and jargon‑free, and tells the agent to say so
  honestly when it's unsure or a tool fails

**Example:** *"What's the population of Göttingen, and what is that divided by 4?"* → the agent
looks the population up on Wikipedia, uses the Calculator for the math, then answers in plain
language.

## How it's built (nodes)

- **When chat message received** (Chat Trigger)
- **AI Agent**
  - **Chat Model:** Google Gemini (Gemini 3.8 Flash)
  - **Memory:** Simple Memory (window buffer)
  - **Tools:** Wikipedia, Calculator
- **System message:** office‑assistant persona — plain language, no jargon, honest about limits

## Run it yourself

1. Import `workflow.json` into your own n8n instance (**Workflows → Import from File**).
2. Add your own **Google Gemini** API credential (free key from aistudio.google.com).
3. Open the **Chat** panel and ask it something.

## What I learned

- How an **agent** differs from a single LLM call — it *chooses* when to use a tool.
- How the **system prompt** shapes behaviour and sets guardrails.
- Where LLMs **need tools** (facts, exact math) and where they shouldn't be trusted to guess.

> Note: API keys/credentials live in n8n, not in this file — nothing secret is committed.
