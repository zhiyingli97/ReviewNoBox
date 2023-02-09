# ReviewNoBox
Review: Practical No-box Adversarial Attacks Against DNNs

## Introudction
+ Reviews background/motivation, problem formulation, method, experiments, and results of the paper “Practical No-box Adversarial Attacks Against DNNs”.
+ We Present post-reading insights and analysis the merit and critics of this work.
+ ML General Adversarial Attack (Python, TensorFlow)

## Files
- Review paper
- Presentation

## Descriptions

Evasion attack, also known as $\ell_p$ evasion attack or adversarial example, is a type of attacks that generate small perturbation to fool a trained ML system (Carlini and Wagner, 2017). The general problem formulation is

$$
\begin{align*}
    \min_\delta & \quad  \ell_\text{atk}(\mathbf{x} + \mathbf{\delta}{;}\mathbf{\theta})\\
    \text{s.t.}  & \quad \Vert\delta\Vert_p \leq \epsilon,
x\end{align*}
$$

where $\mathbf{x}$ is the training data, $\mathbf{\delta}$ is the perturbation, $\theta$ is a model parameter, and $\epsilon$ is the perturbation boundary. Generally, at inference-phase (test time), we use input gradient by back-propagation (bp) $\nabla_\delta l_\text{atk}(\mathbf{x}+\mathbf{\delta}{;}\mathbf{\theta})$  to find the input perturbation.

Based on knowing or not knowing the victim model's parameters $\mathbf{\theta}$, evasion attacks can also be broadly categorized as white-box attacks and black-box attacks. White-box attack directly calculates the gradient, and black-box attack estimates the gradient through queries.

However, it's impractical for many real-world cases when we don't know the victim model's parameters (white-box), or when we are not allowed to query frequently (black-box). Therefore, this paper, \textit{No-Box Attack} is motivated to address these issues: \textit{No-Box Attack} leverages transfer attack to achieve attacks not knowing victim model parameters and not querying the victim model.

The problem formulation of \textit{No-Box Attack} is: ``Assume a benign instance $x_0$ is to be perturbed such that being misclassified into an arbitrary label. We aim to train a substitute discriminative model $\theta_{\text{sub}}$ on a small and thus easily gathered (and labeled) auxiliary dataset $\mathcal{X} := \{\left(x_i, y_i\right)\}_{i=0}^{n-1}$, including the instance $x_0$ to be perturbed.''
