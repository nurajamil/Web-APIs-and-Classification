# Project 3: Web APIs and Classification

---

### Background

My consultancy company services clients from sports news outlets and sports marketing agencies. One of the clients would like to run marketing campaigns for its upcoming football event and wishes to target online audience who is interested in the English Premier League. Hence, he would like to explore and understand classification models that are able to predict whether a particular football-related post is about the English Premier League. 

### Problem Statement

For the aim of this project, data is collected from two subreddits of two of the most popular football leagues in the world - English Premier League and Champions League. The goal is to build and compare different classification models that would best predict whether a specific post belongs to the English Premier League subreddit. 

---

### Executive Summary

Data is collected from two subreddits of two of the most popular football leagues in the world - English Premier League and Champions League. In total, 1,935 posts are collected for this project. Out of these posts, 992 posts come from the Champions League subreddit while 943 posts come from the English Premier League subreddit.

As some of the posts content are empty, a new feature that combined the post title and content is created and further text analysis and modelling is based on this new feature. After lemmatization and data cleaning, which includes removing URL links and non-relevant words, the top unigrams, bigrams and trigrams for each subreddit are visualised and identified. 

It is evident from the visualisations that there are a significant number of words and phrases that are common between the two subreddits. Top English clubs like Manchester City and Chelsea are mentioned in both subreddits. Additionally, some common football-related terms like goal scored, yellow card and substitution are also found in both subreddits.

On the other hand, the words and phrases that are distinct to the English Premier League subreddit seem to be related to the mid/low-tiered premier league clubs like Aston Villa and West Ham. These clubs are not involved in the Champions League. Additionally, words that are specific to the Champions League subreddit are related to the format of the tournament itself, for example, final and round.

Overall, six different models are tested. These models are Multinomial Naive Bayes, Logistic Regression and K-Nearest Neighbours, each combined with either a Count Vectorizer or a TF-IDF Vectorizer. These models are run multiple times using GridSearch Cross Validation to find the optimal hyperparameters for each model. The models are then run again for the final time with their respective optimal hyperparameters. 

Since the aim of this project is to best predict whether a specific post belongs to the English premier league subreddit, minimizing the false positive cases and maximizing the true positive predictive value are key in determining the best model. Hence, accuracy and precision are two of the metrics that are used to compare the different models and identify the best one.

---

### Data Dictionary

|---|---|---|---|
|**subreddit**|*object*|cpl, epl, football|Name of the post's subreddit of origin.| 
|**title**|*object*|cpl, epl, football|The title of each subreddit post.| 
|**selftext**|*object*|cpl, epl, football|The content of each subreddit post.| 
|**combined_text**|*object*|cpl, epl, football|The combined title and content for each subreddit post.| 
|**clean_com_text**|*object*|cpl, epl, football|The combined title and content for each subreddit post after lemmatization and cleaning.| 
|**text_count**|*integer*|cpl, epl, football|Number of word count in content for each subreddit post.| 
|**combined_count**|*integer*|cpl, epl, football|Total number of word count in combined title and content for each subreddit post.| 
|**clean_word_count**|*integer*|cpl, epl, football|Total number of word count in combined title and content for each subreddit post after lemmatization and cleaning.| 
|**label**|*categorical*|cpl, epl, football|A variable to indicate which subreddit the post belongs to. 1 indicates that the post belongs to the English Premier League subreddit while 0 indicates that it belongs to the Champions League subreddit.| 

---

### Conclusions/ Next Steps

### Conclusions

The EPL and CPL subreddits have many common words, as indicated by the top n-grams. Hence, words and phrases that are specific to each subreddit are essential. For both EPL and CPL subreddits, team names are important in classifying the posts between the subreddits. This because mentions of top-tiered clubs like Manchester City can be found in both subreddits. Hence, for EPL subreddit, words related to low and mid-tiered clubs like Everton are important as these clubs are only mentioned in the EPL subreddit. Meanwhile, for CPL subreddit, European non-English clubs like PSG are important.

Furthermore, words that are specific to the respective league are also important. For EPL subreddit, words that are associated with the domestic football league like cup are important. Mentions about domestic english competitions like FA cup are likely only to be discussed on the EPL subreddit. Meanwhile, for CPL subreddit, final, round and stage, are important. These words refer to the different stages of the CPL competition.

Overall, Logistic Regression model with TF-IDF vectorization is the best model that would predict whether a specific post belongs to the English Premier League subreddit. It has high test accuracy and high precision score. Its ROC AOC is close to 1 (0.93), indicating that the positive and negative populations (EPL and CPL posts) are almost perfectly separated. This further confirms that the logistic regression with TF-IDF vectorization is suitable for the objective of this project and it is the best model amongst all the models that have been tested.

### Next Steps

Even though Logistic Regression model with TF-IDF vectorization is concluded to be the best model, there are a few drawbacks with this model. One of the drawbacks that is evident is overfitting. Since the data used to train this model is high dimensional, this model may need to be run with larger dataset to reduce overfitting.

Hence, for the next step, more data from the same subreddits should be incorporated. Additionally, other models like Random Forest should also be tested. Random Forest Classifier is said to be useful in dealing with high dimensional noisy data. As it is based on bagging algorithm and uses ensemble learning technique, using this model may reduce overfitting problem and also reduces the variance. Therefore, the model may help to imporve the accuracy.