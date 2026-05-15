## Agent - Architecture Diagram
<img width="2121" height="1131" alt="agent_architecture drawio" src="https://github.com/user-attachments/assets/63a4cace-3c17-4ad1-9142-09ba12d10075" />

## Setup
Clone the repository https://github.com/rajeshksharmasls/homework-1/

You need:

uv to manage Python and packages. Install once:

curl -LsSf https://astral.sh/uv/install.sh | sh
Windows: see https://docs.astral.sh/uv/getting-started/installation/.

An OpenAI API key with at least a few cents of credit. Create one at https://platform.openai.com/api-keys. The notebooks prompt for it on first run (the input is hidden as you type).

## Run
git clone https://github.com/rajeshksharmasls/homework-1.git

cd homework-1

# install jupyter and the LangChain packages (one-time)
uv add jupyter langchain-openai langchain-core pandas

## From the agent notebook
- Why a fixed pipeline cannot answer multi-source questions.
- How LangChain's @tool decorator and bind_tools() work.
- How to write the ReAct loop by hand: Thought -> Action -> Observation -> repeat -> Final Answer.
- How to read an agent's trace and spot bad tool choices.
- The new failure modes that come with agents (running in circles, premature termination, hallucinated facts).
  
## Optional: rebuild the database
rm -f spacex_launches.db

sqlite3 spacex_launches.db < seed.sql

# The agent 
uv run jupyter lab agent.ipynb

## What's in this repo
- agent.ipynb              - A multi-tool ReAct agent by hand. The LLM picks the tool.
- spacex_launches.db       - SQLite database (18 SpaceX missions) - used by both
- seed.sql                 - SQL to recreate the database
- schema.md                - schema description for the LLM
                              (column meanings + allowed values + domain terms + few-shot)
- vehicle_specs.json       - rocket specs (thrust, height, reusability...)
                             used as the agent's second data source
- diagrams/                - draw.io source + PNG exports for agent architecture
- pyproject.toml           - uv project file (so `uv add ...` works)
- README.md                - this file
- Results Snapshots.docx   - Snapshots of the responses of the agent
