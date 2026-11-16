# World Happiness Report: Exploratory Data Analysis & Insights

**Pluto Academy AI & Machine Learning Internship — Project 01**  
- **Author:** Shivshankar Dhareppa Mali  
- **Offer Letter Ref:** `PA-OL-AIML-2026-0934`  
- **Dataset Source:** [World Happiness Report (Kaggle / UN SDSN)](https://www.kaggle.com/datasets/unsdsn/world-happiness)  
- **Interactive Notebook:** [Open in Google Colab](https://colab.research.google.com/github/shiv123-coder/HappyEDA/blob/main/World_Happiness_EDA.ipynb)

---

## Project Overview

This project presents an exploratory data analysis of the World Happiness Report across the multi-year period from 2015 to 2019. The analysis investigates how GDP per capita, social support, life expectancy, personal freedom, generosity, and trust in institutions relate to national happiness scores across more than 150 countries.

The notebook is structured with short, sequential cells that perform data loading, schema cleaning, five analytical questions, seven data visualizations, and strategic policy recommendations.

---

## Analysis Summary & Rubric Alignment

### 1. Step 1: Load and Inspect Data
- Loaded 5 yearly datasets (2015–2019) containing 155 to 158 surveyed nations per year.
- Validated dimensions, schema differences, missing values, and verified zero duplicate country records per release.
- **Dataset inspection summary:**
  1. *Core Subject*: National happiness evaluated on a 0 to 10 Cantril ladder scale from the Gallup World Poll.
  2. *Key Dimensions*: Quantifies contributions from GDP, social support, life expectancy, freedom, generosity, and corruption perception.
  3. *Coverage*: 156 countries in 2019 and over 780 country-year observations from 2015 to 2019.
  4. *Data Health*: High overall integrity with zero duplicates and only one missing value in 2018 (UAE corruption).
  5. *Challenge*: Column names and regional groupings differ across release years, requiring schema normalization and a unified region lookup.

### 2. Step 2: Data Cleaning Decisions
- **Schema Normalization**: Standardized varying annual column names (such as `Family` vs `Social support`, `Economy (GDP per Capita)` vs `GDP per capita`) into a consistent schema: `country`, `region`, `rank`, `score`, `gdp`, `social`, `health`, `freedom`, `generosity`, `corruption`, `year`.
- **Region Harmonization**: Reconstructed missing regions for 2018 and 2019 using a lookup mapping derived from 2015–2016 records, with alias matching for entity changes (such as Taiwan, Hong Kong, North Macedonia, and Gambia).
- **Missing Value Handling**: Imputed the single missing corruption score for UAE in 2018 using the country's average across surrounding survey years (0.288) rather than discarding the observation.
- **Dimensionality Pruning**: Removed year-specific statistical bounds (`Standard Error`, `Whisker.high`, `Whisker.low`, `Dystopia Residual`) to ensure uniform feature vectors across all five years.

### 3. Step 3: Exploratory Analysis (5 Core Questions)
- **Question 1 (Top 10 vs Bottom 5)**: Nordic countries (Finland, Denmark, Norway, Iceland) lead the rankings with scores above 7.49. Bottom countries (South Sudan, Central African Republic, Afghanistan) average below 3.25. The top 10 average 3.5x higher social support and 2.8x higher life expectancy than the bottom 5.
- **Question 2 (Key Drivers)**: GDP per Capita ($r = 0.794$) and Social Support ($r = 0.777$) show the strongest positive correlation with happiness, followed by Healthy Life Expectancy ($r = 0.780$) and Freedom ($r = 0.567$). Generosity displays negligible linear correlation ($r = 0.076$).
- **Question 3 (Regional Spread)**: Western Europe (mean: 6.898) and North America (mean: 7.085) maintain the highest regional averages. Latin America exhibits the widest internal disparity (spread = 2.975 points), ranging from Costa Rica (7.167) to Venezuela (4.707).
- **Question 4 (5-Year Shifts)**: Countries with largest improvements from 2015 to 2019 include Benin (+1.54) and Ivory Coast (+1.86). Venezuela experienced the steepest decline (-2.10) over the period.
- **Question 5 (Economic Disparity)**: Costa Rica (Happiness Rank 12 vs GDP Rank 55, +43 spots), Mexico (+37 spots), and Guatemala (+47 spots) achieve happiness levels well above their economic rank. In contrast, mineral-wealthy nations like Botswana (Rank 148 in happiness vs Rank 75 in GDP) exhibit large negative rank gaps.

---

## Visualizations

The notebook generates seven chart types using restrained, publication-grade styling:

| Figure | Chart Type | Subject |
| :--- | :--- | :--- |
| **Chart 1** | Bar Chart | Top 10 Happiest Countries in 2019 with score callouts |
| **Chart 2** | Line Chart | 5-Year Regional Happiness Score Trends (2015–2019) |
| **Chart 3** | Histogram | Global Distribution of Happiness Scores (Mean & Median) |
| **Chart 4** | Scatter Plot | GDP per Capita vs. Happiness Score with key country annotations |
| **Chart 5** | Donut Chart | Regional representation of surveyed nations in the 2019 sample |
| **Chart 6** | Heatmap | Pearson correlation matrix across explanatory dimensions |
| **Chart 7** | Box Plot | Regional distribution and variance in happiness scores |

---

## Step 5: Insights & Recommendations

1. **Economic output is strongly correlated with happiness, but has diminishing returns (Chart 4, Chart 6)**:
   GDP per capita exhibits the highest correlation with happiness ($r = 0.794$). However, above a certain wealth threshold, extra GDP does not translate linearly into higher happiness. For instance, Singapore and Qatar report among the highest GDP per capita scores in the world (~1.68), yet rank 34th and 29th respectively. Meanwhile, Costa Rica achieves rank 12 globally with a GDP score of 1.03, compensating through social ties and healthcare access.

2. **Social support is the strongest non-monetary pillar of well-being (Chart 6, Table Q1)**:
   Social support has the second highest correlation with national score ($r = 0.777$). Between the top 10 and bottom 5 countries, the average social support score drops by roughly 3.5x (from 1.53 down to 0.44). For policy decisions, investment in social safety nets, public parks, community care, and family support infrastructure yields direct measurable returns in population well-being.

3. **Regional disparities remain persistent over time (Chart 2, Chart 5)**:
   Western Europe and North America average around 6.9 to 7.1 in happiness, whereas Sub-Saharan Africa averages 4.31. Over the five observed years (2015 to 2019), regional trajectories remained steady with little churn across geographic tiers, underscoring that structural improvements require long-term institutional stability.

4. **Latin American nations punch consistently above their economic wealth (Table Q5, Chart 4)**:
   In the rank disparity analysis, Costa Rica (+43 spots), Mexico (+37 spots), and Guatemala (+47 spots) achieve happiness scores far higher than their GDP per capita rank would predict. By contrast, mineral-rich nations like Botswana (Rank 148 in happiness vs Rank 75 in GDP) exhibit large negative rank gaps, likely due to internal inequality and health challenges.

5. **Generosity shows negligible correlation with national happiness scores (Chart 6, Table Q2)**:
   Generosity had an $r = 0.076$ correlation with happiness. While individual charitable acts are positive, national life satisfaction is driven primarily by baseline economic security, public healthcare, personal freedom, and institutional trust rather than discretionary donations.

### Finding That Surprised Me the Most:
The rank disparity analysis was the most surprising takeaway. Comparing GDP rank against happiness rank demonstrates that wealth alone is an incomplete proxy for national well-being. Middle-income nations with strong familial structures and accessible healthcare routinely outscore far wealthier peers who face higher social isolation or systemic inequality.

---

## Repository Structure

```text
HappyEDA/
├── data/
│   ├── 2015.csv
│   ├── 2016.csv
│   ├── 2017.csv
│   ├── 2018.csv
│   └── 2019.csv
├── visualizations/
│   ├── 01_top_10_countries_bar.png
│   ├── 02_regional_trends_line.png
│   ├── 03_score_distribution_histogram.png
│   ├── 04_gdp_vs_happiness_scatter.png
│   ├── 05_regional_breakdown_pie.png
│   ├── 06_correlation_heatmap.png
│   └── 07_regional_boxplot.png
├── World_Happiness_EDA.ipynb    # Clean Jupyter Notebook with modular short cells
└── README.md                    # Project documentation & insights report
```

---

## How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/shiv123-coder/HappyEDA.git
   cd HappyEDA
   ```
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```
3. Open the notebook:
   ```bash
   jupyter notebook World_Happiness_EDA.ipynb
   ```
