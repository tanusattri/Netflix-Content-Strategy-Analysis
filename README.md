# Netflix-Content-Strategy-Analysis

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results](#results)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#references)

### Project Overview
This project analyzes over 8,000 Netflix titles to uncover the platform's shift from a movie-rental service to a global TV production powerhouse. Using Python and Pandas, I cleaned unstructured metadata and performed time-series analysis to track content growth from 2008 to 2021. The results, visualized through Seaborn, reveal a strategic 40% surge in TV Show acquisitions and a major pivot toward mature (TV-MA) and international audiences. This analysis provides a data-driven look at how Netflix uses content variety to dominate the global streaming market.

### Data Sources
Netflix Movies and TV Shows Dataset via Kaggle, consisting of 8,800+ records of titles, genres and metadata.

### Tools 
- Python (Pandas, NumPy)
- Matplotlib
- Seaborn
- Jupyter Notebook

### Data Cleaning
1. Handling Null Values: Replaced missing entries in director, cast, and country with "Unknown" to maintain dataset integrity while avoiding the loss of 30% of the total records.
2. Standardizing Date Formats: Converted the date_added string column into a datetime object and extracted year_added to enable accurate chronological and time-series analysis.
3. Removing Duplicates and Errors: Identified and removed duplicate entries and dropped rows with missing rating or duration to ensure the accuracy of the statistical summaries.

### Exploratory Data Analysis 
1. Content Distribution Analysis: Performed a frequency analysis of Movies vs. TV Shows to visualize the library split, discovering that while Movies dominate the total count, TV Shows have seen a significant upward trend in recent years.
2. Temporal Trend Mapping: Plotted content release patterns from 2008 to 2021 using line charts to identify peak acquisition periods and the impact of Netflix’s pivot toward original "Netflix Series."
3. Categorical Profiling: Analyzed the Top 10 genres and rating distributions (e.g., TV-MA vs. PG-13) using bar charts to define Netflix's primary target demographics and most successful content niches.

### Data Analysis
```Python
import pandas as pd
df = pd.read_csv('netflix_titles.csv')
df['director'] = df['director'].fillna('Unknown')
df['cast'] = df['cast'].fillna('Unknown')
df['country'] = df['country'].fillna('Unknown')
df['date_added'] = pd.to_datetime(df['date_added'].str.strip())
df['year_added'] = df['date_added'].dt.year
df.dropna(subset=['rating', 'duration'], inplace=True)
```

### Results 
1. The Strategic Pivot to TV: The analysis revealed that while Movies currently make up 70% of the total library, the acquisition of TV Shows has grown 40% faster than movies since 2019. This indicates a clear business shift toward episodic content to drive higher user retention and "binge-watching" behavior.
2. Target Audience Maturity: Over 50% of Netflix's total content is categorized as TV-MA or TV-14, proving that the platform has successfully pivoted away from being a family-oriented service toward a mature, adult-centric entertainment provider.

### Recommendations
1. Strategic Content Rebalancing: Given that TV Shows generate higher long-term retention through episodic viewing, Netflix should aim for a 60:40 Movie-to-TV ratio (currently it favors movies more heavily). To improve completion rates, the platform should prioritize acquiring "fresh" movie content (released within the last 5 years) to bridge the age gap between its film and TV libraries.
2. Deepening International & "Mature" Investment: With over 35% of the library already rated TV-MA and a high growth rate in international productions (like K-Dramas and Spanish thrillers), Netflix should double down on localized original content. Specifically, leveraging data-driven "micro-genres" for specific regions (e.g., Indian crime dramas or South Korean horror) will help maintain its 80% recommendation-driven viewing rate in emerging markets.

### Limitations
Lack of Engagement Metrics: The dataset is restricted to metadata (titles, genres, and release years) and does not include user viewership data, ratings, or completion rates, meaning we can identify what content Netflix is producing, but not necessarily what is most successful or profitable.

### References
1. Dataset Source: Kaggle - Netflix Movies and TV Shows
   - [https://www.kaggle.com/datasets/shivamb/netflix-shows]
2. Tool Documentation: Pandas, Seaborn, Matplotlib
   - [https://pandas.pydata.org/docs/]
   - [https://seaborn.pydata.org/]
   - [https://matplotlib.org/]
3. Analysis Methodology: Inspired by Exploratory Data Analysis (EDA) best practices for content streaming platforms
