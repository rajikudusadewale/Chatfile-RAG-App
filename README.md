# ChatFiles - RAG-based Document Q&A Application

## Overview

ChatFiles is a Streamlit application that allows users to upload documents (PDF, DOCX, or TXT) and ask questions about their content. The application leverages OpenAI's language models, LangChain framework, and Chroma vector database to implement a Retrieval-Augmented Generation (RAG) pipeline for accurate document-based question answering.

Developed by DeDataDude

## Features

- **Document Upload**: Support for PDF, DOCX, and TXT files
- **Customizable Parameters**: Adjust chunk size and retrieval parameters
- **Interactive Q&A**: Ask questions about your documents and receive AI-generated answers
- **Cost Tracking**: Calculate and display token usage and estimated costs
- **Chat History**: View and track your question-answer history within the session

## Technology Stack

- **Frontend Framework**: Streamlit
- **LLM Provider**: OpenAI (gpt-3.5-turbo)
- **Embeddings**: OpenAI Embeddings (text-embedding-3-small)
- **Vector Database**: Chroma
- **Document Processing**: LangChain document loaders and text splitters

## Installation

1. Clone this repository
```bash
git clone https://github.com/rajikudusadewale/chatfile-RAG-App.git
```

2. Create a virtual environment and activate it
```bash
python -m venv venv
source venv/bin/activate  # On Windows, use: venv\Scripts\activate
```

3. Install the required packages
```bash
pip install -r requirements.txt
```

## Required Dependencies

The following packages are needed:
- streamlit
- langchain
- langchain_openai
- chromadb
- tiktoken
- openai
- python-dotenv
- PyPDF2 (for PDF loading)
- docx2txt (for DOCX loading)

Create a `requirements.txt` file with these dependencies.

## Usage

1. Run the Streamlit application
```bash
streamlit run app.py
```

2. In the sidebar:
   - Enter your OpenAI API key
   - Upload a document (PDF, DOCX, or TXT)
   - Set the chunk size (default: 512)
   - Set the K value for retrieval (default: 3)
   - Click "Add Data" to process your document

3. Ask questions about your document in the text input field
   - The AI will provide answers based on the content of your document
   - The chat history will be displayed below

## How It Works

1. **Document Loading**: The application loads documents using LangChain's document loaders
2. **Text Chunking**: Documents are split into manageable chunks using RecursiveCharacterTextSplitter
3. **Embedding Generation**: OpenAI's embedding model converts text chunks into vector embeddings
4. **Vector Storage**: Embeddings are stored in a Chroma vector database
5. **Retrieval**: When a question is asked, the application retrieves the most relevant chunks
6. **Answer Generation**: The LLM uses the retrieved chunks to generate an accurate answer

## Customization

- **Chunk Size**: Controls how documents are split (smaller chunks for precise retrieval, larger chunks for more context)
- **K Value**: Determines how many chunks are retrieved for each question (higher values provide more context but may introduce noise)

## Cost Considerations

The application calculates and displays:
- Total tokens used for embeddings
- Estimated cost based on OpenAI's pricing for text-embedding-3-small ($0.00004 per 1K tokens)

Additional costs will be incurred for each query using the ChatGPT API.

## Notes

- You must provide your own OpenAI API key
- For larger documents, processing time and costs will increase
- The application stores data only for the current session

## License

[DeDataDude]

## Acknowledgments

- OpenAI for providing the embedding and language models
- LangChain for the document processing and RAG pipeline framework
- Streamlit for the web application framework
