<!-- ## DOCENT: Learning Self-Supervised Entity Representations from Large Document Collections -->

## Learning Self-Supervised Entity Representations from Large Document Collections

The website contains additional data and scripts for the EACL-2021 paper **DOCENT: Learning Self-Supervised Entity Representations from Large Document Collections** ([preprint](http://storage.googleapis.com/gresearch/docent/docent_eacl2021_final_v3.pdf))

Please, see [https://goo.gle/research-docent](https://goo.gle/research-docent) for the *Reviews2MovieLens* dataset and modeling code. 

## Datasets

### Reddit Movie Suggestion

The [dataset](https://github.com/urikz/docent/raw/gh-pages/docent/reddit/reddit.json) contains a collection of 4765 movie-seeking queries and corresponding recommendations, collectively curated and voted on by the [Reddit Movie Suggestions](https://www.reddit.com/r/MovieSuggestions) community. Worth noting are (a) the conversational, human-to-human language of the queries; (b) the community-recommended movies that, while sparse and possibly biased, can be used as a source of ground truth. While modest in size, the dataset is well-suited to evaluate zero-shot performance on the movie ranking task defined in [Section 3.3](http://storage.googleapis.com/gresearch/docent/docent_eacl2021_final_v3.pdf).

A sample request is below. 
```
{
    "request": {
        "query_original": "Unreliable Narrator <p>Any suggestions for movies containing unreliable narrators? (Characters version of events is false through mental illness, narcissism, naivety etc) </p>\n",
        "query_full": "Unreliable Narrator Any suggestions for movies containing unreliable narrators? (Characters version of events is false through mental illness, narcissism, naivety etc)  ",
        "query_title": "Unreliable Narrator"
    },
    "response": {
        "result": [
            {
                "score": 16.0,
                "asin": "B00003CWQ2"
            },
            {
                "score": 16.0,
                "asin": "B000JMK6LW"
            },
            {
                "score": 16.0,
                "asin": "B00003CXZ3"
            },
        ]
    }
}
```

``score`` corresponds to how many upvotes the answer has received.

## Scripts

### Closed Vocabulary Tag Prediction

In this scenario, evaluation is done on a holdout set of [1000 movies](https://urikz-research-docent.s3.us-west-1.amazonaws.com/MovieLensTagPrediction/MoviesHoldout/Data/test.asin.csv).

See evaluation script [here](https://github.com/urikz/docent/blob/gh-pages/docent/tag/closed/MoviesHoldoutEval.ipynb) or

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/urikz/docent/blob/gh-pages/docent/tag/closed/MoviesHoldoutEval.ipynb)

### Open Vocabulary Tag Prediction

This task is evaluated by withholding parts of the tag vocabulary ([500 tags](https://urikz-research-docent.s3.us-west-1.amazonaws.com/MovieLensTagPrediction/TagsHoldout/Data/test.tag.csv) and [6392 movies](https://urikz-research-docent.s3.us-west-1.amazonaws.com/MovieLensTagPrediction/TagsHoldout/Data/test.asin.csv)) so that those tags are never seen in training.

See evaluation script [here](https://github.com/urikz/docent/blob/gh-pages/docent/tag/open/TagsHoldoutEval.ipynb) or

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/urikz/docent/blob/gh-pages/docent/tag/open/TagsHoldoutEval.ipynb)


<!-- ## Citation

Please cite the following paper if you use the data in any way:
```bibtex
TBD
```
 -->