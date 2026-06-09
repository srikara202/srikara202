<h1 align="center">Hey, I'm Srikara 👋</h1>

<p align="center">
  <em>Applied AI Engineer • PhD in quantum communications • LLMs, RAG, multimodal ML, and the engineering that ships them</em>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/srikaras">LinkedIn</a> •
  <a href="https://scholar.google.com/citations?user=QmFHyvIAAAAJ">Google Scholar</a> •
  <a href="mailto:srikara.s.phd@gmail.com">Email</a>
</p>

<p align="center">
  <img alt="LLMs" src="https://img.shields.io/badge/LLMs-curious-6C63FF?style=flat-square" />
  <img alt="RAG" src="https://img.shields.io/badge/RAG-from%20scratch-5B5BD6?style=flat-square" />
  <img alt="Multimodal" src="https://img.shields.io/badge/Multimodal-built%20by%20hand-FF6B6B?style=flat-square" />
  <img alt="MLOps" src="https://img.shields.io/badge/MLOps-deployment%20%26%20observability-0EA5E9?style=flat-square" />
</p>

---

### 🙂 a little about me

I'm an applied AI engineer based in **Sydney**. Before this I spent five years on a PhD in **quantum communications**, which left me with eight published papers and a low tolerance for systems that sound impressive but don't hold up. That's mostly what I bring to AI work: a bias toward probability, careful evaluation, and checking whether something does what it claims.

Now I build across LLMs, RAG, multimodal models, and the engineering that surrounds them : APIs, deployment, tracing, evaluation. The parts that separate a demo from something people can rely on.

Most of what I build runs on the same loop:

- figure out how it works under the hood  
- build it end to end  
- find where it breaks  
- make it useful for someone other than me  

### 🧰 stuff I reach for a lot

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=python,pytorch,tensorflow,sklearn,fastapi,react,ts,docker,kubernetes,azure,aws,postgres,git,githubactions&perline=7" />
  </a>
</p>

<p align="center">
  <img alt="Hugging Face" src="https://img.shields.io/badge/Hugging%20Face-Transformers-FFD21E?style=flat-square&logo=huggingface&logoColor=black" />
  <img alt="PEFT LoRA" src="https://img.shields.io/badge/PEFT-LoRA-7C3AED?style=flat-square" />
  <img alt="SentenceTransformers" src="https://img.shields.io/badge/Retrieval-SentenceTransformers-10B981?style=flat-square" />
  <img alt="Supabase pgvector" src="https://img.shields.io/badge/Vector%20DB-Supabase%20pgvector-3ECF8E?style=flat-square&logo=supabase&logoColor=white" />
  <img alt="LangGraph" src="https://img.shields.io/badge/Orchestration-LangGraph-1C3C3C?style=flat-square" />
  <img alt="LangFuse and RAGAS" src="https://img.shields.io/badge/Tracing%20%26%20Eval-LangFuse%20%7C%20RAGAS-DB2777?style=flat-square" />
  <img alt="Terraform" src="https://img.shields.io/badge/IaC-Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white" />
  <img alt="Prometheus and Grafana" src="https://img.shields.io/badge/Monitoring-Prometheus%20%7C%20Grafana-EA580C?style=flat-square&logo=prometheus&logoColor=white" />
</p>

### 🧠 the kind of projects you'll find here

*Loosely ordered: production-shaped systems first, from-scratch builds last.*

#### AI systems built to ship

- **AI Code Reviewer** : a GitHub App that reviews pull requests with four specialised LLM agents (static analysis, security, style, architecture) running in parallel through a **LangGraph** graph, then posts a single consolidated review in about a minute. It runs as **seven Kubernetes workloads** on AWS EKS: HMAC-verified webhooks, Redis/Celery queues that return `202` while analysis happens off the request path, Postgres for state, **LangFuse** tracing on every model call, a weekly **RAGAS** faithfulness gate, and per-service CI/CD that deploys over GitHub→AWS **OIDC**. The model call was the easy part; the real work was the cloud and MLOps scaffolding that makes it operable. I deployed it, validated it on a real PR for a fraction of a cent, and tore it back down to **$0**.
- **YouTube Ad Compliance Checker** : a retrieval-backed pipeline that audits ad videos. **Azure Video Indexer** pulls the transcript and on-screen text, **Azure AI Search** retrieves the relevant policy passages, and **Azure OpenAI** returns a structured verdict, all wrapped in a **FastAPI + React** app with async jobs. The interesting constraint: YouTube blocks downloads from Azure IP ranges, so I split execution and added a self-hosted worker that picks those jobs up through Blob storage without breaking the hosted product.

#### grounded generation & retrieval

- **Grounded Nutrition RAG Chatbot** : a single-document RAG system built from first principles, deliberately without LangChain or Chroma so I could see where retrieval falls over instead of trusting a framework. Most of the time went into chunking: I compared fixed-size, structural, recursive, and semantic splitting across **1,200+ pages and 3,300+ chunks**. It ships as a **React + Supabase (pgvector)** app with citation popups, so every answer points back to the exact passage behind it.
- **Llama-2 English → SQL** : fine-tuned **Llama-2-7B** for schema-grounded SQL using **LoRA adapters and 4-bit NF4 quantisation**, which made iterating on a 7B model practical on a single Colab GPU. The lesson that stuck: for structured generation, the prompt and schema grounding matter as much as the weights you train.

#### building from the inside out

- **GPT-2 from scratch** : a decoder-only transformer rebuilt in PyTorch : attention, causal masking, pre-LayerNorm blocks, autoregressive sampling. The part I'm proudest of is the weight loader that maps `distilgpt2`'s fused Conv1D attention weights into my per-head layout, then checks the logits match the reference almost exactly. Built to understand the internals, not to ship a model.
- **Image Captioning** : a ~32M-parameter captioner pairing a frozen `EfficientNet-B0` encoder with a Transformer decoder over **8,000+ images**. The whole point was the seam between vision and language: a trainable projection that lets the decoder condition on image features instead of treating the two modalities as separate problems.

### ✨ the through-line

I tend to start with *how does this thing work?* and stop somewhere around *okay, now it's usable.* The habits in between are pretty consistent: I keep generation grounded in something real (a schema, a document, evidence), I care more about evaluation and failure modes than about a slick demo, and I don't mind the messy stretch where a notebook slowly turns into an API, a container, and a deploy.

### 🌱 currently into

- transformer internals and training dynamics  
- LLM fine-tuning and evaluation  
- RAG quality: chunking, grounding, retrieval  
- multimodal systems  
- deployment and observability for AI  

### 🎵 outside of code

I sing : Indian classical mostly, plus whatever Western pop is stuck in my head that week : and I lose a fair few evenings to story-driven and open-world games. The rest of my spare time goes to AI papers and blogs, which is usually how these projects start: I read something, get curious, and a repo shows up a week later.

### 🤝 say hi

Always happy to talk about LLM systems, RAG, multimodal ML, or anything that sits between the theory and the implementation. I'm open to applied AI / ML engineering roles, and just as happy to trade ideas.

<p>
  <a href="https://www.linkedin.com/in/srikaras"><img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-srikaras-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
  <a href="https://scholar.google.com/citations?user=QmFHyvIAAAAJ"><img alt="Google Scholar" src="https://img.shields.io/badge/Google%20Scholar-publications-4285F4?style=for-the-badge&logo=googlescholar&logoColor=white" /></a>
  <a href="mailto:srikara.s.phd@gmail.com"><img alt="Email" src="https://img.shields.io/badge/Email-srikara.s.phd%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white" /></a>
</p>
