FROM ${CI_DEPENDENCY_PROXY_GROUP_IMAGE_PREFIX_FOR_DOCKERFILE}continuumio/miniconda3:latest

# see https://pythonspeed.com/articles/activate-conda-dockerfile/
# for details about the setup

WORKDIR /app

# Create the environment:
COPY environment.yml .
RUN conda env create -f environment.yml

# Make RUN commands use the new environment:
SHELL ["conda", "run", "-n", "nlp", "/bin/bash", "-c"]

# Add spacy models
RUN python -m spacy download en_core_web_trf --timeout=600
RUN python -m spacy download fr_dep_news_trf --timeout=600
RUN python -m spacy download fr_core_news_lg --timeout=600
RUN python -m spacy download de_dep_news_trf --timeout=600
RUN python -m spacy download de_core_news_lg --timeout=600
