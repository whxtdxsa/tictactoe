# TicTacToe

Select: Projects
Type: RL

# Overview

---

[https://github.com/whxtdxsa/tictactoe](https://github.com/whxtdxsa/tictactoe)

에이전트가 동작하는 3목 환경을 구현하고, 그 환경에서 최적의 행동를 스스로 찾도록 학습시키는 프로젝트입니다.

![Player vs Trained agent](assets/Screenshot_20260212_173633_Termux.jpg)

Player vs Trained agent

### Previous Future Work

이 프로젝트는 rl-basic프로젝트의 후속 프로젝트이며 이전 프로젝트의 Future Work의 일부를 다룹니다. 

- Apply self-play method.
- Implement another environment.

# Environment

---

## Development Environment

![Android 14 aarch64 without external GPU](assets/AISelect_20260212_180547_Google.jpg)

Android 14 aarch64 without external GPU

## Project Information

| Task Type | Reinforcement |
| --- | --- |
| Data | None |
| Loss |  |
| Optimizer |  |

### Entire Directory Structure

```python
tictactoe
├── README.md
├── main.py
├── play.py
├── q_learning.py
├── table.json
├── tictactoe_world.py
└── utils.py
```

# TicTacToe World

---

## Combinations

- Action Space: 9(height x width)
- State Space: Less than 19,683((Null or Black or White) ^ 9), since there are cases that can not exist such that
    1. Difference between the number of black and white stones is more than 1.
    2. The game was already ended.
- End Points: 8(Row win + Column win + diagonal win)

## Class Design

- Initialization: Define action space, state space, and end points. Run reset method.
- Reset: Initialize the board. Random choose start player
- Step: Update state from action
- Check win: Check the game is ended.
- Visualization: render the board.

# Training Agent

---

## Qlearning Agent

State space is small enough to save all state value in Q-table.

Q-learning algorithm is the kind of TD method which is derived from Bellman Optimality Equation due to off-policy.

![AISelect_20260213_124706_Notion.jpg](assets/AISelect_20260213_124706_Notion.jpg)

![AISelect_20260213_124723_Samsung Notes.jpg](assets/AISelect_20260213_124723_Samsung_Notes.jpg)

## Self-Play

While the agent is trained, the agent and the opponent share the same q-table.

![AISelect_20260213_124629_Samsung Notes.jpg](assets/AISelect_20260213_124629_Samsung_Notes.jpg)

But when the agent selects it’s action in greedy, the opponent selects it’s action in epsilon-greedy.

Thus the as q-table is converging to optimal q-table, the agent has more chance to win from the opponent.

![graph.png](assets/graph.png)

The Graph shows that

1. The greedy agent’s lose rate converges to zero.
2. The greedy agent is defeating the epsilon greedy agent.

That means greedy agent is doing optimal actions.

# Future Work

---

- Reduce state space: There are many board states which correspondance with rotated or fliped state. If those can be considered identity, we can decrease the volume of q-table and reduce time to converge.
