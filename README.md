# Free_AI — Local multi-model AI chat

Lightweight local-first AI chat UI that connects to multiple providers via an OpenRouter-style service. Built with React + Vite, it preserves conversation history in the browser, supports switching models while keeping conversation context, and provides a simple abstraction for calling different model providers.

## Project description (short)

Free_AI is a developer-focused chat UI that lets you experiment with multiple LLM providers (OpenAI, Anthropic, Google, Meta, etc.) through a unified service. It stores conversation history locally, supports model switching with the same context, and is designed for rapid prototyping and extension.

## Features

- Multi-model support (select and switch models)
- Conversation history saved to `localStorage` (save / restore sessions)
- Compact, modular React components (`Chat`, `ProfileMenu`, `ContactButton`)
- Local-first: no backend required for basic usage
- Simple service abstraction (`openRouterService`) for API calls
- Easy to extend: add pruning, summarization, or server-side storage

## Quick start

Prerequisites:
- Node.js 16+ and npm

Install and run locally:

```bash
npm install
npm run dev
```

## Configuration

- The app expects an API key for the model provider. Enter it in the API key input in the sidebar header to enable the chat.
- Sessions and a mock user are stored in `localStorage` under `chat_sessions` and `mock_user` respectively.

## How conversation context & model switching works

- When you send a message, the app builds a request payload from the current `messages` state (mapping UI senders to `user`/`assistant` roles) and sends it to the selected model via `openRouterService.chatCompletion(...)`.
- Saved sessions include the message list so you can restore prior conversations. By default the UI keeps the currently-selected model when restoring a session — consider saving/restoring the `selectedModel` in snapshots if you want to preserve the original model.

## Recommended improvements

- Prune or summarize long histories before sending to avoid token limits.
- Persist sessions to a server or sync across devices if needed.
- Add role/system prompt support for consistent system instructions across models.

## Contributing

Contributions, issues and feature requests are welcome. Fork the repo, make your changes, and open a pull request.

## License

MIT — modify as needed for your project.

---

GitHub description (one-liner):

> Free_AI — A local-first, multi-model AI chat UI for experimenting with OpenRouter-compatible models and preserving conversation history.

LinkedIn blurb (1–2 sentences):

> Free_AI is a lightweight React + Vite chat interface that connects to multiple LLM providers through an OpenRouter-style service. It stores conversation history locally, supports switching models while keeping conversation context, and is ideal for rapid prototyping and testing different AI models.
