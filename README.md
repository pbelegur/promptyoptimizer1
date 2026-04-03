# PromptyOptimizer

PromptyOptimizer is a Chrome extension that rewrites rough AI prompts into clear, structured prompts and lets users inject them directly into ChatGPT, Claude, or Gemini. It uses the Groq API with Llama 3 to generate optimized prompt variants, clarity feedback, token savings, and lightweight local analytics.

## Features

* Rewrite rough prompts into clearer, more structured versions
* Generate 3 prompt variants for different LLM styles

  * Claude / GPT-4
  * Gemini
  * Mistral
* One-click injection into ChatGPT, Claude, and Gemini
* Clarity score and token savings for every optimization
* Improvement suggestions for each rewritten prompt
* Local analytics dashboard for usage tracking
* Prompt history with quick reuse
* API key storage through Chrome local storage
* No backend required

## Supported Platforms

* ChatGPT
* Claude.ai
* Gemini

## Tech Stack

* Chrome Extension Manifest V3
* JavaScript
* HTML/CSS
* Groq API
* Llama 3.1 8B Instant

## Project Structure

promptyoptimizer/
├── manifest.json
├── background.js
├── content.js
├── popup.html
├── popup.js
├── options.html
├── options.js
├── styles.css
├── icon.svg
├── generate_icons.py
├── README.md
└── INSTALLATION_GUIDE.md

## How It Works

1. The user enters a rough prompt in the extension popup.
2. The popup sends the prompt to the background service worker.
3. The background script calls the Groq API and asks the model to:

   * rewrite the prompt
   * generate 3 optimized variants
   * estimate clarity
   * estimate token savings
   * list improvements made
4. The optimized result is shown in the popup.
5. The user can:

   * copy the result
   * inject it into ChatGPT, Claude, or Gemini
   * review history and analytics

## Installation

### 1. Clone or download the project

git clone <your-repo-url>

Or download the ZIP and extract it.

### 2. Open Chrome extensions

Go to:

chrome://extensions/

### 3. Enable Developer Mode

Turn on Developer mode in the top-right corner.

### 4. Load the extension

Click Load unpacked and select the project folder containing manifest.json.

## Setup

### Add your Groq API key

1. Click the extension icon
2. Open Settings
3. Paste your Groq API key
4. Save it

Your key should begin with:

gsk_

## Usage

1. Open the extension popup
2. Paste or type a rough prompt
3. Click Optimize
4. Review:

   * optimized prompt
   * clarity score
   * token savings
   * recommended model
   * improvement list
5. Choose to:

   * copy the prompt
   * inject it into ChatGPT, Claude, or Gemini

## Analytics

PromptyOptimizer stores lightweight analytics locally in the browser, including:

* total prompts optimized
* average clarity
* total tokens saved
* category breakdown
* last 20 prompt history entries

Categories are inferred from the original prompt, such as:

* Coding
* Writing
* Explaining
* Analysis
* Creating
* Other

## Permissions

The extension uses the following permissions:

* activeTab
* storage
* scripting
* tabs

Host permissions are used for:

* https://api.groq.com/*
* https://chat.openai.com/*
* https://chatgpt.com/*
* https://claude.ai/*
* https://gemini.google.com/*

## Privacy

PromptyOptimizer stores the following locally in Chrome storage:

* Groq API key
* last prompt
* analytics
* prompt history

Prompts are sent directly to the Groq API for optimization. No separate backend server is used in this project.

## Core Files

### manifest.json

Defines extension metadata, permissions, popup, background worker, content scripts, and supported sites.

### background.js

Handles:

* prompt optimization via Groq
* analytics tracking
* prompt injection into active tabs

### content.js

Finds the prompt input box on supported AI chat sites and injects the optimized text.

### popup.js

Controls the popup UI, including:

* optimization flow
* results rendering
* stats tab
* history tab
* copy and inject actions

### options.js

Handles Groq API key storage and settings UI.

## Example Flow

### Input

can u explain kafka in simple way like how it works internally brokers topics all that

### Output

Explain Apache Kafka's internal architecture in simple terms.

Cover the following concepts:

* Brokers and their role
* Topics and message organization
* Partitions for scalability
* Producers and Consumers
* Offsets for tracking position

Use a simple analogy if possible. Keep the explanation beginner-friendly with a short example.

## Troubleshooting

### Extension does not load

* Make sure manifest.json is in the selected folder
* Reload the extension from chrome://extensions/

### Optimize button does not work

* Check that your Groq API key is saved
* Make sure the key starts with gsk_

### Injection fails

* Open ChatGPT, Claude, or Gemini first
* Refresh the page and try again
* Make sure the chat input box is visible

### No response from model

* Verify your Groq API key
* Check internet connectivity
* Try the request again

## Future Improvements

* Better selector handling across chat UIs
* Export prompt history
* More detailed prompt analytics
* More model-specific prompt templates
* Support for additional LLM platforms

## Version

Current version: 3.0.0

## License

This project is licensed under the MIT License.
