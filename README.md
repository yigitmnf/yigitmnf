# 👋 Hi, I'm Yiğit Manafi

🎓 **B.Sc. Computer Science & Engineering** at **Sabancı University** · Physics minor · Double major in Industrial Engineering  
📊 GPA **3.84 / 4.00** · Expected graduation 2028 · 📍 Istanbul, Turkey  
🏅 High Honour List and Academic Achievement Scholarship (2024–2025, 2025–2026)

I work where **algorithms**, **high-performance computing** and **software development** meet: C++ and Python on Linux, MPI/OpenMP parallel processing of large sparse data, randomized estimation, and experimental performance analysis.

### 🧩 Why sparse matrices matter

Most large simulations turn into a huge system of equations where each unknown depends on only a few neighbours. Written as a matrix, it is almost all zeros: a **sparse matrix**. Storing and computing only the nonzeros is what lets these simulations fit in memory and finish in time. In the 1-million-row airfoil mesh I use for SparseViz (NACA0015), only **0.0006%** of the entries are nonzero.

- 🌦️ **Weather and climate:** the atmosphere is cut into millions of grid cells, and each cell only talks to the cells next to it.
- ✈️ **Fluid flow and aerodynamics (CFD):** air flowing around a wing or a car is solved on a mesh, one row per mesh point.
- 🏗️ **Structures and materials (FEM):** bridges, buildings and crash tests use stiffness matrices that link each node to its neighbours.
- ⚡ **Circuit simulation:** every component connects only a few nodes, so SPICE-style simulators solve sparse systems.
- 🌐 **Graphs and networks:** web links, social networks and road maps; PageRank is repeated sparse matrix–vector multiplication.
- 🤖 **Machine learning:** recommender systems, graph neural networks and pruned neural networks.
- ⚛️ **Quantum physics and chemistry:** Hamiltonians of many-particle systems are enormous but sparse.

The core step in most of these is **SpMV** (y = A·x), repeated thousands of times. How fast it runs depends on the order of the rows and columns, how the matrix gets from disk into memory, and how the work is split across cores and nodes. That is what I work on: orderings in SparseViz, 400 GB sparse matrix I/O at Simula, and sparse-matrix permanent estimation.

---

## 📄 Publications

