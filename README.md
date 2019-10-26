### 个人觉得值得精读/反复读的一些文章

1.《BERT_Pre-training of Deep Bidirectional Transformers for Language Understanding》

2.《Attention Is All You Need》

3.《Summarization with Pointer-Generator Networks》

4.《Universal Model Fine-tuning for Text Classiﬁcation》

### Others

2.《Effective Neural Solution for Multi-Criteria Word Segmentation》

在每种分词方案后添加属于该分词方案的特殊标志符。虽然是2017年的文章，但是类似思想可以用在非常多的地方，在分词任务上的提升也是非常显著的。

1.《PAWS:Paraphrase Adversaries from Word Scrambling》

主要贡献：构建了一个非常有趣的数据集。数据集的特点：两个句子，word order不一样，但是word overlap非常高；标签为语义相同/不同。

用途：bert直接作用于这样的数据集，指标非常差；通过将该类数据添加到训练数据中，可以提升模型的robustness。能够很好的处理该类数据的模型，获取non-local contextual information的能力要强。此外，使用该数据，可以很好的度量模型对于word order和syntactic structure的sensitivity。

延伸思考：该数据集是平行语料，应该有其他可能的场景。

举例如下：

(1)Flights from New York to Florida.

(2)Flights to Florida from NYC.

(3)Flights from Florida to New York.

主要技术：Language Model(按照规则构建数据后，打分过滤)+Back Translation，最终构建类型如下：

