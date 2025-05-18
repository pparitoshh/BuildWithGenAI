# LinkedIn Job Alert → Telegram Notification (n8n Workflow)

This n8n workflow watches your Gmail for LinkedIn job alert emails, extracts relevant job listings using OpenAI's GPT-4o, and sends the matching jobs to your Telegram chat.

## 📦 Workflow Overview

1. **Gmail Trigger** — Watches for new emails with subject `Job alert`
2. **Get Full Email** — Fetches full email content using message ID
3. **Decode HTML** — Decodes base64 HTML to readable text
4. **LLM Extract Jobs** — Sends the email content to GPT-4o to extract structured job info
5. **Send to Telegram** — Sends the matching jobs to your Telegram via the Bot API

## 🛠️ Requirements

- n8n self-hosted or cloud setup
- Gmail credentials connected in n8n
- OpenAI credentials with access to GPT-4o
- Telegram bot token and chat ID

## 🔧 Setup

1. Replace `{{BOT_TOKEN}}` with your actual Telegram bot token in the `Send to Telegram` node.
2. Replace `{{CHAT_ID}}` with your personal or group chat ID.
3. Replace OpenAI credential placeholder (`openai-credentials-id`) with your actual credentials ID.
4. Activate the workflow.

## 🧠 Prompt Functionality

The LLM parses all jobs in the email and returns:

- Job title
- Company name
- Location
- Posting date (if available)
- Number of applicants (if available)
- Link
- Whether the job is actively recruiting

## 📬 Example Output on Telegram

```
1. **Senior Data Scientist** – Company ABC – Berlin  
🔗 Link: https://www.linkedin.com/jobs/view/123456789  
🗓️ Posted: 3 days ago  
👥 Applicants: 42  
✅ Actively Recruiting: Yes
```

---
MIT License