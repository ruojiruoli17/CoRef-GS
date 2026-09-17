<h1 align="center">
  🤖 CoRef-GS
</h1>

<h3 align="center">
  Cooperative Referring Gaussian Splatting for Multi-Agent Scene Understanding
</h3>

<p align="center">
  <b>Multi-Agent 3D Gaussian Splatting · Open-Vocabulary Grounding · Cooperative Referring</b>
</p>

<p align="center">
  🚧 <b>Code and dataset are coming soon.</b>
</p>

---

## 🌟 Overview

**CoRef-GS** is a cooperative referring scene understanding framework for
multi-agent robotic systems based on **3D Gaussian Splatting (3DGS)**.

In our setting, multiple robots independently explore complementary regions of
the same indoor environment and construct their own local semantic Gaussian maps.

CoRef-GS enables these independently reconstructed maps to be:

> 🗺️ **aligned** → 🔗 **associated** → 🧠 **reasoned over** → 🎯 **queried**

while preserving language-grounded referring ability after map fusion.

Unlike conventional single-agent referring methods, the target object or its
contextual landmark may come from observations of another robot, while the
final referring decision is still interpreted from the **querying robot's
viewpoint**.

<br>

<p align="center">
  <img src="assets/overall.png" width="95%">
</p>

<p align="center">
  <i>
    Figure 1. Overview of CoRef-GS. Multiple agents independently construct
    local semantic Gaussian maps, which are aligned and fused for cooperative
    language-grounded referring.
  </i>
</p>

---

## 🧩 Framework

CoRef-GS contains three main components:

### 🗺️ 1. Instance-aware Local Semantic Mapping

Each agent independently reconstructs an **instance-aware semantic Gaussian
map**, where Gaussian primitives are equipped with:

- 🧩 instance-level grouping
- 🔤 CLIP-aligned semantic embeddings
- 🔎 open-vocabulary querying capability

This shared semantic space allows independently reconstructed maps to remain
semantically comparable.

---

### 🔗 2. Cross-Agent Alignment & Instance Association

Local Gaussian maps reconstructed by different agents initially lie in
different coordinate systems.

CoRef-GS performs **image-assisted coarse-to-fine Sim(3) registration** to
align these maps into a common frame.

After geometric alignment, duplicate object instances across different maps
are associated using both:

**geometry consistency** + **semantic consistency**

This produces a shared object-level representation without retraining the
local semantic maps.

---

### 🧠 3. View-conditioned Relation Reasoning

Given a referring expression such as:

> **"The pink doll on the left."**

CoRef-GS first identifies candidate target and landmark objects and renders
their instance masks from the querying robot's viewpoint.

A **View-conditioned Mask Relation Graph** is then constructed to reason about
spatial relations such as:

`left of` · `right of` · `in front of` · `behind` · `above` · `beneath`

This enables the same grounding module to operate on either a **local map**
or the **aligned cooperative map**.

<br>

<p align="center">
  <img src="assets/pipeline.png" width="98%">
</p>

<p align="center">
  <i>
    Figure 2. Overall framework of CoRef-GS, including local semantic mapping,
    view-conditioned relation reasoning, and cross-agent alignment.
  </i>
</p>

---

## 🚀 Key Features

✨ **Independent Local Mapping**  
Each robot constructs its own semantic Gaussian map independently.

🔄 **Cross-Agent Sim(3) Registration**  
Align independently reconstructed Gaussian maps under large viewpoint changes.

🧩 **Cross-Map Instance Association**  
Associate duplicated object identities across different robot maps.

🔤 **Open-Vocabulary Grounding**  
Use CLIP-aligned semantics to preserve cross-map language queryability.

👀 **View-conditioned Spatial Reasoning**  
Interpret spatial relations from the querying robot's viewpoint.

🤝 **Cooperative Referring**  
Ground objects that may only be visible in another agent's observations.

---

## 📦 Release

> 🚧 This repository is currently under preparation.

- [ ] 💻 Source code
- [ ] 📚 CoQuad-Ref Dataset
- [ ] 🧠 Pretrained models
- [ ] 🛠️ Installation instructions
- [ ] 📊 Evaluation scripts

---

## 📖 Citation

If you find **CoRef-GS** useful for your research, please consider citing our work:

```bibtex
@article{corefgs2027,
  title  = {CoRef-GS: Cooperative Referring Gaussian Splatting
            for Multi-Agent Scene Understanding},
  author = {Anonymous},
  year   = {2027}
}
