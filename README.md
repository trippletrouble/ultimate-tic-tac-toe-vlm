# Ultimate Tic Tac Toe: Multimodal AI Fine-Tuning
This project implements a generative VQA approach to solving Ultimate Tic Tac Toe. We fine-tuned a Vision-Language Model (VLM) to perceive game states, identify valid moves, and apply strategic logic through hierarchical tasks.

# Model Evaluation & Training
Initially, the model was evaluated on a base dataset of 1,001 manual samples to establish a performance baseline. We identified significant issues with spatial hallucinations and conversational drift.

### Key Points:
- LoRA Changes: We increased the LoRA rank and alpha from 32 to 64, and finally to 128 to provide sufficient capacity for the complex, hierarchical board logic.
- Format Enforcement: Introduced strict ```JSON_START``` and ```JSON_END``` anchors to force machine-readable outputs and simplify parsing.
- Dataset Expansion: Scaled to 4,004 data points by applying 90°, 180°, and 270° rotations to the original dataset to improve state recognition and in turn the robustness.

# Repository Structure

- ```adapter_uttt_qwen_8b_v2/```: Model configuration and metadata
- ```documentation/```: Contains the full preTrain_Eval.pdf and postTrain_Eval.pdf reports.
- ```uttt_qwen_dataset/```: The 4,004-sample training dataset in Parquet format.
- ```train_model.ipynb```: The training pipeline using Unsloth.
- ```evaluate.ipynb```: The script for calculating accuracy and logic scores.