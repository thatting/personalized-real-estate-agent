
### Project: Personalized Real Estate Agent

The project consists of three parts: synthetic data generation, semantic search and augmented response generation. It has been created using LangChain and OpenAI.


#### Synthetic Data Generation
Specifications for 10 properties has been provided (neighborhoods in London). 
A prompt template has been defined and gpt-3.5 Turbo has been called to provide the real estate listings. The listings are stored individually in directory 'data'.  Also, the listings are stored collectively in file 'listings.txt'.

#### Semantic Search
An 'llm' object has been created from class ChatOpenAI. A 'loader' object has then been created from class DiretoryLoader. The 'loader' object is used to load the real estate listings. The class CharacterTextSplitter has been used to split the documents into chunks for more efficient storage. Finally, the chunks are stored as embeddings in a Chroma vector database.  

A query has been created using 5 questions and answers. The Chroma vector database is searched for the top 5 most similar documents to this query.

Lastly, a RetrievalQA chain has been used to find the real estate listing which is semantically the most similar out of these five listings.


#### Augmented Response Generation
A memory object has been created using the CombinedMemory class.  The memory consists of two parts: summary_memory and conversational_memory.  
A recommender template is then created to describe how to augment the real estate listings. The recommender template, memory object and llm object are used to create an instance of a Conversation Chain (class ConversationChain). 
This instance is used to augment the 10 real estate listings. 

NB: I have tried to use the Vocareum key which was recently provided, however, this led to errors saying that I have an insufficient budget available. There seems to be a problem with the proxy server (parameter open_api_base). Instead, I have defined an environment variable 'OPENAI_API_KEY' with my own key from OpenAI, which still has funds on it. Also, I have used command: llm = ChatOpenAI() instead of command: llm = OpenAI(...). This is a more up-to-date command and works fine.