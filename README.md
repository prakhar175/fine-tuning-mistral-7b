# Engage-GPT: Fine-tuned YouTube Comment Response Model

A specialized language model fine-tuned for generating contextual responses to YouTube comments, functioning as a virtual data science consultant.

## 🎯 Model Overview

Engage-GPT is built on top of the Mistral-7B-Instruct-v0.2 model and fine-tuned using LoRA (Low-Rank Adaptation) to respond to YouTube comments in a natural, engaging manner. The model adapts its response length and technical depth based on the input comment.

### Base Model
- **Base**: TheBloke/Mistral-7B-Instruct-v0.2-GPTQ (Quantized version)
- **Architecture**: Causal Language Model
- **Fine-tuning Method**: LoRA (Low-Rank Adaptation)
- **Trainable Parameters**: 2,097,152 (0.79% of total parameters)

## 📊 Training Results

The model was trained for 10 epochs with the following performance:

| Epoch | Training Loss | Validation Loss |
|-------|---------------|-----------------|
| 1     | 4.233200      | 3.803648        |
| 2     | 3.491500      | 3.128949        |
| 3     | 2.916400      | 2.629169        |
| 4     | 2.442100      | 2.335195        |
| 5     | 2.227600      | 1.974963        |
| 6     | 1.743100      | 1.754646        |
| 7     | 1.536300      | 1.613378        |
| 8     | 1.476200      | 1.503656        |
| 9     | 1.388500      | 1.456323        |
| 10    | 1.272400      | 1.442117        |


## 🔧 Training Configuration

### LoRA Configuration
- **Rank (r)**: 8
- **Alpha**: 32
- **Target Modules**: ["q_proj"]
- **Dropout**: 0.05
- **Bias**: None
- **Task Type**: CAUSAL_LM

### Training Hyperparameters
- **Learning Rate**: 2e-4
- **Batch Size**: 4 (per device)
- **Epochs**: 10
- **Weight Decay**: 0.01
- **Gradient Accumulation Steps**: 4
- **Warmup Steps**: 2
- **Optimizer**: paged_adamw_8bit
- **Precision**: FP16
- **Max Length**: 512 tokens


## 📈 Model Characteristics

### Response Behavior
- **Adaptive Length**: Matches response length to comment complexity
- **Technical Depth**: Escalates technical detail upon request
- **Signature**: Always ends with "–Engage-GPT"
- **Natural Tone**: Maintains engaging, conversational style

### Training Dataset
- **Source**: shawhin/shawgpt-youtube-comments
- **Preprocessing**: Left truncation at 512 tokens
- **Split**: Train/Test evaluation

## 💻 Hardware Requirements

### Training
- GPU with at least 16GB VRAM (recommended)
- CUDA-compatible device
- Sufficient RAM for model loading

### Inference
- GPU with at least 8GB VRAM
- Can run on CPU (slower performance)

## 🎯 Use Cases

- YouTube content creator comment responses
- Data science consultation chatbot
- Educational content engagement
- Automated community management
- Customer support for technical content

## 📝 Model Limitations

- Optimized for YouTube comment format
- Requires specific prompt template for best results
- Performance may vary with out-of-domain comments

## 🔄 Model Updates

The model uses gradient checkpointing and can be further fine-tuned on additional data. The LoRA approach allows for efficient updates without retraining the entire base model.


---

*Built with ❤️ using Hugging Face Transformers and PEFT*
