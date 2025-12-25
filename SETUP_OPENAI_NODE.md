# OpenAI Node.js Setup Instructions

This document explains how to correctly set up a Node.js project using the OpenAI API and fix the common
`ERR_MODULE_NOT_FOUND: Cannot find package 'openai'` error.

---

## 1. Prerequisites


- Node.js **v18 or higher** (Node 22+ works)
- npm (comes with Node)
- An OpenAI API key

Verify Node:
```bash
node -v

```

## Project Folder Structure

Your project folder should look like this after setup:

LLM_chatbot/
├─ chatbot.js
├─ explanation.md
├─ package.json
├─ package-lock.json
└─ node_modules/



## Initialize a Node.js Project

From inside your project folder:

npm init -y


This creates a package.json file, which Node uses to manage dependencies.

## Install OpenAI SDK
npm install openai


This creates:

node_modules/

package-lock.json

Without this step, Node cannot import openai


## Enable ES Modules (IMPORTANT)

The OpenAI SDK uses ES Modules.

Open package.json and add:

{
  "type": "module"
}


Example final package.json:

{
  "name": "llm-chatbot",
  "version": "1.0.0",
  "type": "module",
  "dependencies": {
    "openai": "^4.0.0"
  }
}

## Set the OpenAI API Key
Windows (PowerShell):
setx OPENAI_API_KEY "sk-your-api-key-here"


Close and reopen the terminal after running this command.

Verify:

echo %OPENAI_API_KEY%


## Common Errors & Fixes
❌ Error: Cannot find package 'openai'

Cause:

npm install openai not run

No package.json

Wrong directory

Fix:

npm init -y
npm install openai

❌ Error: Cannot use import statement outside a module

Cause:
ES modules not enabled.

Fix:
Add "type": "module" to package.json.

❌ API key undefined

Cause:
Environment variable not set or terminal not restarted.

Fix:
Re-run setx and restart terminal.

10. Important Notes

Never expose your OpenAI API key in frontend code (React, HTML, etc.)

Always call OpenAI from a backend (Node/Express)

.env variables in frontend builds are NOT secure

11. Next Steps (Optional)

Convert this into an Express backend

Add chat history (real chatbot)

Add streaming responses

Add rate limiting & auth

Connect to a React frontend safely