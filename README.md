# Text Analytics in the News

This is a repository for everything relating to text analytics at BBC News Labs.

## Text Mining

There is great potential in the use of data science and text mining to extract new insights about news. Analysing vast amounts of text can tell us more about the trustworthiness of content. As part of the [Trust Project](http://thetrustproject.org/), which is exploring the role of trust in news, Google Fellows at BBC News Labs have developed two prototypes to encourage trust in news content. One of these prototypes is the Stat Index.

### Stat Index

#### What is the Stat Index?
The tool mines content, creating scores and visualisations to measure the extent to which statistical insights have been used. It uses a pre-processed dictionary of statistical terms and a corpus-based approach. The tool takes news content URLs, parses the HTML, converts it to text and then analyses the use of statistical insights like "percent", "data" and "map". It was developed using [R](https://www.r-project.org/), an extremely popular statistical programming language that's increasingly being used by Journalists. Below is an example visualisation that can be embedded in webpages.

![alt tag](https://studentdatalabs.files.wordpress.com/2016/08/statindex-scores1.jpg)

#### How do you use it?
First, clone or download the repo, unzip the file and open the Stat Index folder. In the Stat Index folder above you'll find two more folders - one contains the [statistical dictionary](https://github.com/BBC-News-Labs/Text_Analytics/tree/master/StatIndex/StatIndex-StatDictionary) (a collection of statistical terms by type and complexity) and the other with the code to carry out the [analysis](https://github.com/BBC-News-Labs/Text_Analytics/tree/master/StatIndex/StatIndex-Analysis) and create the scores. The four-part analysis should be carried out in the following order - JSON, HTML, Dictionary/Corpus and Scoring. 

While the Stat Index makes use of Freebird, a small internal tool being created by [BBC R&D](http://www.bbc.co.uk/rd), it can be used to test and compare your own news - simply choose your URL and run it through [Part 2](https://github.com/BBC-News-Labs/Text_Analytics/blob/master/StatIndex/StatIndex-Analysis/R%20Code%20-%20StatIndex%20-%20HTML.R). More info can be found in this [quick quide](https://github.com/BBC-News-Labs/Text_Analytics/blob/master/StatIndex/Guide.md) but if you're not a developer, journalist or researcher don't worry! A more friendly step-by-step workflow will soon be published online.

#### What does the future hold?
The Stat Index will be considered a success if it is used by the public and Journalists to learn more about the relationship between trust, statistics and news. The prototype is in testing phase after inital tests were successful.  The data and code are in development and features are being added. This repository will be regularly updated to incorporate these changes and collaboration is more than welcome. The Statistical Data Dictionary, for example, is a work in progress and will change as more research is undertaken.

### [NewsStat](https://github.com/lbuk/NewsStat)
NewsStat is an R package and set of functions that allow you to extract text containing key statistics from online news. Simply enter a URL and it will return sentences containing stats. Once it's been installed, using NewsStat is as easy as:

```
NewsStat("http://www.bbc.co.uk/news/uk-37345436")
```

#### What can I use NewsStat for?
Looking for statistics in text can be a difficult and arduous task. NewsStat can make your life easier by quickly extracting key stats from online news content. You can use [NewsStat](https://github.com/lbuk/NewsStat) for blogs, websites and other non-news sites as well. 
It was developed following a Google Fellowship at BBC News Labs. Like the Stat Index, NewsStat is a work in progress - feel free to contribute, build on it and let me know if there are any issues.

---

## Topic Modelling

We are trying to answer the question *"What is this article about?"* from looking at word frequencies in news articles. Initially we are building on the corpus of BBC News articles to try different strategies for article classification, clustering and prediction of the respective topic.

For the moment this is more a proof of concept thing, and for that matter we decided to focus only on english language BBC news articles for the purpose of training and testing.

There are three strategies we want to explore initially are...

- Topic Modelling with number of topics as a variable (clustering)
- Topic Modelling with a given number (and possibly label) of topics
- Supervised topic modelling using human curated training sets

### (1) Topic Modelling with number of topics as a variable (clustering)

Starting without any prior knowledge: Given a set of news articles, we don't know the number of topics nor the labels. We want to experiment with PCA as well as a couple of clustering methods to infer the number of topics from the the word frequency distributions in news articles.

Some ideas:

- Depending on the vocabulary, they word frequency matrix may become huge --> maybe we can limit the vocabulary?
- In a news story the first few sentences are supposed to contain the core information of the article. Using only those first sentences, we may get rid of noise (i.e. synonyms, word-games, irony...) contained in the body of the text and increase performance?

### (2) Topic Modelling with a given number (and possibly label) of topics

Its not that we don't know anythings about topics: There are of course broad topic groups (assigned within BBC and throughout other news organisations) and varying degrees of sub-topic-breakdowns. So, it may be easier to fix the number (and maybe label) for possible topics beforehand and do unsupervised classification on word frequency distributions in news articles. 

Some ideas:

- is SOM (self organising maps maybe something to try?)
- how many articles would we need for an unsupervised approach (much much more than for the supervised version, right?)


### (3) Supervised topic modelling using human curated training sets

Using news articles and human assigned topics or tags, we could learn the relation between the word frequency distribution and the topic. The advantage would be that the learned relationships would match with the topics that are currently used within BBC's content store. 

Some ideas:

- How many 'tagged' news articles would we need to train a model?
- Is there already a training set that is sufficiently large and representative of all news articles?
- How could we harness existing topic/tag assignments for training?
- How could we harness the journalists or the reader to assign or validate topics?
- Is there a way to re-train incrementally (as new articles are published every day...)