![img__](https://wx4.sinaimg.cn/mw690/aba7d18bly1g813dh8n3oj21n40f2wix.jpg)


### GNN/GCN/GAN

2.《MASKGAN: BETTER TEXT GENERATION VIA FILLING IN THE_____》

微软的MASS感觉和这篇思路很是类似。

1.《Keep It Simple: Graph Autoencoders Without Graph Convolutional Networks》

### Dialogue System

2.《PLATO：Pre-trained Dialogue Generation Model with Discrete Latent Variable》

domain code是可控文本生成的一个好的策略，具体使用方式也比较灵活。这周实现的一个工作，也有应用。

《Mask and Infill：Applying Masked Language Model to Sentiment Transfer》

1.《End-to-end LSTM-based dialog control optimized with supervised and reinforcement learning》

这个是小蜜参考的另外一篇文章。整体上两篇文章时间都算是相对较早的。

0.《A Network-based End-to-End Trainable Task-oriented Dialogue System》

陈海青在2019年的云栖大会上分享中谈到的，小蜜用的一个工作，涉及一些RL的内容。

### GAN/VAE/RL

一些关于RL（**主要是policy gradient**）用于text generation任务的文章：

5.《A Deep Reinforced Model For Abstractive Summarization》

在RL的应用上感觉没有特别亮的点，类比之前的几篇工作。


4.《A Study of Reinforcement Learning for Neural Machine Translation》

将RL用于nmt任务（单语），和之前几篇整体上类似。文章给了一个经验性的结论：

**several previous tricks such as reward shaping and baseline reward does not make signiﬁcant difference。**

3.《Sequence Level Training With Recurrent Neural Networks》,第一篇将RL用于文本生成的文章

2.《Self-critical Sequence Training for Image Captioning》[参考笔记](https://zhuanlan.zhihu.com/p/58832418)

这篇文章差不多是基于3做了一点儿小的改进。

1.《Improved Image Captioning via Policy Gradient optimization of SPIDEr》

0.《Connecting Generative Adversarial Networks and Actor-Critic Methods》, Oriol Vinyals等

从MDP的角度解释了两个方法，gan中的生成器约等于ac中的actor，gan中的判别器约等于ac中的critic。同时梳理了一些**稳定**两种方法的训练trick。**从目前的一些观察来看，要想将rl用于自己的任务，先要保证收敛，其次再谈效果。具体的任务，比如文本生成相关。**

### 技术杂谈

1.[基于深度学习的自然语言处理，边界在哪里？](https://mp.weixin.qq.com/s?__biz=MzI4MDYzNzg4Mw==&mid=2247489825&idx=5&sn=026e9257fa25bb1af2a13cab0888138f&chksm=ebb421f5dcc3a8e33463b506de142bcd4b36628977f1d095191ff68c25ef6dcab30654fdbd94&mpshare=1&scene=23&srcid&sharer_sharetime=1567267555857&sharer_shareid=0e8353dcb5f53b85da8e0afe73a0021b%23rd)

亮点：文章中在解释问题时，对应的例子真的很棒。

总结：现在这种关于在特定任务领域的DL缺陷的讨论，各家基本说辞一致，倒也没什么新鲜感。但是说归说，自己能否真正理解可能就是另外一回事了。读这类文章，印证自己的观点可能是目的之一吧。对自己相对认同的一些观点整理一下：

（1）数据量较多场景下，DL具有优势；其他情况下，传统方法胜算更大。（补充一个：简单任务下，传统方法和DL差不多。）

（2）大家心心念念的中文分词技术已经不是机器翻译领域的关键问题了，而是成为了一种建模粒度的选择。（所以，面试官问有几种分词技术的时候就基本等同问茴香豆的茴有几种写法？额，已经不吃豆子了。也劳烦面试官同学们跟进技术发展，不要难为候选人了。当然，喜欢吃豆的候选人能有选择的吃了。）

（3）句法结构多数情况下也不是问题了。（最近比较痴迷把语言学的东西融合进bert，可能任务依赖吧，没有发现显著提升。包括一些bert的理论工作证明，模型是可以在一定程度上learn到句法结构的。）

（4）“机器翻译的成功是一个比较特殊的例子，这是因为它的**源语言和目标原因的语义都是精确对应**的，所以它只要有足够的数据而并不需要其他的支撑，就能取得较好的效果。现在的自然语言处理系统大部分，还只是流于对词语符号之间的关系建模，没有对所描述的问题语义进行建模，即对客观世界建模。而人理解语言的时候，脑子里一定会形成一个客观世界的影像，并在理解影像后再用自己的语言去描述自己想说的事情。 ”（本质的讨论：现有模型学到的是啥？syntactic和semantic如何界定？我们实际需要的是semantic哦）

### Pre-trained 

6.《DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter》

主要贡献：通过蒸馏的方式，获取一个更小，inference速度更快，performance损失极少的bert。

主要方法：teacher网络就是原始较大的bert，student网络是较小的bert。损失函数=L(masked lm)+**L(cross entroy based-on soft targets)** + L(cosine distance based-on hidden representation)三个部分组成。

个人想法：

（1）student网络设计

student网络设计理论上应该比较灵活。比如选择一个三层的Transformer的Encoder端，一个一层的BiLSTM，甚至CNN系网络。对于第一种，假设用原始较大的bert中的一些层的参数做初始化，则可以认为是一个小的bert，这和文章中的做法是一致的。当然也可以选择初始化，比如对于第二种和第三种，类似工作后来在文章《Distilling Task-Specific Knowledge from BERT into Simple Neural Networks》中有看到，直觉上初始化方式和网络结构是强相关的。对于第一种，天然适合用原始bert的参数做初始化，那么对于第二种，第三种能否做参数共享值得思考。实际上，初始化方式对于蒸馏比较重要。

此外，能否直接在原始较大bert上实现类似student网络的功能也值得思考，因为这样就不需要重新去train一个新的网络，这就和bert在fine-tuning时的freeze layer/lr schedule等相关Trick相关了。

（2）损失函数设计

实际上，损失函数的设计不限于文章中所说的，本质上是如何建立teacher和student的logits之间的关系，让二者尽可能接近。比如本文的ce和（1）中提到文章的mse等。除此之外，regularization的探讨也是一个很自然的想法。

（3）蒸馏任务设计

文章的蒸馏任务是Masked LM，仍旧需要在下游任务上做fine-tuning，（1）中提到的是直接用下游任务来蒸馏。当考虑pretrained+fine-tuning的时候，蒸馏任务的设计就会比较灵活。

5.《Unified Language Model Pre-training for Natural Language Understanding and Generation》

多种预训练模式的大杂烩。如下：

![multi-pretrained-method](https://wx2.sinaimg.cn/mw690/aba7d18bly1g7oy2a23mwj212x0u0ng8.jpg)

4.《Enriching BERT with Knowledge Graph Embeddings for Document Classiﬁcation》

motivation：present a way of enriching BERT with knowledge graph embeddings（PyTorch BigGraph） and additional metadata.
任务：book classification
架构：类似于deep&wide

3.《CTRL: A CONDITIONAL TRANSFORMER LANGUAGE MODEL FOR CONTROLLABLE GENERATION》

主要贡献：

（1）带有条件的语言模型。其实，仔细看gpt的相关文章的话，已经在gpt中出现了，作者又发扬光大了。

16亿参数的语言模型，比起nvidia的80亿参数的模型较小，不过仍旧是较大的语言模型了。训练语言模型的文本如下：

Horror Text: I was a little girl when my parents got divorced. My dad had been in the military for years and he left me with my mom. She worked as an RN at a hospital so she could take care of me.\n\n When we moved to our new house it took some time before things settled down. We were still living together but there wasn’t much going on. It didn’t help that my mom would get mad if someone came over or even just walked by her house.\n\n One day while walking through the yard I noticed something out of place...

这里，Horror Text:就是条件了。

（2）penality sampling。类似于coverage机制，decoder不搞一些新的sampling策略，就感觉缺点啥；类似于不在loss上搞点事情，就觉得工作不够高大上。

（3）一个有很多参数的语言模型。16亿。

总结：散了，散了，你们玩儿吧。


2.《Pre-Training with Whole Word Masking for Chinese BERT》

BERT-wwm的工作，中文版。

motivation：wordpiece分词会导致将一个完整的词分成几个子词， 原始的bert在mask的时候会mask掉子词，但是从语义角度，更好的mask方式应该是mask一个完整的词（对比，个人持保留意见）。

solution：解决方法相对简单，就是如果发现一个词中某个子词被mask了，就全部mask掉该词对应的所有子词。

工作扩展：在给bert添加语言学信号的时候，例如pos/依存分析/srl的信号，最好考虑wordpiece分词后的对齐问题。

1.《A Robustly Optimized BERT Pretraining Approach》

facebook的工作，bert是undertrained的，并对bert重新训练的细节做了思考。

### EMNLP2019论文选读（浏览了一些自己感兴趣方向的文章）

总结：EMNLP的文章读起来八股气息要弱一些，文章类型更加丰富，个人觉得是好现象。不过收一些个人感觉明显质量有问题的工作也是有点奇怪。下述文章只是看题目觉得可看，就大致浏览了一下。

1.《Text Summarization with Pretrained Encoders》

思路：用bert去fine-tune句子级的embedding，然后对sentence做binary classification(要不要？)。实际上，直接对token做binary classification未尝不可，不过相比前者，semantic的粒度确实小了很多。一如很多工作，这次bert后不加bilstm，不加crf，加self-attention层了。额，可以一直加，但是不要搞得像CV的一些工作就行。比较有启发的是，如何构造输入进行sent embedding的学习。bert不是只可以一个[CLS]和两个[SEP]吧。

2.《Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks》

思路：当输入两个句子直接进bert得到sent embedding的问题在于，当句子比较长的时候就有点尴尬了。一个比较直接的思路是，每个bert喂一个sent，用两个bert做embedding，然后加融合层，比如cosine之类的操作等，整体上是siamese的结构。除此之外，文章也提出了triplet loss的应用。嗯，整体上的工作和人脸领域的一类工作很类似了。

3.《Neural Text Summarization: A Critical Evaluation》

个人较喜欢的一个工作，相对务虚，不过指出的问题需要思考。文章认为：**整体上神经关系抽取近期的工作基本处于停滞状态。**比如，有些数据集上，SOTA只比直接从文章中抽取前三句话好一点点。原因有三个方面：（1）数据集的问题。某些数据集只给定一篇文章+一个参考摘要，除此之外，没啥额外的信息了。真实场景下可不是这样的哦。也就是说，现在的数据集构造还是离真实场景有点远。（2）评估指标的问题。已经是生成式模型的老问题了，除了大家知道的一些弊端，还有对**事实性错误的评估**。（3）模型到底学到的是个啥？

4.《Attending to Future Tokens for Bidirectional Sequence Generation》

思路：用bert做序列生成。输入源句子+目标句子用于训练，其中目标句子随机选一些token用placeholder替换。扩展一下，关于bert用于生成，最近印象中有一些工作。第一：类似于本文的思路。第二：seq2seq中将bert作为encoder，decoder单独训练(模型可以灵活选择)。第三：decoder端用bert。第四：更加广义地应用，比如做extractive摘要的工作。

5.《Dynamic Past and Future for Neural Machine Translation》

思路：用于Capsule Network做机器翻译。

6.《Learning to Recognize Discontiguous Entities》

解决的问题：命名实体识别中，识别不连续的实体。

7.《ner and pos when nothing is capitalized》

解决的问题：在NER和POS任务中，**大小写很重要。**

8.《On NMT Search Errors and Model Errors: Cat Got Your Tongue?》

解决的问题：组合beam search和depth-first search做精确推断用于NMT任务。作者在文末明确指出：该方法不实用，但是可以帮助理解现有一些NMT的Trick可能并不能完全解决一些特定的问题。

### BERT


8.《Universal Text Representation from BERT: An Empirical Study》

讨论了各种Bert抽Sentence Embedding的方法，比较系统。

7.《ALBERT：A Lite BERT For Self-Supervised Learning Of Language Representations》，iclr2020投稿

结论：参数更少，效果更好的bert变种。

主要工作：

（1）降低embedding的dim，O(vxh)->O(vxe+exh) where h>>e（隐含条件v>>e），是一个较简单且松弛的不等式问题；

（2）跨层参数共享。类RNN，将layer视为building block。作者也尝试了共享ffn和共享attention

（3）sop任务。原来的nsp是鸡肋，因为有信号泄漏，实际上模型可能没有学到多少coherent信息，而是泄漏的topic信息；这里重新设计了一个任务：
给定一篇doc中的两个句子a和b，其中a和b按照doc中的顺序出现，则a+b=1；b+a=0。这样可以push模型学到coherent信息而不是topic信息。

评价：总体上看没有骚操作，不过工作做的很是干净，效果也很不错。

6.5和4的相关paper，《Enriching BERT with Knowledge Graph Embeddings for Document Classiﬁcation》，德国

5.《ERNIE: Enhanced Representation through Knowledge Integration》，百度

4.《ERNIE: Enhanced Language Representation with Informative Entities》，清华

3.《Revealing the Dark Secrets of BERT》

model pruning and finding an optimal sub-architecture reducing data repetition;

主要方法：对attention weight 进行可视化

主要的想法：disabling self-attention heads（应该是一个比较普遍的结论）

2.《Universal Language Model Fine-tuning for Text Classification》

**非常好的工作，相信可以对更好地利用bert做fine-tuning有很好的启发。**

主要思路(对ULMFiT的使用包含三个阶段， 基于3层lstm)：

(1) LM pre-training

(2) LM fine-tuning（不同层用不同的学习率，2.6倍差异）

(3) Classifier fine-tuning（gradual unfreezing，每个epoch都只unfreeze掉一部分layer）

现在多数情况下，大家对于bert用于fine-tune的过程通常是没有第二个阶段的。


1.《Visualizing and Understanding the Effectiveness of BERT》，**2019.08.15**

主要思路：可视化loss landscape和optimization trajectories

主要结论：

（1）pre-training可以到达一个好的优化初始化点，使得下游任务的训练到达wider optima和easier optimization；另一方面虽然bert是over-parameterized的，但是robust to overfitting。

（2）fine-tuning可以获得更好的泛化性能（flat and wide optima），同时可以观察到traning loss surface和generalization errro的一致性；

（3）bert的低层在fine-tuning的过程中more invariant，这意味着学习到了more transferable representation of language。

关于第三点的具体展开：《BERT Rediscovers the classical NLP pipeline》

lower layers: most local syntactic phenomena

higher layers: more complex semantics


主要建议：

**开发一些好的fine-tuning的算法，使得能够使下游任务的最优点收敛到一个wider and more flat optima。**

### Classification

5.《Hierarchical Relation Extraction with Coarse-to-Fine Grained Attention》

motivation：关系是有层次的。hierarchical modeling几乎是一个很直接的idea。

4.《How to Fine-Tune BERT for Text Classiﬁcation?》

黄老师组的文章，名字有点俗，但是内容脱俗。讨论了如何去fine-tuning bert用于文本分类任务。文章中提到一些有意思的想法，值得尝试一下。ULMFit的工作也值得对比着看。个人觉得关于bert的工作，我们的认识还是很浅的，需要持续的研究和探讨。什么任务就bert一把梭的想法有点扯。

3.《Learning Named Entity Tagger using Domain-Specific Dictionary》

用于ner任务，两个方法。这篇文章和**AutoPhrase**（**语料库+wikipedia+pos，整体上偏规则方法**）的作者基本相同。

第一：fuzzy crf。利用crf挖掘multi-label的信息；

第二：AutoNer。新的标注范式，用两个token是否连接来标注。大概思路如下：

输入一句话：艾耕科技由高榕投资。

构造数据如下：

[S] 艾 1
 
 艾 耕 1
 
 耕 科 1
 
 科 技 1
 
 技 由 0
 
 由 高 0
 
 高 榕 1
 
 榕 投 0
 
 投 资 0
 
 资 [E] 0
 
 [E] 。 0
 
 剩下的事情就是labeling了。



2.《BERT for Joint Intent Classification and Slot Filling》

个人非常喜欢的思路。

intent classification：给一句话打标签，多分类，必要时multi-label；比如一句话“艾耕科技由高榕投资。”，类别标签是：**是否是融资新闻？**

slot filling：slot对应字段，比如**融资机构，投资机构**等，filling是找到对应字段类型的值，比如**艾耕科技，高榕**等。

思路：[CLS]做intent classification；slot filling用sequence labeling做；

思路扩展：

（1）两个模型。一个做分类，一个做labeling；

（2）一个模型做，但是两个任务是异步的；

（3）multi-task

（4）就是上面的思路了，同步做；

目标函数是最大化条件概率：p(y(i), y(s)|x) ，其中y(i)是intent的label的softmax分布，y(s)是slot的label的softmax分布（有多个slot）。本质上等价于cross\_entropy的最小化，同为分类问题。


1.《A Simple and Effective Approach for Fine-Tuning Pre-trained Word Embeddings for Imporved Text Classification》

一个分类的Trick：在对word embedding进行fine-tuning的时候，每个example添加类别的信息。fine-tuning的model是doc2vec。

0.《Bag of Tricks for Efﬁcient Text Classiﬁcation》

fastText的工作。

（a）

Q:linear classiﬁers do not share parameters among features and classes. This possibly limits their generalization in the con- text of large output space where some classes have very few examples.

A:low rank matrices, multi layer neural networks

（b）**bow对word order不敏感，需要显式的考虑order，因此有了bag of n-grams，不过仍旧是只考虑了local order。**

（c）两个实现上的技巧：hierarchical softmax， n-grams的hash trick

### Learning to Rank

#### 1.RankNet，《Learning to rank using gradient descent》,ICML2005

主要目的：学习一个Ranking Function

训练：给定一个doc list，构建example = (doc1，doc2)。如果doc1和query更相关，则label=1；否则label = 0。

测试：给定一个doc list，通过构建pair list，得到label list，最后可以得到一个ranking结果。

#### 2.LambdaRank, 《Learning to Rank with Nonsmooth Cost Functions》,NIPS2006

主要目的：损失函数中添加对排序指标的优化项。

#### 3.LambdaMART

Lambda+MART(GBDT,梯度提升树)

#### 4.ListNet,《Learning to Rank: From Pairwise Approach to Listwise Approach》

上述三篇都是input为pair的方法，这篇工作是input为list的方法。一般认为效果上，后者要优于前者。

相关资源：

1.[PTL2R](https://github.com/ptl2r/ptl2r.github.io)

基于PyTorch，实现了多种排序学习的算法。

2.[RankNet的实现](https://github.com/ShaoQiBNU/RankNet)

### Knowledge Graph

3.ACL2018,《Improving Entity Linking by Modeling Latent Relations between Mentions》

**goal:** link each mention to an entity in a KB.

**candidate selection:** local and global modeing


2.《OAG: Toward Linking Large-scale Heterogeneous Entity Graphs》,KDD2019


1.《Entity Alignment between Knowledge Graphs Using Attribute Embeddings》,AAAI2019


### others

6.《data decisions and theoretical implications when adversarially learning fair representations》

主要贡献: we use an adversarial training procedure to remove information about the sensitive attribute from the latent representation learned by a neural network.

![img](http://wx1.sinaimg.cn/mw690/aba7d18bgy1g2o8funikij20j40dwgmo.jpg)

5.《the sample complexity of pattern classification with neural networks: the size of the weights is more important than the size of the network》,1999年trans on information theory的一篇文章

**Results in this paper show that if a large neural network is used for a pattern classiﬁcation problem and the learning algorithm ﬁnds a network with small weights that has small squared error on the training patterns, then the generalization performance depends on the size of the weights rather than the number of weights.**

相关论文，《Real numbers, data science and chaos: How to ﬁt any dataset with a single parameter》


4.《reducing multiclass to binary：a unifying approach for margin classifiers》

**传统方法：**

（1）each class is compared against all others

（2）all pairs of classes are compared to each other

(3) output codes with error-correcting properties are used, [文献](http://www.ccs.neu.edu/home/vip/teach/MLcourse/4_boosting/lecture_notes/ecoc/ecoc.pdf)，周志华老师的书上也有介绍，不过更常见的多是前两种。

3.《classifying relations by ranking with convolutional neural networks》

**主要贡献：**

（1）提出了一个新的pairwise rank loss用于减少人工类的影响。（我们之前也有一个工作将改进的pairwise rank loss用于图片质量评价）

（2）提供了一个证据：cnn+rank loss > cnn+softmax

（3）在关系分类任务中，如果仅仅考虑两个nominal之间的text，使用word embedding就可以sota

周博文挂名的文章看的几篇都是思路比较清晰的，方法上虽然看起来不太复杂，但是work。同时，有必要关注一下，logistic loss， rank loss， margin loss等在nlp领域中的应用，不一定logistic loss去dominate所有的情况，印象中cv的某些任务上，margin就表现的比较好。rank loss印象中在ir上应用较广，但是loss之间并非绝对的独立，对他们之间关系的思考也是一个有趣的方向，估计已经有一些工作了。


2.《dropout training as adaptive regularization》,percy liang等人的文章

主要贡献：对于glm，dropout可以认为是一种自适应正则化的技术，同时建立了与adagrad的联系。在dropout，regularization和adagrad的联系基础上，提出了一个semi-supervised算法，该算法使用没有标签的数据可以建立一个更好的自适应的regularizer。

we show that the dropout regularizer is first-order equivalent so an L2 regularizer applied after scaling

the features by an estimate of the inverse diagonal Fisher information matrix.

1.《Using Pre-Training Can Improve Model Robustness and Uncertainty》

Through extensive experiments on **label corruption, class imbalance, adversarial examples, out-of-distribution detection, and conﬁdence calibration**, we demonstrate large gains from pre-training and complementary effects with task-speciﬁc methods.

### Language Model

5.《Mask and Infill: Applying Masked Language Model to Sentiment Transfer》,IJCAI 2019

主要贡献：non-parallel下的style transfer(情感)的SOTA

具体工作：两个阶段，第一个阶段为Mask，也就是给定一句话，把情感词Mask掉。第二个阶段为Infill。分为两个过程，分别是重构和判别。重构的含义是给定被Mask情感词的句子和目标情感，用Mask LM做被Mask词的填充预测。判别的含义是用一个预先训练好的分类器判断情感是否正确。

个人想法：

（1）指标问题：BLEU值每增加一个单位，ACC显著的掉点。当BLEU为SOTA的时候，ACC非常差；当ACC为SOTA的时候，BLEU也为SOTA，这意味着既能做content preserving，又能实现style transfer；显然，前者BLEU的SOTA值高于后者。前者没有意义，因为假设不对句子做任何的修改，BLEU也将为SOTA；

相关文献：《Unsupervised Text Style Transfer using Language Models as Discriminators》

4.《On Extractive and Abstractive Neural Document Summarization with Transformer Language Models》

用LM的方法做摘要，其实类似思路在GPT系列已经体现。例如做翻译，用"="来连接两个语种的句子；例如摘要，用"TL;DR;"的符号来连接等。另外，这里存在一个术语上可能会混淆的地方，一般说Transformer是指seq2seq，包含一个encoder和decoder，实际上这里只是使用一个decoder，标准的lm。

3.《The Curious Case of Neural Text Degeneration》

motivation：机器生成的语言的prob分布（锯齿状且更加平稳）和人生成的语言的prob分布是不一致的；

solution：一种decoder端的策略。

2.《Using the Output Embedding to Improve Language Models》

weight typing技术。lm的input和output embedding共享。

优点：减少模型容量到一半；正则化；

印象中多个lm的实现都支持相同做法。

 1.《think again network, the delta loss, and an application in language modeling》
 
 lm在penn treebank上的新的sota，通过在rnn的hidden输出上再添加一层recurrent机制，使得性能提升；同时提出了一个新的损失函数，但是实验上并没有提升；虽然实现了新的sota，但是个人认为模型会相对较大，需要保留较多的历史信息。


### NLG

17.《Fine-tune BERT for Extractive Summarization》

16.《HIBERT：Document Level Pre-training of Hierarchical Bidirectional Transformers for Document Summarization》

两种基于BERT做extractive summarization的工作；第16需要处理hierarchical的doc。

15.《Learning to Encode Text as Human-Readable Summaries using Generative Adversarial Networks》

类似玩法印象中有几篇。

![img_](https://wx2.sinaimg.cn/mw690/aba7d18bly1g7prsoh823j20ow0af766.jpg)

14.《Unsupervised Text Summarization Using Sentence Embeddings》

无监督方式做文本摘要，两种方式：

抽取式：句子做cluster，选择cluster中心的句子作为摘要，不流畅。（流畅应该是摘要的评估指标之一吗？）

生成式：句子做cluster，选择cluster中心的embedding，作为一个decoder的输入。

既然是sentence embedding，这里ICLR2017有一篇讨论了sentence embedding的方法，《A Simple But Tough-to-Beat Baseline For Sentence Embeddings》，除此之外，讨论更好的embedding的文章不要太多。

13.《BERTSCORE : EVALUATING TEXT GENERATION WITH BERT》

我们组也正在做的工作。文章的一个特色是40+页，大量都是实验。思路比较简单，如下：

![img](https://wx2.sinaimg.cn/mw690/aba7d18bly1g7pqsofpv9j217z0f2gro.jpg)

准备用在无监督的文本摘要任务上。

12.《LARGE-SCALE PRETRAINING FOR NEURAL MACHINE TRANSLATION WITH TENS OF B ILLIONS OF SENTENCE PAIRS》，ICLR2020，under review

我们组也正在做的工作，偏实践。今年关于用非常大的规模的语料训练nmt系统的工作印象中已经有好几篇了。这篇文章大概40billion的平行pair，BLEU+3.2。

整体上的流程是：预训练+fine-tuning，标准玩法。因此，要解决的主要是工程上的问题，关于两个基本问题：大规模的数据难免包含一些noise；很长的训练时间。为此，这篇文章尝试了以下四类方法：

（1）一个单模型直接训练；

（2）把数据平均分成K份，训练K个模型，概率层做K等权值融合；

（3）把数据按照topic分成K份，训练K个模型，先分类，再训练；topic的划分基于LDA；

（4）上述三种都是在train前数据集都是static的，实际上dynamic理论上更好一些。也就是说，一个example可以在train的过程中，被dynamic的分给任意一个模型。技术上采用hard-EM的思想，使用batched-EM，将latent variable的计算（分给哪个模型）转化为一个整数线性规划问题，用Hill Climbing解决。batched-EM也是神经mixture模型相关工作的一个经典方法。

（5）我们自己做的工作是直接cluster；通过t-sne可以看到cluster是make sense的；


11.《BottleSum: Unsupervised and Self-supervised Sentence Summarization using the Information Bottleneck Principle》

10.《Neural Text DeGeneration With Unlikelihood Training》

指出了传统decoder端的一些策略的问题（top-k/nucleus sampling/beam blocking etc.），通过修改损失函数作为文章的contribution。

9.工业Track的一些文章

(1)《OpenTag: Open Attribute Value Extraction from Product Profiles》，KDD2018

(2)《Scaling Up Open Tagging from Tens to Thousands: Comprehension Empowered Attribute Value Extraction from Product Title》，ACL2019

(3)《A Multi-task Learning Approach for Improving Product Title Compression with User Search Log Data》，AAAI2018

(4)《Multi-Source Pointer Network for Product Title Summarization》，CIKM2018

上述四篇都是工业Track的文章（阿里），（1）和（2）解决从商品标题中抽取商品属性值的问题。（3）和（4）采用seq2seq，输入商品长标题，输出商品短标题，并保证尽可能商品短标题中的词是关键词。

（1）采用sequence labeling的思路，模型上的一个尝试是在经典的BiLSTM+CRF之间添加了Attention层。但是（1）的问题是：商品属性数量众多，导致分类空间巨大。

（2）采用MRC的架构，将商品标题和属性作为输入，三类标签作为输出(BIO)。相比于（1），（2）将问题进行了分解，大大减小了分类空间，同时在属性支持上更加灵活。文章认为，当新属性出现时，使用已经训练好的模型仍旧可以提取到属性值，因为MRC架构已经学习到了属性和商品标题的语义分布。个人对此持怀疑态度，待王磊实验反馈。

（3）一个Encoder的输入是商品长标题，两个Decoder分别编码对应的商品短标题和商品长标题对应的用户搜索Query。训练时，保证二者的Attention分布尽可能一致；预测时，只使用一个Decoder。整体上是一个multi-task任务，共享Encoder端。训练一个Query端的Decoder有一定的启发性。

（4）两个Encoder，分别编码商品长标题和与该商品相关的知识信息(可以扩展为知识图谱)，一个Decoder端用于生成商品短标题。同时训练一个分类器，判断使用哪个Encoder，或者说生成的关键词来自哪个数据源，这其实是一种hard的copy机制使用，并且不使用vocab的信息，区别于传统的soft的copy机制，同时用到attention和vocab的分布信息。整体上的思路比较naive，不过将知识图谱引入有一定的启发性。

8.《Mask-Predict_Parallel Decoding of Conditional Masked Language Models》

7.《FlowSeq: Non-Autoregressive Conditional Sequence Generation with Generative Flow》

7和8都是近期关于Non-Autoregressive的工作，7的价值似乎更大一些。但是征哥认为：**该工作是CVAE的一个变种而已**。

6.《MASS: Masked Sequence to Sequence Pre-training for Language Generation》

motivation：近期来主要的工作围绕pretrained language model，比如经典的bert系列（transformer的encoder）和gpt系列（transformer的decoder），那既然这样，为啥不能两个都pretrained呢（seq2seq）？为了pretrain这个seq2seq，按照传统思路，自然需要大量的平行语料，但是如果这个条件现实，可能已经不需要这个工作了。所以，一种方式是类似自编码的思路，input和output的句子相同。如果真是这样，就没啥意思了。所以，本文采用的思路是：input端挖掉一些片段，然后output端预测这些片段。

优点：强迫input端做好理解的事情；强迫output端能够在生成的时候更加依赖input端的表示，而不是上一个预测输出的token；

做法：pre-trained seq2seq + fine-tuning下游任务

扩展：这种思路可以用于基于生成的完形填空吧。

**trick（soft contextual data augmentation）**：为了获得更多更多的训练语料，可以基于挖空的句子语料训练一个lm，然后让lm去预测空位对应的词，选择topk，填入到空位。这样就形成了多个平行语料对。

5.《Comparison of Diverse Decoding Methods from Conditional Language Models》

梳理了围绕beam search改进的各种方法，可以在不损失quality的同时，增加diversity。

4.《A Simple Theoretical Model of Importance for Summarization》

几个用于评估摘要的指标：**Redundancy**, **Relevance**, and **Informativeness**.

3.《Towards Knowledge-Based Personalized Product Description Generation in E-commerce》，kdd2019

主要贡献：基于seq2seq（transformer），融合用户属性，商品属性和知识图谱，生成个性化的商品描述。

2.《challenging common assumptions in the unsupervised learning of disentangled representation》

主要内容：如题

主要特色：用大量的实验来challenge一个common assumption，主要讨论的是vae相关变种模型。

想法：对vae和gan以及正则化流相关的工作没有做过深入思考，因此这篇文章自认为并不是读的特别明白，后续有相关工作了需要进一步思考。

1.《Unifying Human and Statistical Evaluation for Natural Language Generation》NAACL2019

motivation:

(1)quality: 人类评估可以评估质量，但是无法评估diversity；bleu&rouge在评估quality方面做的比ppl好，但是还是比human弱，同时在评估diversity方面也是很弱。

(2)diversity： ppl可以评估，但是无法评估quality；

(3)一个unified framework：（最优错误率）预测一个sent来自human还是machine

问题：如何证明huse（human unified with statistical evaluation）是work的？

结论：huse=quality+diversity

2.[Are generative models good enough?](https://blog.singularitynet.io/are-generative-models-good-enough-a-case-study-on-class-modeling-9a57c91ddcae)

用**一个简单的例子**讲了几个generative模型的问题，包括生成模型和判别模型的区别和联系；vae/gan等；

### Transformer

4.《Accelerating Neural Transformer via an **Average Attention Network**》

Transformer在decoder端的加速工作，通过加层的方式实现。比起直接将auto-regressive的方式转化为nonauto-regressive的方式，这种方式还是相对廉价的。 

3.《Attention is all you need》,nips2017

从整体上看，transformer的encoder端就是一堆linear层的堆叠，添加**norm layer和dropout**，在最后的pooling层添加了tanh的activation函数；

思想：完全依赖attention机制获取input和output端的全局依赖。

end-to-end memory networks are based on a **recurrent attention mechanism** instead of **sequence-aligned recurrence**. Transformer is the first transduction model relying entirely on self-attention to compute representations of its input and output without using sequence-aligned RNNs or convolution.

Encoder: LayerNorm（x+SubLayer(x)）；

Decoder: 是三个子层，self-attention需要添加mask；

问题：

（1）transformer中，scaled dot-production attention可以用additive attention代替吗？能和不能的原因是什么？

（2）attention(q,k,v)=softmax(qk^t/sqrt(d_k))v中，为啥需要这个**scaling factor**？

（3）为什么self-attention是可以work的？或者说self-attention的优点是什么？

a.computational complexity per layer

b.amount of computation that can be parallelized(measured by the minimum number of sequential operations required)

(个人认为可以并行优化的地方：第一：分别计算q，k，v的时候；第二，multi-head scaled dot-product attention)

c.the path length for long-range dependencies(from one position to another position)

d.interpretable(syntactic and semantic)

（4）transformer中使用的regularization技术有哪些？

a. apply dropout to the output of each sub-layer

b. apply dropout to the sums of the embeddings and positional encodings in both the encoder and decoder stacks

c. label smooothing: this hurts perplexity, as the model learns to be more unsure, but improves accuracy and BLEU score.



2.《SpanBERT: Improving Pre-training by Representing and Predicting Spans》

contribution：

（1）masking contiguous random spans, rather than random tokens

（2）training the span boundary representations, encourage the model to store this span-level information at the boundary token.

一张图解释：

![img](http://wx3.sinaimg.cn/mw690/aba7d18bgy1g5d25mjbdqj214y0gwacy.jpg)

个人想法：类似工作很多了，印象中今年MSRA在wmt2019取的好多第一的工作《MASS: Masked Sequence to Sequence Pre-training for Language Generation》ICML2019;

百度的[ERNIE](https://github.com/PaddlePaddle/ERNIE)的工作；

我的博客[神经关系抽取](https://zhpmatrix.github.io/2019/06/30/neural-relation-extraction/)中的一些工作；

我们组在生成方面的一些尝试等。

总之，个人对类似工作已经提不起兴趣了。

1.《Training Tips for The Transformer Model》基于英语-捷克语的语料，用transformer做翻译模型。使用tensor2tensor框架，对任务中的各个参数进行了实验探索。

总结如下：

#### （1）checkpoint averaging：几乎总是有稳定的提升。

#### （2）resumed training：
