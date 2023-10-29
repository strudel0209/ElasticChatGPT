# ABBDocs_GPT
Combining the search power of Elasticsearch with the Question Answering power of GPT

A repo to demonstrate the functionality of Elasticsearch in conjunction with OpenAI ChatGPT to boost ABB global portal search.
[Blog - ChatGPT and Elasticsearch: OpenAI meets private data](https://www.elastic.co/blog/chatgpt-elasticsearch-openai-meets-private-data)

![diagram](https://github.com/strudel0209/ChatGPTonELK/blob/main/Streamlit%20ChatGPT%20App/images/ElasticChat%20GPT%20Diagram.png)
## Flow
1. Python interface accepts user questions
- Generate a hybrid search request for Elasticsearch
- BM25 match on the title field
- kNN search on the title-vector field
- Boost kNN search results to align scores
- Set size=1 to return only the top scored document
2. Search request is sent to Elasticsearch
3. Documentation body and original url are returned to python
4. API call is made to OpenAI ChatCompletion
- Prompt: "answer this question <question> using only this document <body_content from top search result>"
5. Generated response is returned to python
6. Python adds on original documentation source url to generated response and prints it to the screen for the user

# Setup
- Run pip install -r requirements.txt
- Set authentication and connection environment variables (e.g., if running on the command line: export openai_api=”123456abcdefg789”)
  - openai_api - OpenAI API Key
  - elastic_url - Elastic Cloud Kubernetes http exposed service i.e https://localhost:9200
  - elastic_user - Elasticsearch Cluster User
  - elastic_pass - Elasticsearch User Password
<<<<<<< HEAD:Streamlit ChatGPT App/README.md
- Run the streamlit program streamlit run elasticsearch_chattgpt_k8s.py

