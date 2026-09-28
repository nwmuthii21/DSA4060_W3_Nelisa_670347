# DSA 4060: Week 2 Practical Task - Recommendation Data and Popularity Baselines

NAME: NELISA WACERA MUTHII

ADM: 670347

The objective of this project was to clean and explore user-movie interaction data, measure matrix sparsity, and build a simple popularity-based recommender system using Python and Pandas.

## Repository Contents
* `DSA_4060_Week2_Notebook.ipynb`: The complete Jupyter Notebook containing step-by-step code execution, data exploration, and visualizations.
* `DSA_4060_Week2_Movie_Ratings.csv`: The original input dataset containing user ratings, movie IDs, titles, and timestamps.
* `top_10_recommendations.csv`: The exported CSV file containing the top 10 popularity-based movie recommendations.
* `README.md`: Documentation explaining the project structure, tasks, and findings.

---

## Task Summary

### 1. Data Inspection
* Loaded the raw interaction dataset to check its structure, dimensions, and types.
* Identified missing user/movie IDs and duplicate entries.
* Verified that the rating column contained anomalies (such as `-1`, `0`, and `6`) outside the standard expected 1–5 scale.

### 2. Data Cleaning
* Removed duplicate row records.
* Dropped records with missing `user_id` or `movie_id` fields.
* Filtered the dataset to retain only valid ratings within the expected 1 to 5 scale, ensuring data integrity.

### 3. Exploratory Data Analysis (EDA)
Calculated core metrics from the cleaned dataset:
* **Total Ratings:** 500
* **Unique Users:** 50
* **Unique Movies:** 24
* **Most Active User:** `U010`
* **Most-Rated Movie:** *Mountain Echoes*
* **Average Rating:** 3.45 / 5.00

### 4. User-Item Interaction Matrix and Sparsity
* Constructed a pivot table mapping users (rows) against movies (columns) with ratings as cells.
* Calculated matrix sparsity: **64.17%**.
* **Interpretation of Sparsity:** Over 60% of the possible user-movie interaction cells are empty (`NaN`), meaning most users have only rated a fraction of the available catalog. This highlights the sparse nature typical of collaborative filtering environments.

### 5. Popularity-Based Recommender System
* Grouped data by movie to calculate average ratings and total rating counts.
* Implemented a threshold requirement of **at least 10 ratings** to filter out low-sample noise.
* Sorted remaining titles by average rating to isolate the top-performing movies and exported the final list to `top_10_recommendations.csv`.

---

## Interpretation of Results

The popularity-based recommendations appear at the top because they strike a practical balance between high user satisfaction and statistical reliability, ranking movies with the highest average scores only after filtering out titles with fewer than 10 ratings to prevent skewed results from small sample sizes.

A primary advantage of this approach is its ability to handle the cold-start problem seamlessly, allowing new users or platforms with no prior interaction history to immediately receive sensible, trending suggestions. 

Limitations:

* Provides entirely generic recommendations that ignore individual user preferences or niche tastes.

* Creates a self-reinforcing feedback loop where already popular items receive continuous exposure while unique or less-mainstream titles remain undiscovered.
