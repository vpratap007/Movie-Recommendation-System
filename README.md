---

# Movie Recommendation System

## Overview

This project is a content-based movie recommendation system that suggests movies based on several features like genres, keywords, cast, and crew. The system utilizes the TMDB 5000 Movies and Credits datasets to generate recommendations by analyzing the metadata of the movies.

## Datasets

The datasets used in this project are:

1. **Movies Dataset (`tmdb_5000_movies.csv`)**: Contains details such as budget, genres, homepage, production companies, release date, revenue, runtime, and user ratings for each movie.
2. **Credits Dataset (`tmdb_5000_credits.csv`)**: Contains information about the cast and crew of the movies.

The two datasets are merged using the `title` column to create a unified dataset for building the recommendation system.

## Features

- **Genres**: The genres of the movies are extracted and processed.
- **Keywords**: Keywords related to the movie are used to enrich the metadata.
- **Cast**: Top three main actors for each movie are considered.
- **Crew**: The director of the movie is included as an important feature.

## System Functionality

### Steps:

1. **Data Preprocessing**:
   - Merging the movies and credits datasets using the `title` column.
   - Extracting and processing the genres, keywords, cast, and crew columns.
   - Using `ast.literal_eval()` to convert JSON-like strings into Python objects.
   - Selecting the top three actors from the cast and identifying the director from the crew.

2. **Feature Engineering**:
   - Text data in genres, keywords, cast, and crew are converted into lists of words or names for further processing.
   - The overview of each movie is also analyzed for relevance.

3. **Recommendation System**:
   The system will compare movies based on their metadata and recommend similar movies. The similarity between movies can be calculated using methods like:
   - Cosine Similarity
   - Count Vectorizer

### Example Output:

Given a movie like "Avatar", the system can recommend movies that share similar genres, actors, or have a similar plot structure.

## Requirements

- Python 3.x
- Libraries:
  - `numpy`
  - `pandas`
  - `ast` (for parsing string-represented lists)
  
You can install these packages using pip:
```bash
pip install numpy pandas
```

## Usage

1. Load the datasets into the program using pandas:
   ```python
   movies = pd.read_csv('tmdb_5000_movies.csv')
   credits = pd.read_csv('tmdb_5000_credits.csv')
   ```

2. Merge the datasets on the movie `title`:
   ```python
   movies = movies.merge(credits, on='title')
   ```

3. Apply data preprocessing steps to extract relevant features (genres, keywords, cast, crew).

4. Use the processed data to build a recommendation function that suggests similar movies based on the input movie.

## Future Enhancements

- Integrate more advanced NLP techniques for better analysis of movie overviews.
- Implement collaborative filtering based on user ratings and interactions.
