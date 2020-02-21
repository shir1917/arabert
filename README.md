# AraBERT : Pre-training BERT for Arabic Language Understanding

**AraBERT** is an Arabic pretrained lanaguage model based on [Google's BERT architechture](https://github.com/google-research/bert). AraBERT uses the same BERT-Base config.

There are two version off the model AraBERTv0.1 and AraBERTv1, with the difference being that AraBERTv1 uses pre-segmented text where prefixes and suffixes were splitted using the [Farasa Segmenter](http://alt.qcri.org/farasa/segmenter.html).

The model was trained on ~70M sentences or ~23GB of Arabic text with ~3B words. The training corpora are a collection of publically available large scale raw arabic text ([Arabic Wikidumps](https://archive.org/details/arwiki-20190201), [The 1.5B words Arabic Corpus](https://www.semanticscholar.org/paper/1.5-billion-words-Arabic-Corpus-El-Khair/f3eeef4afb81223df96575adadf808fe7fe440b4), [The OSIAN Corpus](https://www.aclweb.org/anthology/W19-4619), Assafir news articles, and 4 other manually crawled news websites (Al-Akhbar, Annahar, AL-Ahram, AL-Wafd) from [the Wayback Machine](http://web.archive.org/))

We evalaute both AraBERT models on different downstream tasks and compare it to [mBERT]((https://github.com/google-research/bert/blob/master/multilingual.md)), and other state of the art models (*To the extent of our knowledge*). The Tasks were Sentiment Analysis on 6 different datasets ([HARD](https://github.com/elnagara/HARD-Arabic-Dataset), [ASTD-Balanced](https://www.aclweb.org/anthology/D15-1299), [ArsenTD-Lev](https://staff.aub.edu.lb/~we07/Publications/ArSentD-LEV_Sentiment_Corpus.pdf), [LABR](https://github.com/mohamedadaly/LABR), [ArSaS](http://lrec-conf.org/workshops/lrec2018/W30/pdf/22_W30.pdf)), Named Entity Recognition with the [ANERcorp](http://curtis.ml.cmu.edu/w/courses/index.php/ANERcorp), and Arabic Question Answering on [Arabic-SQuAD and ARCD](https://github.com/husseinmozannar/SOQAL)

## Results
Task | prev. SOTA | mBERT | AraBERTv0.1 | AraBERTv1
---|:---:|:---:|:---:|:---:
HARD |95.7 [ElJundi et.al.](https://www.aclweb.org/anthology/W19-4608/)|95.7|96.2|96.1
ASTD |86.5 [ElJundi et.al.](https://www.aclweb.org/anthology/W19-4608/)| 80.1|92.2|92.6
ArsenTD-Lev|52.4 [ElJundi et.al.](https://www.aclweb.org/anthology/W19-4608/)|51|58.9|59.4
AJGT|93 (citation needed)| 83.6|94.1|93.8
LABR||83||86.7
ArSaS|
ANERcorp||78.4|84.2|81.9
ARCD|-|EM:34.2 F1: 61.3||EM:30.6 F1: 62.7

*We would be extremly thankful if everyone can contibute to the Results table by adding more scores on different datasets*

## How to use

You can easily use AraBERT since it is almost fully compatible with existing codebases (You can use this repo instead of the official BERT one, the only difference is in the ```tokenization.py``` file where we modify the _is_punctuation function to make it compatible with the "+" symbol and the "[" and "]" characters)
**To use the [Transformers](https://github.com/huggingface/transformers) Library you can use [this FORK](https://github.com/WissamAntoun/transformers)** 
**If you have a more elegant solution please contact us**

The ```araBERT_(initial_Demo_TF)_.ipynb``` Notebook is a small demo using the AJGT dataset using TensorFlow (GPU and TPU compatible).

The ```araBERT_(initial_Demo_Transformers)_.ipynb``` Notebook is another demo using the AJGT dataset using Transformers from HuggingFace (GPU and TPU compatible).

## Model Weights and Vocab Download
Models | AraBERTv0.1 | AraBERTv1
---|:---:|:---:
TensorFlow|Coming SOON | [Drive Link](https://drive.google.com/drive/folders/1GQr8ue04rsvkOO3GieYTWnCOmB3-CNJz?usp=drive_open)
PyTorch| Coming SOON | Coming SOON

*You can find the PyTorch models in HuggingFace's Transformer Library under the ```aubmind``` username (SOON)*

## If you used this model please cite us as:
```
@comingsoon{just couldnt get the paper finished on time XD}
```
## Acknowledgments 
Thanks to TensorFlow Research Cloud (TFRC) for the free access to Cloud TPUs, couldn't have done it without this program, and to the [AUB MIND Lab](https://sites.aub.edu.lb/mindlab/) Members for the continous support. Also thanks to [Yakshof](https://www.yakshof.com/#/) and Assafir for data and storage access.

## Contacts
**Wissam Antoun**: [Linkedin](https://www.linkedin.com/in/giulio-ravasio-3a81a9110/) | [Twitter](https://twitter.com/wissam_antoun) | [Github](https://github.com/WissamAntoun) | <wfa07@mail.aub.edu> | <wissam.antoun@gmail.com>

**Fady Baly**: [Linkedin](https://www.linkedin.com/in/fadybaly/) | [Twitter](https://twitter.com/BalyFady) | [Github](https://github.com/fadybaly) | <fgb06@mail.aub.edu> | <baly.fady@gmail.com>

***We are looking for sponsors to train BERT-Large and other Transformer models, the sponsor only needs to cover to data storage and compute cost of the generating the pretraining data***