- **[The Quick and the Dead: Estimating Sparse-Matrix Permanents with Adaptive Work Filtering](https://arxiv.org/abs/2608.15390)**  
  D. Elbek, **Y. Manafi**, Z. Gürdal, S. Yıldırım, K. Kaya · arXiv:2608.15390 [cs.DS], 2026  
  Under review at **ALENEX 2026** (SIAM Symposium on Algorithm Engineering and Experiments)
- **Survey on Sparse Matrix Ordering Methods** · co-author, in preparation (since 10/2025)

Both with the Sabancı University Parallel Computing Group (Assoc. Prof. Kamer Kaya).

---

## ⭐ Featured: SparseViz

<table>
<tr>
<td width="56%" valign="top">

**[SparseViz](https://github.com/sparcityeu/SparseViz)** is an open-source C++ library that reorders sparse matrices and tensors, draws them, and times CPU/GPU kernels on every ordering.

**What I did**

- 📊 Added **new matrix-quality metrics** to SparseViz's report: envelope, block density, Jaccard similarity, skewness of the nonzero distribution, row block efficiency, and row–column metrics (Envelope R-C, Jaccard Row-Col) that show structural asymmetry after reordering. HTML reports compare matrices and orderings side by side. [See them in the guide](https://sparcityeu.github.io/SparseViz/guide/#metrics).
- 🐛 Bug-fix pull requests for the core library: build paths, matrix / tensor / IO fixes, and keeping local matrices ([#6](https://github.com/sparcityeu/SparseViz/pull/6), [#7](https://github.com/sparcityeu/SparseViz/pull/7), [#8](https://github.com/sparcityeu/SparseViz/pull/8)).
- 📈 Cache-locality analysis: a cache hit plot and features for every matrix and ordering ([#9](https://github.com/sparcityeu/SparseViz/pull/9)).
- 🖥️ Ran and measured everything on the eX3 supercomputer (OpenMP, Slurm, NUMA-aware thread counts).
- 🌐 Built the **[interactive guide website](https://sparcityeu.github.io/SparseViz/guide/)**: how to build, configure, run and extend SparseViz, with animations made from real SparseViz runs ([#10](https://github.com/sparcityeu/SparseViz/pull/10)).

On a matrix with 1 million rows, the RCM ordering made SparseViz's SpMV kernel **3.3× faster** on one thread (31.7 ms → 9.6 ms).

**[→ Open the guide](https://sparcityeu.github.io/SparseViz/guide/)**

</td>
<td width="44%" valign="top" align="center">

<a href="https://sparcityeu.github.io/SparseViz/guide/">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/sparseviz-rcm-dark.gif">
    <img src="assets/sparseviz-rcm-light.gif" width="340" alt="The same sparse matrix in natural order and after RCM reordering, from a real SparseViz run">
  </picture>
</a>

<sub>Real SparseViz output: the same matrix before and after RCM reordering.</sub>

</td>
</tr>
</table>

---

## 🔬 Research

**Simula Research Laboratory**, Oslo · Research Intern, High-Performance Sparse Matrix I/O · *07/2026 – present*  
Supervisor: Assoc. Prof. Johannes Langguth
- A fast, reusable read/write system for sparse matrices of around **400 GB** each.
- Parallel binary reading and CSR construction with **MPI** (across nodes) and **OpenMP** (within nodes) on the **eX3** supercomputer.
- High-performance SpMV on the loaded matrices; benchmarking I/O throughput, memory bandwidth and parallel scaling.

**Sabancı University** · Research Assistant, Sparse Data & Parallel Computing · *08/2025 – present*  
Supervisor: Assoc. Prof. Kamer Kaya
- C++ features for SparseViz (see above) and experimental testing across sparse matrix collections.

**Sabancı University** · Research Course, Quantum Mechanics: Negative Probabilities · *08/2024 – 01/2025*  
Supervisor: Prof. Zafer Gedik

**Sabancı University** · Research Assistant, Materials Science & Nanoengineering (Ceramics) · *02/2024 – 07/2024*  
Supervisor: Prof. Özge Akbulut

---

## 🚀 Projects

**Sparse-Matrix Permanent Estimation** · C++17 / Linux  
Randomized permanent estimators with incremental two-sided minimum-degree ordering, Sinkhorn–Knopp scaling and Dulmage–Mendelsohn support filtering. Built the multi-run statistical test harness (relative error, RSE, effective sample size) on a 60-core Xeon server; evaluated on 50 matrices with exact permanents, real SuiteSparse matrices, and against DeepNIS.

**Time-Series Data Analysis and Prediction** · Python / Jupyter  
398 days of sleep, heart-rate, activity and mood data: exploratory analysis and hypothesis testing, now extended with machine learning for next-day mood prediction.

---

## 🏭 Experience

- **NATO STO IST-TSI-244** · Summer School on Dual-Use Quantum Technologies · *07/2026 – 08/2026*
- **TÜBİTAK BİLGEM YİTAL** · Processor Manufacturing Intern (photolithography, ion implantation, IC fabrication) · *01/2025 – 02/2025*
- **QSB SU – Sabancı Quantum Society** · General Secretary · *07/2024 – present*
- **Toastmasters**, Kocaeli · Leadership Program · *01/2026 – 02/2026*

## 🧪 Teaching

- **Teaching Assistant** · Data Science and Python, Sabancı Summer High School Program · *07/2026 – 09/2026*
- **Teaching Assistant** · Introduction to Python and Quantum Physics, Sabancı Summer High School Program · *07/2025 – 09/2025*
- **Peer Moderator** · Natural Sciences 101/102 and Math 101/102, Sabancı Academic Support Program · *10/2024 – 08/2025*

---

## 🛠️ Skills

- **Programming:** C++, Python, HTML
- **HPC & Parallelism:** MPI, OpenMP, multi-threaded C++, eX3 supercomputer workflows, binary I/O, CSR formats, SpMV, scaling and bottleneck analysis
- **Algorithms:** sparse matrices, permanent estimation, sequential importance sampling, Sinkhorn–Knopp scaling, Dulmage–Mendelsohn decomposition, minimum-degree ordering, bipartite matching, graph algorithms
- **Data:** Jupyter, time-series analysis, exploratory data analysis, hypothesis testing, machine learning basics, benchmarking
- **Tools:** Linux, SSH, Git / GitHub, VS Code, CMake, LaTeX / Overleaf
- **Hardware:** Verilog, LTspice, semiconductor fabrication
- **Languages:** Turkish (native), English (C1), Turkish Sign Language (beginner)

## 📫 Contact

📧 yigit.manafi@sabanciuniv.edu · 💼 [LinkedIn](https://www.linkedin.com/in/yigit-manafi-270745217/) · 📄 [CV](https://drive.google.com/drive/folders/1mnerJ6PkpifUpn3CWkO_pwTN_zCaACoa?usp=sharing)
