---
title: My Document
summary: A brief description of my document.
authors:
    - Waylan Limberg
    - Tom Christie
date: 2018-07-10
some_url: https://example.com
---

# NLP Before Transformers

## RNNs (Recurrent Neural Networks)
RNNs, or Recurrent Neural Networks, are a type of neural network designed for sequential data, where the current output depends not just on the current input, but also on previous inputs. This is achieved by maintaining a hidden state that captures information about previous time steps. At each step, the hidden state is updated based on the current input and the previous hidden state, allowing the network to learn dependencies over time. RNNs are commonly used for tasks like language modeling, speech recognition, and time series forecasting, where understanding the context of prior data points is crucial. However, standard RNNs struggle with long-term dependencies due to issues like vanishing gradients, where the influence of earlier time steps diminishes significantly as the sequence length increases, limiting their ability to remember information over extended periods.

## LSTM (Long Short-Term Memory)
LSTM, or Long Short-Term Memory, is a specialized form of RNN designed to address the problem of long-term dependency retention that standard RNNs face. LSTMs introduce a gating mechanism—consisting of input, forget, and output gates—that controls the flow of information through the network. These gates regulate which information is added to the cell state (the memory of the network), which information is removed, and what part of the cell state is used to produce the output. By doing so, LSTMs can maintain and update relevant information over longer periods, effectively mitigating the vanishing gradient problem.

LSTMs are particularly useful in tasks that require understanding and retaining long-term dependencies, such as text generation, machine translation, and speech recognition. For example, in language translation, understanding the context of a word within a longer sentence is crucial for accurate translation. LSTMs enable the model to keep track of this context more effectively than standard RNNs, making them a popular choice in NLP before the rise of transformer-based models. However, despite these improvements, LSTMs can still struggle with very long sequences and require more computational resources than simpler RNNs.

## Comparison with Transformers
Transformers fundamentally differ from RNNs and LSTMs in how they handle sequential data. While RNNs and LSTMs process sequences step-by-step (sequentially), transformers leverage an attention mechanism that allows them to process entire sequences in parallel. This key distinction leads to several advantages and disadvantages when comparing transformers with RNNs and LSTMs.

**Advantages of Transformers:**
- **Parallel Processing**: Transformers handle data in parallel, making them significantly faster, especially for long sequences, as there’s no need to wait for one step to complete before processing the next.
- **Handling Long-Range Dependencies**: Transformers excel at capturing long-range dependencies because their self-attention mechanism evaluates relationships between all tokens in a sequence at once, rather than relying on sequential processing where earlier information can be diluted.
- **Scalability**: With the ability to process large datasets efficiently, transformers can be scaled up with more parameters and data, improving performance on complex tasks.

**Disadvantages of Transformers:**
- **Computational Intensity**: The parallel nature of transformers, combined with the need to calculate attention scores between all token pairs, makes them more computationally intensive. They require more memory and processing power compared to RNNs and LSTMs, particularly as sequence length increases.
- **Data-Hungry**: Transformers require large amounts of data to train effectively, which can be a limiting factor in domains with less available data.

**Advantages of RNNs and LSTMs:**
- **Lower Computational Cost**: RNNs and LSTMs, particularly when not dealing with extremely long sequences, can be less demanding in terms of computational resources, making them suitable for smaller-scale applications or where parallel processing isn’t a priority.
- **Sequential Learning**: For tasks where step-by-step processing mirrors the nature of the problem (like streaming data or real-time predictions), RNNs and LSTMs can be more intuitive and easier to implement. They are much better at tasks such as stock price prediction compared to Transformer models

**Disadvantages of RNNs and LSTMs:**
- **Slower for Long Sequences**: The sequential nature of RNNs and LSTMs makes them slower for long sequences, as each step depends on the previous one.
- **Difficulty with Long-Term Dependencies**: Despite LSTM’s improvements, both RNNs and LSTMs can still struggle with very long-term dependencies compared to transformers.

While transformers generally outperform RNNs and LSTMs on a wide range of tasks due to their ability to handle long-term dependencies and parallel processing, they do so at a higher computational cost and with a need for large amounts of data. RNNs and LSTMs still hold value in specific contexts, particularly when computational resources are limited or when the problem inherently benefits from sequential learning.