# 🤖 AI-Powered Code Review Assistant

🚀 An AI-driven GitHub Action that automatically reviews pull requests, summarizes code changes, generates test plans, and provides intelligent developer feedback using GPT-4o, Claude, or Gemini.  
Built for modern software engineering workflows and intelligent CI/CD automation.

---

## 🌟 Overview

This project is a fully-featured, production-grade **AI Code Review Assistant** that acts like an intelligent teammate:

- Automatically reviews your PRs
- Suggests unit tests
- Flags vulnerabilities
- Generates release notes
- Learns your project’s style over time

It’s perfect for **SDEs, open-source contributors, and AI engineers** who want to showcase **full-stack + AI + DevOps integration**.

---

## ✅ Complete Feature List

### 🧩 1. Core Features
| Feature | Description |
|----------|--------------|
| `/review` | Performs detailed AI-powered code reviews |
| `/describe` | Summarizes PRs into natural-language explanations |
| `/improve` | Suggests refactors and code quality improvements |
| `/ask` | Lets developers query PRs (e.g., “Explain this function”) |
| Multi-Platform Support | Works with GitHub, GitLab, Bitbucket, Azure DevOps |
| Configurable Prompts | Customize tone, style, and review depth via `.pr_agent.toml` |
| PR Compression | Handles large diffs using intelligent summarization |
| Self-Hosted Privacy | Uses your own OpenAI API key; no external data storage |
| CLI, Docker, and GitHub Action Support | Run locally or in CI/CD pipelines |

---

### ⚙️ 2. Custom Enhancements
| Feature | Description |
|----------|--------------|
| **AI Test Plan Generator 🧪** | Automatically generates unit test cases using GPT-4o |
| **Smart Review Skipping 🧹** | Skips trivial PRs (typos, docs, dependency bumps) |
| **Multi-Reviewer Mode 🧠** | Combines personas — Strict, Security, Mentor — for richer reviews |
| **Custom Model Selection ⚙️** | Switch between GPT-4o, Claude, or Gemini |
| **AI Personality Customization 🎭** | Choose review tone: Friendly, Strict, Teaching, etc. |
| **Changelog Generator 🧾** | Auto-generates `CHANGELOG.md` entries |
| **Enhanced GitHub Workflow 🚀** | Optimized CI with caching, tagging, and concurrency |
| **Security Scan Mode 🔐** | Detects unsafe code patterns using OWASP-style analysis |
| **Lint + AI Hybrid Review 🧰** | Combines pylint/flake8 static analysis with AI reasoning |

---

### 🌐 3. Optional Advanced Add-Ons
| Feature | Description |
|----------|--------------|
| **PR Chat Interface 💬** | Get contextual AI replies inside PR threads |
| **FastAPI Microservice ⚡** | Backend service for triggering reviews |
| **Analytics Dashboard 📊** | Visualize PR counts, model cost, and AI accuracy |
| **RAG Context Integration 📚** | Adds documentation snippets for context-aware reviews |
| **Auto-Fix / Implement Mode 🛠️** | Suggests code patches directly in PR comments |
| **Slack/Discord Integration 🔔** | Sends summarized PR reports to your chat app |

---

## 🧾 Tech Stack

| Category | Tools |
|-----------|--------|
| **Languages** | Python, YAML, TypeScript (for optional UI) |
| **Frameworks** | FastAPI, Dynaconf, OpenAI SDK |
| **AI Models** | GPT-4o, Claude, Gemini |
| **CI/CD** | GitHub Actions |
| **Infrastructure** | Docker-ready, self-hosted compatible |
| **Version Control** | GitHub, GitLab |

---

## 🧭 Repository Structure

AI-Code-Review-Assistant/
├── .github/
│ └── workflows/
│ └── ai-review.yml
├── pr_agent/ # Core AI logic
├── custom_ai/
│ ├── testplan.py # GPT-4o test plan generator
│ ├── review_modes.py # Multi-reviewer persona logic
│ ├── security_review.py # OWASP-style security checks
│ └── utils/
│ └── openai_client.py # Efficient API wrapper
├── api/
│ └── review_server.py # Optional FastAPI microservice
├── CHANGELOG.md
├── .pr_agent.toml
├── README.md
└── requirements.txt

yaml
Copy code

---

## ⚙️ Installation & Setup

### 1️⃣ Clone and Install

```bash
git clone https://github.com/YOUR-USERNAME/AI-Code-Review-Assistant.git
cd AI-Code-Review-Assistant
pip install -r requirements.txt
2️⃣ Add Environment Variables
Create a .env file or use GitHub secrets:

bash
Copy code
OPENAI_KEY=your_openai_api_key
GITHUB_TOKEN=${{ secrets.GITHUB_TOKEN }}
3️⃣ Set Up GitHub Action
.github/workflows/ai-review.yml:

yaml
Copy code
name: AI Code Review
on:
  pull_request:
    types: [opened, synchronize]
jobs:
  ai_review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run AI Review
        run: python review_pipeline.py
        env:
          OPENAI_KEY: ${{ secrets.OPENAI_KEY }}
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
🧠 How It Works
pgsql
Copy code
Pull Request Created
        ↓
Fetch Code Diff
        ↓
Static Lint Check
        ↓
Generate AI Prompts
        ↓
GPT-4o Review + Test Plan
        ↓
Security + Multi-Reviewer Merge
        ↓
Post Comments on GitHub PR
        ↓
Update Changelog / Notify Slack
🧩 Example AI Output
PR Example:
Adds new calculate_discount() function in utils.py

AI Review Summary:

python
Copy code
✅ Logic is correct and readable  
⚠️ Suggestion: Add validation for negative prices  
💡 Type hints: def calculate_discount(price: float, percentage: float) -> float  
🔐 Security: No unsafe patterns found  

🧪 Test Plan:
- price=100, percentage=10 → expect 90
- price=0, percentage=50 → expect 0
- price=-10 → handle gracefully
💬 Reviewer Personas
Persona	Description
🧑‍💼 Strict Reviewer	Focuses on standards and edge cases
🧑‍🏫 Mentor Reviewer	Explains logic and gives learning tips
🧑‍💻 Security Reviewer	Detects vulnerabilities and unsafe patterns

🔒 Security Scan Examples
Detected Pattern	AI Suggestion
eval() usage	“Avoid using eval(); use ast.literal_eval().”
hashlib.md5()	“MD5 is insecure; use bcrypt or sha256.”
Missing input checks	“Validate all user inputs before processing.”

🧾 Example CHANGELOG Output
markdown
Copy code
## v1.2.0 — 2025-10-31
- ✅ Added discount calculation function
- 🧪 Added 3 unit tests for validation
- ⚡ Optimized rounding logic
🧰 Future Enhancements
Add RAG context for large codebases

Integrate Slack & Discord notifications

Introduce Auto-Fix patch generation

Add dashboard UI with commit analysis

👨‍💻 About the Author
Developed by Sandeep Kumar CM, exploring how LLMs like GPT-4o can transform software engineering workflows through automated PR analysis, intelligent test generation, and DevOps integration.

🪪 License
This project is licensed under the MIT License.





