<div align=center>

# **[Neurips 2025]** Benford's Curse: Tracing Digit Bias to Numerical Hallucination in LLMs

</div>


## Getting started

### Environment Setup

1. clone the repository

```bash
git clone https://github.com/shamy28/Benford-Curse.git && cd Benford-Curse
```

2. install dependencies

```bash
pip install -r requirements.txt
```


## Datasets


The datasets used in this paper are located in the `Datasets/` directory. The directory contains the following files and directory:

### Identification Task

Both files contain 100 numerical sequences, each with the same configuration except for the last term. 

- `identification_lastbig.csv`
- `identification_lastsmall.csv`

### Digit Bias Benchmark
 Seven tasks on digit bias.


## Neuron_Bias
A compressed version of the biased neurons is provided for convenience. Users are advised to decompress the archive prior to usage.

## generation
The generation code for both the original and the pruned models is provided in the `generation/` directory.

## Check
To check the result of the generation content, please use the code in the `Check/` directory. We suggest using an LLM to extract the answer first.

## Probing 
We provide the original code for extracting digit selectivity of individual neurons in this directory. A complete version of the probing code will be released upon publication.
 

## Running the Model

### Prerequisites

1. Ensure all dependencies are installed:
   ```bash
   pip install -r requirements.txt
   ```

2. Download the required LLMs from HuggingFace. You can access models mentioned in the paper at https://huggingface.co/. Update the model path in the scripts or set the `--model_name` argument accordingly.

3. Ensure the dataset files are available in the `Datasets/` directory.

4. Extract the Neuron_bias archive if you plan to use the pruned model version:
   ```bash
   cd Neuron_bias
   unzip Neuron_bias.zip
   cd ..
   ```

### Running Generation Scripts

#### Using the Original Model

To run the generation script with the original (unpruned) model:

```bash
cd generation
python model_generation_original.py --model_name llama27b --task sequence_next_term --output_path "./results"
```

#### Using the Pruned Model

To run the generation script with the pruned model:

```bash
cd generation
python model_generation_pruned.py --model_name llama27b --task sequence_next_term --output_path "./results"
```

Replace `sequence_next_term` with the appropriate task name from the `Datasets/` directory.

### Checking Results

To check the results of generation, use the scripts in the `Check/` directory:

```bash
cd Check
python check.py
```


## Citation

```
@article{shao2025benford,
  title={Benford's Curse: Tracing Digit Bias to Numerical Hallucination in LLMs},
  author={Shao, Jiandong and Lu, Yao and Yang, Jianfei},
  journal={arXiv preprint arXiv:2506.01734},
  year={2025}
}
```
