# Frozen-lake-DRL
THIS IS THE PROJECT OF THE FROZEN LAKE MURDER FROM THE REINFORCEMENT LEARNING TO FIND THE BEST PATH FOR THE AGENT
Project Overview

This project implements a Reinforcement Learning agent using Q-learning to solve the FrozenLake-v1 environment from Gymnasium. The objective is for the agent to reach the goal without falling into holes.

The agent was trained from scratch without using pre-built RL libraries. Training was limited to 1000 episodes.


Algorithm Used: Q-Learning

Q-learning is a model-free, off-policy reinforcement learning algorithm.

It updates a Q-table using the Temporal Difference (TD) update rule:

Q(s, a) ← Q(s, a) + α [ r + γ max Q(s', a') − Q(s, a) ]


Why Q-learning was chosen:

FrozenLake has a small discrete state space (16 states)

Actions are discrete (4 possible moves)

Tabular learning is efficient and converges within 1000 episodes

No neural network is required for this environment

Exploration was handled using an epsilon-greedy strategy.


Hyperparameters

Learning rate (α): 0.1

Discount factor (γ): 0.99

Initial epsilon: 1.0

Epsilon decay: 0.995

Minimum epsilon: 0.01

Training episodes: 1000

Max steps per episode: 100


Results

Evaluation over 100 test episodes:

Random policy average reward: 0.02
Trained policy average reward: 0.41

The trained agent significantly outperformed the random baseline, demonstrating successful learning.

(If you saved the reward curve plot)


Slippery Mode

Training was conducted with is_slippery=True, meaning the environment is stochastic.
This increases difficulty because actions may not always move the agent in the intended direction.

Performance in slippery mode demonstrates robustness under uncertainty.


Reflection

Changing the learning rate affected convergence stability.
A high learning rate caused unstable Q-value updates and fluctuating performance.
A very low learning rate slowed down learning and required more episodes for improvement.
A moderate value (0.1) provided stable and consistent learning.

The discount factor played a critical role because FrozenLake has sparse rewards.
With a low discount factor, the agent failed to value long-term rewards properly.
A high discount factor (0.99) allowed reward information from the goal to propagate backward through the state space.

Meaningful improvement began after several hundred episodes.
This delay occurred because the agent must randomly reach the goal before reward signals can propagate backward through the Q-table.
Once the agent experienced successful trajectories, performance improved steadily.







