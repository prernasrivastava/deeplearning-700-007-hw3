## Deep Learning 700-007 HW3

We have training a seq2seq model on twitter data set. The data set was in the format of tweet/reply. We kept a vocabulary size of 40,000 for both questions and responses.
We created an alexa skill call ps_twitter_chat_model for interaction with alexa. The invocation name for the skill is "twitter chat".
The code for the skill is written in alexaskill.py.

The training set size ws taken as: 301812
The test set size was taked as: 75453

Evaluation:
The following are a few qualitative examples:

>how are you?
i am fine . how are you ?

>what do you think about president trump?
he ' s a b####

>what makes you think you are funny
a lot of people all the time

>what do you about hilary clinton?
she ' s on the list

>what list are you talking about?
i ' m not sure what you mean lol

>you are not making any sense
i ' m sorry for this

>what do you like?
i ' m not even talking about it now

A few mistakes:
>do you have any plans for dinner?
here has lots of other drinks and food

>what are plans for tonight?
who are you hitting for ?

>do you have any plans for dinner?
here has lots of other drinks and food

>do you like republicans?
. i would be a good moderator .

>how about pizza tonight?
i ' m down . i ' m down rn

>what do you do for work?
just buy a buy UNK

A few observations:
1) The model worked better with accompanying a question with a question mark probably because there were more of these in the training set.
2) The model worked if larger sentences than on shorter sentences.
3) We saw a lot of UNK's in the responses because of the small vocabulary size.

The following are the train and test loss for the model:
 
We ran the model for 130000 but the best results came on early stopping at 71000 iterations. The perplexity were as follows:
Train perplexity: 9.06
Validation perplexity: 182.415 (avg over 4 sets)

Other evaluation techniqiues that could be used are:
1) Syntactic parsing of the response (using parse tree) to test for grammatical mistakes.
2) Word overlap using longest common subsequence (without stop words) to find a relation between what is asked and what is replied.
3) Over the span of the whole conversation, we can get topics out (using LDA or some other topid modelling) for the user and the response generated by the model. We can then do a basic overlap between the users questions and the models responses on the topics, and we can measure if the model is staying on topic.
