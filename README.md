# 🤖 Telegram AI Agent Bot (n8n Automation)

This project integrates **Telegram**, **OpenAI**, and **Google Workspace tools** using **n8n** to create a smart conversational assistant capable of understanding natural language, checking calendar availability, scheduling events, and logging structured data in Google Sheets.

---

## 🚀 Features

- **AI-Powered Conversations** using OpenAI Chat Model (GPT-4 or higher)
- **Contextual Memory** through LangChain’s Window Buffer Memory
- **Task Automation** using n8n workflow engine
- **Google Calendar Integration** for:
  - Checking availability
  - Creating events automatically
- **Google Sheets Integration** for structured data logging
- **Telegram Bot Interface** for real-time user interaction

---

## 🧠 System Architecture

```text
          ┌──────────────────┐
          │ Telegram Trigger │
          └────────┬─────────┘
                   ▼
             ┌──────────┐
             │ AI Agent │◄────────────────────────────────────┐
             └────┬─────┘                                     │
    ┌─────────────┼────────────────────────────────────┐      │
    ▼             ▼                                    ▼      │
OpenAI       Memory Buffer                 ┌────────────────┐ │
 Chat        (Window Buffer)              │    Tools Set    │ │
Model                                      └────┬────┬───────┘ │
                                              ▼    ▼         ▼
                                    Check Avail  Create   Append Data
                                     (GCal)      Event     (Sheet)

                   ▼
       ┌─────────────────────┐
       │Send Telegram Message│
       └─────────────────────┘
🧩 Components Used
Component	Technology
Bot Interface	Telegram Bot API
Automation Engine	n8n (Open Source Workflow Automation)
AI Model	OpenAI ChatGPT (GPT-4 / GPT-3.5)
Memory Handling	LangChain - Window Buffer Memory
Calendar Management	Google Calendar API
Data Logging	Google Sheets API

⚙️ Workflow Overview
1. Telegram Trigger
Listens for incoming messages from users and passes them into n8n.

2. AI Agent Node
Acts as the central decision-maker, using the Chat Model, Memory, and connected tools.

3. OpenAI Chat Model
Processes natural language prompts and generates intelligent responses.

4. Memory Node
Stores a buffer of recent messages to provide conversational context.

5. Google Calendar Nodes
Check Availability: Verifies open time slots.

Create Event: Books meetings or reminders automatically.

6. Google Sheets Node
Appends structured conversation data (name, date, event, etc.) for logging or analytics.

7. Send Telegram Message
Delivers the AI-generated response or action confirmation back to the user.

🧰 Setup Instructions
Prerequisites
n8n (self-hosted or cloud)

Telegram Bot Token (from BotFather)

OpenAI API Key

Google API Credentials (Calendar + Sheets)

Steps
Clone this repository:

bash
Copy code
git clone https://github.com/<your-username>/telegram-ai-agent-n8n.git
cd telegram-ai-agent-n8n
Import the provided n8n workflow JSON into your n8n instance.

Set up environment variables in n8n:

bash
Copy code
TELEGRAM_BOT_TOKEN=<your_telegram_token>
OPENAI_API_KEY=<your_openai_key>
GOOGLE_CREDENTIALS=<path_to_google_credentials.json>
Activate the workflow and start interacting via Telegram!

🧠 Example Conversation
User:

Can you schedule a meeting with the team tomorrow at 3 PM?

Bot:

Checking your Google Calendar...
✅ Slot available. Event created: Team Meeting – Tomorrow, 3 PM.

User:

Also note it in the sheet.

Bot:

Added meeting details to Google Sheet successfully. ✅

🔒 Security Considerations
Store all API keys securely using n8n environment variables or credentials vault.

Limit memory window size for privacy.

Use OAuth for Google APIs instead of plain tokens.

Validate all Telegram inputs to prevent command injection.

💡 Future Enhancements
Add support for Google Meet link creation

Include CRM integration (Notion / Airtable / Salesforce)

Enable voice-to-text for Telegram voice messages

Add fallback and error recovery mechanisms

🧑‍💻 Author
Yokesh Kumar Sundararaman
Integration Engineer | AI Automation Enthusiast
🔗 LinkedIn(linkedin.com/in/yokeshkumar-aiml)
📧 yokesh1987@gmail.com

🪪 License
This project is licensed under the MIT License.
