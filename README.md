### yy3242 Project 1

# List of files:
src/main.py stop_words.txt Makefile README.md requirements.txt transcript.txt
# Instructions:
```
make dev-shell # it installs all python and venv and activate the virtual env.
. .venv/bin/activate # used if the virtual env is not activated in make dev-shell, can be ignored.
make install-requirements # install all pip requirements. 
python3 src/main.py <google api key> <google engine id> <precision> <query>
``` 
# Description

In my implemetation, structure is very clear, as I have docstrings explaining each function. Below is the pseudocode starting from main:
```
main: 
	while True:
		query google with cur_query
		display to user the top 10 results get their feedback by display_and_retrieve_user_response() # output a instruction to stop or not and a new query
display_and_retrieve_user_response:
	display to user all api responses and retrieve user feedback.
	calculate a score and compare to precision.
	if below precision, go to reformulate_query()

reformulate_query(): 
	My query modification method.
	It first extracts all titles and summaries of relevant and not relevant api responses.
	Then use tfidfvector to calculate a dictionary that has key: a word extracted from titles and summaries, value: tfidf weight.
	Because we need to based on relevant information, and delete all irrelavant, therefore, we only need to calculate based on relevant information. However, it would be better if we use all words as vocab to calculate out a better tfidfvector instance. So we do that and see use all the words that are in relevant and not in non-relevant.
	And we sort them based on their weight. The first should be most relevant to our feedback to the api search.
	Then we add at most two words and keep the rest to the query.
	Important: as we use the sorted output, we do not preserve the order of the original query, we give them a new order based on current result without deleting them.
```
My first step of implementation is based on:
```
https://github.com/googleapis/google-api-python-client/blob/main/samples/customsearch/main.py
```
# Google API Key
```
AIzaSyB2aL6qLGAj6GehkVCn7hS_IT10_uFwssE
```

# Google Search Engine ID
```
f574718d7af0314d2
```

# Additional Information
I did not collaborate with anyone, person with uni yh3575 did not contribute to this project.
