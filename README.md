# Knowledge_DIstillation_in_Deep_Learning
Knowledge Distillation is a model-compression technique where a large, high-performing model (Teacher) transfers its knowledge to a smaller, faster model (Student).


Where is it used?. <br>
• In LLMs as well (DistilGPT, DistilBERT) to compress heavy GPT/BERT models for faster inference. <br>
• Smaller & faster inference: Runs on edge/mobile with lower latency and memory. <br>
• Retain accuracy: Soft targets transfer "dark knowledge" to keep performance close to teacher. <br>
• Lower serving cost: Fewer GPUs/CUs needed; higher throughput per server. <br>
• Ensemble -> single model: Compress multiple/large models into one compact network. <br>

***

How It Works<br>

Teacher model produces soft labels (probability distribution).<br>

Student is trained to match:<br>
The soft logits of the teacher<br>
The ground-truth labels (optional)<br>

Loss =<br>

Hard loss: CE(Student_output, true_labels)<br>
Soft loss: KL(Student_output, Teacher_output / T) × T²<br>
Where T = temperature (softens logits → exposes “dark knowledge”).<br>

Loss Function (distillation loss):<br>
• This is usually a combination of:<br>
  - Cross-Entropy Loss (for the true labels)<br>
  - KL-Divergence Loss (between the Teacher's and Student's soft outputs)<br>
  
To smooth the soft outputs, a temperature (T) parameter is used, which makes the softmax output "softer."<br>


- Distillation	-- Transfer knowledge to a smaller model	Reduces model size; keeps accuracy <br>
- Fine-tuning	-- Adapt a model to a task	Doesn’t reduce model size <br>
- Quantization	-- Reduce precision (FP32→INT8)	Speeds inference; small accuracy drop <br>

<img width="2000" height="1815" alt="image" src="https://github.com/user-attachments/assets/85d071a4-1d29-4023-92f9-f65f9a38d1af" />
