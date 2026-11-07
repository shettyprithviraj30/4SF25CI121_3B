# Amazon Prime Titles Data Analysis – Milestone 1

🎬 Analysis of the Amazon Prime titles catalogue (9,668 titles, 12 columns).

🛠️ Technologies and Libraries Used

- Python – Programming language.
- Pandas – Data manipulation and analysis.
- NumPy – Numerical operations.
- Matplotlib – Data visualization.
- Jupyter Notebook – Interactive coding and analysis.
- VS Code – Development environment.
- Git & GitHub – Version control and project management.

📂 Files in this Project

| File | Purpose |
|------|---------|
| `amazon_prime_titles.csv` | Original dataset |
| `data_sel_read.ipynb` | Loading, inspecting, selecting rows and columns |
| `data_understandinng.ipynb` | `loc`, `iloc`, `at`, `iat` practice |
| `data_transformation.ipynb` | Cleaning, renaming, new columns, missing values |
| `insight_generation.ipynb` | `groupby()` and `agg()` insights |
| `data_visualization.ipynb` | Matplotlib charts |

Keep the CSV in the same folder as the notebooks (the notebooks read `amazon_prime_titles.csv` by relative path).

📂 Project Tasks Performed

### 1. Data Loading and Understanding
- Imported the required Python libraries.
- Loaded the Amazon Prime CSV dataset using Pandas.
- Displayed the first and last records using `head()` and `tail()`.
- Checked dataset dimensions using `shape`.
- Examined column names and data types.
- Generated statistical summaries using `describe()`.
- Selected data using `loc`, `iloc`, `at` and `iat`.

### 2. Data Cleaning and Transformation
- Removed unnecessary columns (`show_id`, `description`).
- Checked for duplicate records (none found).
- Renamed columns (`type` → `content_type`, `rating` → `age_rating`, `listed_in` → `genres`).
- Converted columns into appropriate data types.
- Used `astype()` for datatype conversion.
- Used `pd.to_numeric()` and `pd.to_datetime()` for numerical and date conversion.

### 3. Handling Missing Values
Identified missing values using `isnull()` and handled them using:
- **Mean / Median:** Calculated for release year and movie runtime. Median is used as the safeguard fill for movie runtime (no numeric column actually has nulls in this dataset).
- **Mode:** Filled missing `age_rating` (337 rows) with the most frequent value (`13+`).
- **Label fill:** Filled missing `director`, `cast` and `country` with `"Unknown"`.
- **Left as is:** `date_added` is empty for about 98% of rows, so it was kept as missing instead of inventing dates.
- Compared missing values before and after handling.

### 4. Data Transformation Using Pandas
Practised different Pandas operations:
- `apply()` – Applied functions to individual column values.
- `lambda` – Performed simple operations on dataset columns.
- `astype()` – Changed column data types.
- Created new columns using existing data:
  - `runtime_minutes` and `seasons` – split from the `duration` text.
  - `genre_count` – number of genres per title.
  - `title_age` and `decade` – based on release year.
  - `audience` – Family / Teen / Adult grouping from the age rating.

### 5. Insight Generation Using GroupBy
Used Pandas `groupby()` and `agg()` operations to generate insights, including:
- Number of titles by content type (Movie vs TV Show).
- Average release year and runtime by content type.
- Number of titles by genre (multi-genre titles counted once per genre).
- Number of titles and average runtime by age rating.
- Title distribution by release decade.
- Title distribution by country.
- Movie runtime summary and TV shows by number of seasons.
- Comparison of titles with and without director information.

### 6. Data Visualization
Created five visualizations using Matplotlib (plus two extras):

| Graph | Purpose |
|-------|---------|
| Line Graph | Number of titles by release year |
| Bar Graph | Top 10 genres |
| Histogram | Distribution of movie runtime |
| Scatter Plot | Relationship between release year and movie runtime |
| Pie Chart | Movies vs TV Shows |
| Bar Graph (extra) | Top age ratings |
| Bar Graph (extra) | TV shows by number of seasons |

### Key Findings
- 7,814 movies (80.8%) and 1,854 TV shows (19.2%).
- Drama (3,687), Comedy (2,099) and Action (1,657) are the most common genres.
- Median movie runtime is 91 minutes; 1,342 of the 1,854 TV shows have only one season.
- `country` is missing for 8,996 titles, so country-level insights only cover the 672 titles that list one.
