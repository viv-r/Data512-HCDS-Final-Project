
## A4: Using word embedding models to understand bias in web communities.

### Introduction

Word embedding models like word2vec and GloVe are widely used today as the 'first-step' in most NLP pipelines. Several pre-trained models exist, and each model captures the biases of the community that had produced the raw text data on which the model was trained. This project will compare the biases (limited to gender, religion, and race) between different internet communities (Wikipedia, General Web Common Crawl, and Twitter) using word embedding models that were trained on text from those websites. A second goal of this project is to validate methods to de-bias these models and quantify the impact of de-biasing.


### Datasets and Pre-trained Models

#### Facebook Fasttext Models
https://fasttext.cc/docs/en/english-vectors.html <br>

Description: (as described on the fasttext website)
>The first line of the file contains the number of words in the vocabulary and the size of the vectors. Each line contains a word followed by its vectors, like in the default fastText text format. Each value is space separated. Words are ordered by descending frequency.

The pre-trained models listed in the link above are licensed under Creative Commons Attribution-Share-Alike License 3.0. https://creativecommons.org/licenses/by-sa/3.0/

#### Stanford GloVe Models
https://nlp.stanford.edu/projects/glove/

Description:
The data format for the text files is exactly the same as for FastText models listed above.

The pre-trained models listed in the link above are licensed under Public Domain Dedication and License v1.0. http://www.opendatacommons.org/licenses/pddl/1.0/.

#### De-biasing Algorithm
Github: https://github.com/tolga-b/debiaswe
Paper: Man is to Computer Programmer as Woman is to Homemaker? Debiasing Word Embeddings by Tolga Bolukbasi, Kai-Wei Chang, James Zou, Venkatesh Saligrama, and Adam Kalai. Proceedings of NIPS 2016.

Description:
This algorithm takes an existing pre-trained word embedding model (as a text file) and a seed list of words that are bias-specific. It then uses this seed list to generate a larger list of bias specific words. It also takes in a list of word pairs that specify the bias axis and then transforms the vector space so that all the bias-specific words and equidistant from the word paris defined the bias axis.

The code and the data in this repository are licensed under the MIT License.
https://github.com/tolga-b/debiaswe/blob/master/LICENSE

### Differences to prior work in this domain

There are several papers that analyse gender bias in word embeddings. This project was inspired by the papers and articles listed below.

Most of the existing work is focused on analysing bias (specifically gender) present directly in the model itself. In this project, I will attempt to use models trained on different text sources to understand the biases in the communities that have produced the data and answer questions like 'Are wikipedia's policies effective at making it's text more gender neutral?' and 'Is twitter more religiously biased compared to an average web page?'

Existing work on de-biasing also analyses only the gender bias. This project will attempt to extend that and validate if the de-biasing algorithms are effective in correcting for racial/religious biases. (Listed as possible future work in https://arxiv.org/pdf/1607.06520.pdf)

### Human-centered aspects of the project

The visualizations are expected to provide some insight to the various types of biases in different internet communities. These methods could possibly be used to validate/implement new policies aimed at reducing bias in sites like Wikipedia.

### Data/Model Limitations

Most of the prior work in word embedding bias use a binary gender model. The de-biasing algorithm that I plan to use also has this limitation.

### Research questions

1) How do web communities differ in their biases? Comparing Wikipedia, Twitter, Common Web Crawl w.r.t <br>
 a) gender bias (assuming a binary model) <br>
 b) religious bias <br>
 c) racial bias <br>

2) Does correcting the bias using the method described in the paper (https://arxiv.org/pdf/1607.06520.pdf) make all the communities have similar bias characteristics?

3) Quantifying the bias before and after correction according to the methods described in https://developers.googleblog.com/2018/04/text-embedding-models-contain-bias.html

### Data processing

Since the models I plan to use are pre-trained, this step would just require loading the binary formats and using the Gensim library to query the different embeddings for analogies.

### Tools

The visualizations and analysis will use Python and the following libraries: <br>
Gensim: Loading and querying GloVe word embeddings. <br>
Plot.ly, matplotlib: Visualizations. <br>
numpy, pandas: basic data processing. <br>
fastText: Loading facebook fasttext models <br>

### References

- Llorens, Marisa (2018) "Text Analytics Techniques in the Digital World: Word Embeddings and Bias," Irish Communication Review: Vol. 16: Iss. 1, Article 6.
doi:10.21427/D7TJ05
Available at: https://arrow.dit.ie/icr/vol16/iss1/6
- Demographic Word Embeddings for Racism Detection on Twitter, Mohammed Hasanuzzaman, Gae ̈l Dias, Andy Way: http://www.aclweb.org/anthology/I17-1093
- Quantifying and Reducing Stereotypes in Word Embeddings, Tolga Bolukbasi Kai-Wei Chang James Zou Venkatesh Saligrama Adam Kalai: https://pdfs.semanticscholar.org/2558/231cadaf0b1a4ac79d1a5c79322c8fbd327f.pdf
- Quantifying and Reducing Gender Stereotypes in Word Embeddings: https://drive.google.com/file/d/1IxIdmreH4qVYnx68QVkqCC9-_yyksoxR/view
- Man is to Computer Programmer as Woman is to Homemaker? Debiasing Word Embeddings:
Tolga Bolukbasi, Kai-Wei Chang, James Zou, Venkatesh Saligrama, Adam Kalai: http://papers.nips.cc/paper/6228-man-is-to-computer-programmer-as-woman-is-to-homemaker-debiasing-word-embeddings.pdf
- Jeffrey Pennington, Richard Socher, and Christopher D. Manning. 2014. GloVe: Global Vectors for Word Representation.
