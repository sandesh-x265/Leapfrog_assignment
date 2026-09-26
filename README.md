# Leapfrog AI Agent Assignments

Three Python notebook assignments  exploring tool calling, weather retrieval, and AI-assisted travel planning.


**Live deployment:** [Try Sojourn - A day well spent](https://plansojourn.vercel.app/), a web app built from Assignment 3's AI travel planner.


## Assignments

| Notebook | Description | Main tools |
| --- | --- | --- |
| [Assignment 1](leapfrog_assignment1_sandesh.ipynb) | Retrieves current weather sequentially for three user-provided locations and calculates their average temperature in Celsius. | Google Gemini SDK, OpenWeather via PyOWM |
| [Assignment 2](leapfrog_assignment2_sandesh.ipynb) | Creates a one-day city itinerary using current weather, three attractions, and an estimated total visit cost. | Strands Agents, Groq, Tavily, PyOWM, custom calculator tool |
| [Assignment 3](leapfrog_assignment3_sandesh.ipynb) | Adds a Gradio interface with chat, morning/afternoon/evening itinerary cards, weather, estimated costs, sample preview, and itinerary export. | Gradio, Strands Agents, Groq, Tavily, PyOWM, Pydantic, Strands calculator |

## Setup

Use a Python environment with Jupyter Notebook, JupyterLab, or VS Code's Jupyter extension. An internet connection and API credentials are required for live requests.

1. Clone this repository and open its root folder.
2. Optionally create a virtual environment. In Windows PowerShell:

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   python -m pip install -r requirements.txt
   ```

3. Copy [`.env.example`](.env.example) to `.env` in the repository root (skip copying if you already have a `.env` file):

   ```powershell
   Copy-Item .env.example .env
   ```

   Open `.env` and replace the placeholders with your credentials:

   ```dotenv
   GEMINI_API_KEY=your_gemini_api_key
   OPENWEATHER_API_KEY=your_openweather_api_key
   GROQ_API_KEY=your_groq_api_key
   TAVILY_API_KEY=your_tavily_api_key
   ```

   Assignment 1 uses Gemini and OpenWeather. Assignments 2 and 3 use Groq, OpenWeather, and Tavily. Only the keys required by the notebook you run need to be configured. The `.env` file is excluded from Git.

4. Start JupyterLab from the repository root, or open a notebook in VS Code:

   ```powershell
   jupyter lab
   ```

5. Select your Python environment as the notebook kernel. If you installed `requirements.txt`, you can skip the notebook's first dependency installation cell and run the remaining cells in order. Otherwise, run that installation cell first. Restart the kernel after installation if prompted. Keep the notebook working directory set to the repository root so `.env` can be found.

The shared `requirements.txt` covers all three assignments and includes JupyterLab and ipykernel. Its version pins match Assignment 3's installation cell; other dependencies remain unpinned.

## Running the assignments

- **Assignment 1:** Enter three locations when prompted. The notebook displays each retrieved temperature and calculates the average when all three lookups succeed.
- **Assignment 2:** Enter a destination city when prompted to generate a one-day itinerary.
- **Assignment 3:** Run through the final cell to launch the Gradio app inline. Enter a city and optional preferences, such as `Plan a day in Kathmandu with more art and a slower pace`. The interface also provides a sample preview and itinerary download. The launch cell uses `share=False`.

Each notebook contains its own dependency installation cell; Assignment 3 pins several package versions. Model settings are defined inside the notebooks. Assignment 3 also reads the optional `GROQ_MODEL` environment variable, with additional model substitutions in its configuration cell. If a configured model is unavailable to your account, review that cell and select a supported model.

## Notes

- Weather reflects the current conditions returned by OpenWeather, rather than a forecast for a future trip.
- Attraction costs are estimates based on search results. The total represents attraction entrance/visit fees; transport, meals, and accommodation are not included in that total.
- API requests depend on provider availability, account access, and usage limits.
- Before publishing notebooks, review saved outputs for credentials or personal information. `.gitignore` excludes local secret files but does not remove data embedded in notebook outputs.
