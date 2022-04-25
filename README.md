# Movies - Extract, Transform, Load

# Overview 

Amazing Prime, an online movie streaming company, is looking for a database that will collect information from a Wikipedia Movie Database, Kaggle Metadata and MovieLens Reviews.  The process of combining the data into one useable dataset is called Extract, Transform, Load (ETL).  Amazing Prime requested an automated process to take the date and transform it into a SQL Database. 

# Results

Extract

The first step of Extract took the three data sources, downloaded them and then loaded them into Pandas DataFrames.  Files pulled from various sources will have different structures and labels.  In order to get to the goal of a combined dataset for SQL, we need to understand the structure of each data sources. 

Transform

Before the Wikipedia data and the Kaggle metadata files can be merged together, we needed to clean the Wikipedia data and transform it to match the structure of the Kaggle metadata. Regular expressions were used to search the data and clean up the format.  Large datasets can have a lot of variability in the format used to input data.  Regular expressions allowed for transforming the data to uniform formats after searching through the rows. Rows with null values were dropped as well as duplicate occuranes of IMDB ids.  Once the Wikipedia data was cleaned, the DataFrame went from 193 columns to 23 usable columns. 

Once the Wikipedia Data was transformed, it could be merged with the Kaggle Metadata. The merged DataFrame (movie_df) was then merged with the Movielens reviews to create movies_with_ratings.df.  During the merge process, cells with no listed rating were replaced with a "0" value.  

Load

The ETL process was connected to SQL by placing the values in tables in Postgres. As a check in PGAdmin, a query was run to check the imported data to ensure all the CSV data was loaded.  The images below show that 6,502 rows were imported to the movie table and 26,024,389 were imported into the ratings table. The imports were successfull and all the rows of the cleaned data were imported. 

<img width="157" alt="movies_query" src="https://user-images.githubusercontent.com/98054953/165010407-afdee477-f9ac-4cbd-8368-d3d680445b71.png"> <img width="157" alt="ratings_query" src="https://user-images.githubusercontent.com/98054953/165010426-6bdcaa58-cc2a-4038-9877-0e40f2cd506a.png">


