 # CDG: Cross-Domain Generalization for Robust Website Fingerprinting Defense

CDG (Cross-Domain Generalization) is a source-calibrated latent-space inference framework for robust open-world Website Fingerprinting (WF) under structural domain shift. Unlike conventional packet-level defenses, CDG performs inference entirely within the learned latent representation space without modifying encrypted traffic, requiring neither packet padding, bandwidth overhead, nor deployment-time retraining.

The proposed framework combines supervised contrastive representation learning, neighbourhood-density estimation, and prototype-aware semantic inference to improve monitored traffic recognition while maintaining a fixed source-calibrated false-positive operating point across previously unseen deployment domains.

---

# Key Contributions

- Introduces the first prototype-aware latent-space inference framework for improving cross-domain robustness in open-world Website Fingerprinting.
- Combines neighbourhood-density estimation with source-domain prototype representations to jointly exploit local geometric consistency and class-level semantic information.
- Maintains a fixed source-calibrated false-positive operating point without requiring target-domain supervision, deployment-time retraining, or packet modification.
- Formally characterizes the security–availability trade-off through the concepts of Availability Cost and Access Failure Rate (AFR).
- Evaluated against three representative Website Fingerprinting attacks: Deep Fingerprinting (DF), TikTok, and Swallow.
- Includes comprehensive cross-domain evaluation, Effective Attack Success Rate (EASR) analysis, ablation studies, runtime evaluation, and threshold-sensitivity analysis.

---

# Repository Structure

```
CDG/
│
├── SRC/
│   Main source code used to reproduce all experiments reported
│   in the manuscript.
│
├── TRAINER/
│   Training utilities reproduced from the Swallow framework,
│   including the BYOL trainer, momentum update, and loss
│   functions used to learn the encoder backbone.
│
├── MODELS/
│   Neural network architectures reproduced from the Swallow
│   framework, serving as the representation learning backbone
│   for the proposed CDG framework.
│
├── RESULTS/
│   ├── cross_domain/
│   │     Cross-domain performance evaluation (Table 4)
│   │
│   ├── attackers/
│   │     Effective Attack Success Rate (EASR) evaluation
│   │     and attacker performance (Table 5)
│   │
│   ├── ablation/
│   │     Prototype-aware inference ablation study (Table 6)
│   │
│   ├── runtime/
│   │     Runtime evaluation
│   │
│   └── threshold_sensitivity/
│         Threshold sensitivity analysis supporting the
│         security–availability trade-off
│
├── requirements.txt
├── LICENSE
└── README.md
```

---

# Experimental Evaluation

This repository reproduces all experiments reported in the accompanying manuscript, including:

- Cross-domain Website Fingerprinting evaluation under controlled structural domain shift.
- Evaluation against Deep Fingerprinting (DF), TikTok, and Swallow attacks.
- Effective Attack Success Rate (EASR) analysis.
- Cross-domain monitored traffic acceptance evaluation.
- Prototype-aware inference ablation study.
- Runtime performance evaluation.
- Threshold-sensitivity analysis.
- Security–availability trade-off analysis.

---

# Running the Experiments

## 1. Construct Structural Domains

```
python SRC/build_structural_domains.py
```

Constructs packet-volume-conditioned structural domains (A–D).

---

## 2. Prepare Source Domain

```
python SRC/prepare_source_domain.py
```

Prepares the source-domain reference manifold used throughout the experiments.

---

## 3. Train CDG

```
python SRC/train_cdg.py
```

Trains the supervised contrastive encoder and constructs the monitored reference manifold and source-domain prototypes.

---

## 4. Cross-Domain Evaluation

```
python SRC/evaluate_attackers.py
```

Generates the cross-domain performance and attacker evaluation results reported in the manuscript.

---

## 5. Ablation Study

```
python SRC/evaluate_ablation.py
```

Evaluates the contribution of neighbourhood-density estimation and prototype-aware semantic inference.

---

## 6. Runtime Evaluation

```
python SRC/evaluate_runtime.py
```

Measures the computational overhead of the proposed framework.

---

## 7. Threshold Sensitivity Analysis

```
python SRC/evaluate_threshold_sensitivity.py
```

Evaluates the effect of different operating thresholds on monitored traffic acceptance, Access Failure Rate (AFR), False Positive Rate (FPR), and Domain Generalization Gap (DGG).

---

# Results

The experimental results are organized as follows:

## RESULTS/cross_domain/

Contains the cross-domain performance evaluation reported in Table 4.

## RESULTS/attackers/

Contains attacker accuracy and Effective Attack Success Rate (EASR) results reported in Table 5.

## RESULTS/ablation/

Contains the prototype-aware inference ablation study reported in Table 6.

## RESULTS/runtime/

Contains runtime measurements of the proposed CDG framework.

## RESULTS/threshold_sensitivity/

Contains supplementary threshold-sensitivity experiments supporting the discussion of the security–availability trade-off.

---

# System Requirements

The experiments were conducted on the following platform. Comparable hardware should reproduce the reported results.

- Operating System: Windows 10/11 or Linux
- Python: 3.10+
- PyTorch: 2.x
- CPU: Intel/AMD multi-core processor (8 cores recommended)
- RAM: 16 GB or higher
- GPU: Optional (CUDA is not required; CPU execution is fully supported)

---

# Acknowledgment

The representation learning backbone included in this repository is reproduced from the Swallow framework and serves as the encoder component of the proposed CDG framework. The primary contribution of this work lies in the proposed cross-domain inference mechanism, including prototype-aware latent-space inference, source-calibrated thresholding, the formal characterization of the security–availability trade-off, and comprehensive cross-domain evaluation under controlled structural domain shift.

---

# Contact

This research was conducted at the School of Computer Science and Communication Engineering, Jiangsu University, China.

For research collaboration and academic inquiries, please contact our research group through the official university channels.

For code-related questions or technical issues, please contact:

**5103240323@stmail.ujs.edu.cn**

---

# Citation

If you find this repository useful in your research, please cite:

```bibtex
@article{nartey2026cdg,
  title={CDG: A Cross-Domain Generalization for Robust Website Fingerprinting Defense},
  author={Amanor Nartey, Andrews and Sun, Wenyue and Ametepe, Wolali and Wang, Changda},
  journal={ACM Transactions on Privacy and Security},
  year={2026}
}
```



 
