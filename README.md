# IBM SpaceX Capstone

Predicting whether the **Falcon 9** first stage will land successfully—and
understanding the business drivers behind it.

This repo contains the work I completed for the **IBM Data Science
Professional Certificate capstone**.  
It walks through data collection, wrangling, exploration, modelling, and
dashboarding, all aimed at helping a hypothetical competitor bid intelligently
against SpaceX launches.

---

## Summary

| File / Notebook | What happens inside | Key libraries |
|-----------------|--------------------|-------------------------|
| **`spacex-data-collection-api.ipynb`** | Queries the SpaceX REST API for launch metadata (flight number, payload mass, launch site, success flag). Saves raw JSON → `spacex_launch_raw.json`. | `requests`, `pandas` |
| **`spacex-webscraping.ipynb`** | Scrapes additional launch-price info from Wikipedia and SpaceX pages to enrich the dataset. | `BeautifulSoup`, `lxml` |
| **`spacex-data-wrangling.ipynb`** | Cleans & merges API + scraped data, engineers the binary target **`LandingSuccess`**, one-hot-encodes categorical features, and exports `spacex_clean.csv`. | `pandas`, `numpy` |
| **`spacex-eda-dataviz.ipynb`** | Visual EDA on payload, flight number, and year-over-year trends. Includes Box, Scatter, and interactive Plotly charts. | `matplotlib`, `seaborn`, `plotly.express` |
| **`spacex-eda-sql.ipynb`** | Loads the clean data into an in-memory SQLite DB; runs SQL queries for total payload, success counts, and minimum/maximum payloads for successful landings. | `sqlite3`, `pandas`, `sqlalchemy` |
| **`launch_site_locations.ipynb`** | Maps four launch sites on an interactive Folium map; overlays circle markers coloured by landing success rate. | `folium`, `geopy`, `shapely` |
| **`spacex-ml-predictive-analysis (1).ipynb`** | Trains multiple classifiers (Logistic R, SVM, KNN, DecisionTree, RandomForest) to predict **`LandingSuccess`**; evaluates with Accuracy, F1, and Jaccard; selects the best model. | `scikit-learn`, `pandas`, `matplotlib` |
| **`spacex_dash_app.py`** | Production-ready Dash app: dropdown to filter launch sites, slider for payload range, and multiple interactive Plotly charts to explore success rates and payload relationships in real time. | `dash`, `plotly.graph_objs`, `pandas` |
