<h1 align="center">IBM watsonx Plugin for LLM Overview 🌐✨</h1>
<p align="center">This plugin integrates IBM watsonx.ai with [`llm`](https://github.com/simonw/llm) to bring advanced AI capabilities to your command-line interface (CLI).</p>

<div align="center">
    <img src="https://img.shields.io/pypi/v/llm-watsonx.svg" alt="PyPI Version Badge">
    <img src="https://img.shields.io/badge/license-Apache%202.0-blue.svg" alt="License Badge">
</div>

<h2 align="center">Deskripsi</h2>
<p>IBM watsonx.ai is a powerful AI platform that allows you to leverage cutting-edge machine learning models. By integrating with the `llm` plugin, you can easily interact with these models directly from the command line. 🔥💡</p>

<h3>Langkah-Langkah Penggunaan 🛠️</h3>
<p>Berikut adalah langkah-langkah untuk menggunakan plugin ini:</p>


Install this plugin in the same environment as LLM. From the current directory

```bash
llm install llm-watsonx
```

## Configuration

You will need to provide the following:

- API Key from IBM Cloud IAM: https://cloud.ibm.com/iam/apikeys
- Project ID (from watsonx.ai instance URL: https://dataplatform.cloud.ibm.com/projects//)
- Associate a Watson Machine Learning (WML) service to your watsonx.ai instance
  1. Inside your watsonx project, navigate to: "Manage" > "Service & Integrations"
    - Alternatively, paste your project ID here and go this URL: `https://dataplatform.cloud.ibm.com/projects/<YOUR PROJECT ID>/manage/services?context=wx`
  2. Click "Associate service" > Check "WatsonxMachineLearning" > Click "Associate"

  > Note: WML service(s) are hosted on your IBM Cloud account (https://cloud.ibm.com/resources). Make sure to have a WML service provisioned and active in your IBM Cloud account for best response rate.

```bash
export WATSONX_API_KEY=
export WATSONX_PROJECT_ID=
```

- Optionally, if your watsonx instance is not in `us-south`:

```bash
export WATSONX_URL=
```

## Usage

Get list of commands:

```bash
llm watsonx --help
```

### Models

See all available models:

```bash
llm watsonx list-models
```

See all generation options:

```bash
llm watsonx list-model-options
```

#### Example

```bash
llm -m watsonx/meta-llama/llama-3-8b-instruct \
    -o temperature .4 \
    -o max_new_tokens 250 \
    "What is IBM watsonx?"
```

#### Chat Example

```bash
llm chat -m watsonx/meta-llama/llama-3-8b-instruct \
    -o max_new_tokens 1000 \
    -s "You are an assistant for a CLI (command line interface). Provide and help give unix commands to help users achieve their tasks."
```

### Embeddings

See all available models:

```bash
llm watsonx list-embedding-models
```

#### Example

```bash
cat README.md | llm embed -m watsonx/ibm/slate-30m-english-rtrvr
```
