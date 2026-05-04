# Generation

```text
Let's make a presentation for general modern AI knowledge.
  On the first slide explain what is AI, what kind of AI exists - symbolic model (rule-based), instructions based, machine learning and others (I cannot recall right now, please add).
  Make sure it looks like a tree. The purpose of the presentation would be to focus on machine learning. In the machine learning section specify different algorithms - decision forest,
  random forest, bigram models and also neural networks (which are the root in LLM). Maybe add a few sentences explaining basic CNN and RNN and just add transformers (but without
  explanation about them) as they will be addressed later on.
  On the next slide - explain what a neural network is - a forward pass - basically performing matrix multiplication and finishing up with a cross entropy loss function and outputing
  logits - which are probabilities for predicting the next token. Also, explain how a backward pass works based on deriving the loss function against a particular parameter (also how we
  can use the chain rule in order to derive complex expression) we nudge the network in the right direction. Add a very brief explanation about different types of layers - linear,
  activation layer (with a modern activation function), normalization layer (batch and / or layer), attention layer, softmax (if anything else is also needed - please add it with
  explanation, since I may not be aware of it).
  On the next slide - let's discuss about the tokenization - add an example - a simple word that can be tokenized per character. Specify that there is also a special token that denotes
  beginning/end of word. Then explain that in this word there are numerous examples - 7 special tokens, first letter, 6 special tokens, first 2 letter, and so on. Note that training - in
  order to take advantage of linear arithmetics is happening in batches - basically all examples together (becoming a matrix with two dimensions). Then also explain a bit that the
  mechanism for attention would actually add to our example word another dimension - using an embedding matrix. The embedding matrix will be based on the vocabulary and the number of
  scalars we would like to use in order to take into the account the position of the token in the training data. Also explain that the training data is basically split into 3 sets -
  training/test/validation. Do not forget to mention that the context is basically the size of the input layer of the network. A forward pass takes into account everything in the context
  and inference is basically performing a forward pass (although in some cases certain layers behave differently in inference vs training)
  On the next slide - we want to build from a simple LLM to basically an agent. Have one block that represents the LLM and note that it does not have any memory or capabilities outside of
  predicting the next character based on an input of characters. Add also a user that can feed it prompts (pure text) and expect text in return (prediction). Then add two more boxes -
  conversation memory and long-term memory. In the conversation memory - just list some options - in-memory, DBs. For the long-term memory - basically tool can be used to retrieve
  information and load it into context (challenge me if wrong). The storage can again be DBs or a RAG. Then add another box - tools - where you can have web scraping, bash execution or
  anything else. Wrap all of the boxes in a big box - just with border and name it agent harness.
  On the next slide - show the hierarchy between different types of prompts - system prompt, user prompt, tool request, tool response. Explain how skills or agents are loaded when using
  popular coding agents (I think in claude - basically it detects you want to use a particular agent and then uses a tool to find the right .md file and adds it to the context, the model
  is also trained in the SFT - supervised fine-tuning stage to behave like an agent). Explain how all these prompts are just guidance compared to actual enforcement in the agent harness.
  On the next slide - show the stages through which a model passes before we actually see what we see today from modern LLMs. From base model - the training explained in the beginning, to
  SFT - supervised fine-tunning - basically human annotated sets of data. Then binary classification reward training - with basically introducing a reward token. Then RLHF or RLAIF -
  basically making the reward not only a binary classification but rather adding a score it.
  The final slide should be left for Q&A
```

Another agent with clean context

```text
Can you do a review of this presentation and challenge it in areas where you think it's misleading or inaccurate?
```

# Fixes

```text
Okay, it seems I cannot scroll down to view the entire slide in the presentation, can you fix this?
```

```text
It seems that now the footer with the slide number is in the middle of the page, can you fix this
```

```text
Looking at the first slide - Programmatic AI Systems - isn't this only workflows, not tooling around models.
```

```text
On slide 2 - can you have a separate row for the backward pass - again with a graph, basically explaining you calculate every parameter with respect to the loss function - basically
  doing dL/dParameter - and how does a chain-rule apply on a different layer (based on the derivative of the previous layer)
```

```text
On slide - 3:
 - have a first row - that explains how the training data is split into 3 sets - training/validation/test. 
    - explain that the test set should be used only when we are sure the model is ready to mitigate risks of overfitting
 - then have a second row that explains what is a token with the existing example of character level tokenization. Also provide a table that shows tokenized inputs as a batch. 
 - then have a third row - that explains what an embedding matrix is and how it adds a third dimension to the batch - with information about the position. Again provide a table - this time with a row for the input tokens of a single row of the batch and columns - the positional information as digits. 
    - keep the information that when you combine batches with tokens with embedding matrix - it becomes a 3 dimensional matrix
    - specify this is self-attention and that in order to have multiple-heads - the positional information can be split on the number of heads basically
```

```text
Okay, in the example for the embeddings - can you add more rows - I mean there are more channel vectors than a single one usually
```

```text
Okay, can you add a 4th row - where it explains what B, T and C are.
```

```text
On slide 2 - can you modify the graph - to actually be input -> linear -> activation -> linear -> logits -> softmax -> loss and wrap the linear -> activation -> linear with a border and name it an MLP - Multi-Layer-Perceptron. Modify the backward pass in the same way.
```

```text
On slide 4 - do not have the "prompt in text out" inside the user - rather have an arrow between the user and the llm core with that label. Also have an arrow between the User and the whole agent harness - with a label - provide tasks and expect real world results. 
```