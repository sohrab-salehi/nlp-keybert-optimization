# NLP Project: Optimizing KeyBERT for Advanced Keyword Extraction ✨

## Overview 🔬
This project investigates keyword extraction using KeyBERT with optimized hyperparameters. The study enhances evaluation metrics to accommodate partial matches, significantly improving precision. By systematically fine-tuning hyperparameters and performing model selection, KeyBERT is optimized on the SemEval dataset and its adaptability is assessed through transfer learning on the KPTimes dataset.

## Features 🚀
- Preprocess textual data by removing extraneous elements such as links, mentions, hashtags, white spaces, and punctuation.
- Optimize KeyBERT’s hyperparameters for enhanced keyword prediction accuracy.
- Evaluate and compare multiple transformer architectures for keyword extraction.
- Implement Maximum Marginal Relevance (MMR) to improve keyword selection diversity and relevance.
- Examine cross-domain generalization using transfer learning on the KPTimes dataset.

## Datasets 📊
The project leverages two distinct datasets:

1. **SemEval-2010 Task 8 Dataset**
   - Contains 8,000 training samples and 2,700 test samples.
   - Expert-annotated entities with high-quality linguistic annotations.
   - Average sentence length of approximately 120 words.
   - Downloaded from Hugging Face using the `load_dataset` method:
   ```python
   from datasets import load_dataset
   dataset = load_dataset("semeval2010_task8")
   ```

2. **KPTimes Dataset (Sports Domain)**
   - Comprises 260,000 training samples and 20,000 test samples.
   - Consists of long-form news articles with complex syntactic structures.
   - Average sentence length of approximately 500 words.
   - The dataset was obtained from [this repository](https://github.com/ygorg/KPTimes).

## Installation ⚙️
To set up the project environment:

1. Clone the repository:
   ```sh
   git clone https://github.com/your-username/nlp-keybert-optimization.git
   cd nlp-keybert-optimization
   ```

2. Create and activate a virtual environment (optional but recommended):
   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   ```

3. Install required dependencies:
   ```sh
   pip install -r requirements.txt
   ```

### Running on Google Colab 💻
Certain Jupyter notebooks within this project are configured for execution on **Google Colab**. These notebooks may include:
- `!pip install` commands for installing dependencies within the Colab environment.
- `from google.colab import drive` for accessing Google Drive storage.
- Environment setup commands specific to Colab.

For execution on a local machine, these Colab-specific commands should be removed or modified accordingly.

## Project Structure 📂
```
├── results/           # includes all the running results in csv format
├── notebooks/           # Jupyter notebooks (see details below)
│   ├── baseline.ipynb
│   ├── baseline_new_eval.ipynb
│   ├── MMR.ipynb
│   ├── maxsum.ipynb
|   ├── results.ipynb
│   ├── model_exploration_maxsum.ipynb
│   ├── model_exploration_mmr.ipynb
│   ├── transfer_learning.ipynb
├── requirements.txt     # Project dependencies
├── README.md            # Documentation
```

### Notebooks 📓
The `notebooks/` folder contains Jupyter notebooks dedicated to different tasks:
1. **baseline**: Initial KeyBERT run with a strict evaluation method.
2. **baseline_new_eval**: KeyBERT run results after modifying the evaluation function.
3. **MMR**: Fine-tuning hyperparameters using Maximum Marginal Relevance (MMR).
4. **maxsum**: Fine-tuning hyperparameters using MaxSum selection.
5. **results**: Running results and data visualization.
6. **model_exploration_maxsum**: Model exploration with MaxSum, running KeyBERT with different input models.
7. **model_exploration_mmr**: Same as 6 but using MMR.
8. **transfer_learning**: KeyBERT run on the KPTimes dataset (sports category) with the best hyperparameters from the best SemEval run.

## Results 📈
- **Evaluation Metrics**: Precision increased from 7% to 42% by incorporating partial matches.
- **Hyperparameter Optimization**: Achieved a peak **79.5% F1-score** using MMR.
- **Transformer Model Performance**:
  - Sentence-Transformers/Paraphrase-MiniLM-L6-v2 attained **80% precision** on the SemEval dataset.
  - Comparative analysis of alternative models including RoBERTa, ALBERT, and MPNet.
- **Transfer Learning Analysis**:
  - The optimized model was applied to the KPTimes dataset (sports domain).
  - Performance degradation observed due to longer sentence structures, with precision decreasing to 18%.

## Future Research Directions 🔍
- Explore segmentation techniques to improve performance on lengthy texts.
- Conduct domain-specific fine-tuning for enhanced adaptability.
- Investigate newer transformer architectures (e.g., GPT, T5) for keyword extraction tasks.
- Leverage Sentence-BERT (SBERT) for improved contextual keyword extraction.
- Incorporate stemming techniques to enhance keyword alignment accuracy.

## Contributing 🤝
Contributions are encouraged! To participate, open an issue or submit a pull request.

## License 📜
This project is distributed under the MIT License.
