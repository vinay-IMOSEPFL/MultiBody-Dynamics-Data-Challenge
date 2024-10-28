# Multi-Body Dynamics Data Challenge

Welcome to the **Multi-Body Dynamics Data Challenge**! 

This challenge presents a scenario involving multiple masses connected by springs & dampers, fixed at two ends, and falling under gravity. 

Participants will use trajectory data and physics bias/knowledge to learn physically consistent dynamics of this multi-body system and predict the trajectories for various operating conditions and configurations. 
![ezgif-5-4590467762](https://github.com/user-attachments/assets/24d6b39a-7b84-4d1f-9306-ce0ef5597742)

---

## Introduction
In the real world, dynamical systems with complex interactions—such as gear meshing or bearing contacts—are everywhere. Modeling such systems accurately is crucial for applications in engineering, physics, and beyond. 

In this challenge, you will predict:
1. **Future trajectories** based on:
   - Known geometry (number of masses and their connections).
   - Boundary conditions (fixed masses).
   - Observable trajectory data (positions and velocities at each time step).
2. **Forces** between masses (optional).

For models to be effective in real-world applications, they must be able to:
1. **Learn** from scarce data.
2. **Generate physically consistent long rollouts** of trajectories.
3. **Generalize** to changes in configuration of similar systems.
4. **Adapt** to new boundary conditions. 

Your trained simulators will be evaluated on the above mentioned characterstics
 
 **These characterstics can not be obtained from merely data driven modeling and therfore it becomes important to incorporate physics baises**

---

## Training Data

The training dataset consists of simulated trajectories for systems with **4, 5, 6, 7, and 8 masses**. Each mass weighs the same. Each mass is connected to the next one with a link, forming a chain like configuration (see the visualization of the trajectory of each configuration). Each link can produce spring and damping forces due to its deformation and the rate of change of deformation respectively. Additionaly each mass experiences a body force due to gravity (g=9.81 m/s^2). All the positions are in meters and velocities in m/s. 

Each configuration is stored in a separate folder within `train.zip`, organized as:

- `4 masses/`
- `5 masses/`
- `6 masses/`
- `7 masses/`
- `8 masses/`

Each folder contains **2000 CSV files** (one per time step) representing the trajectory data, with position and velocity measurements sampled every 0.01 seconds.

### CSV File Structure

Each CSV file has the following columns:

| posx | posy | velx | vely | mass | boundary_condition |
|------|------|------|------|------|--------------------|
| -8   | 0    | 0    | 0    | 1    | 1                 |
| -4   | 0    | 0    | 0    | 1    | 0                 |
| 0    | 0    | 0    | 0    | 1    | 0                 |
| 4    | 0    | 0    | 0    | 1    | 1                 |

- **`mass`**: A scalar (1) representing equal mass for all components.
- **`boundary_condition`**: A scalar indicating whether a mass has a **fixed (1)** or **free (0)** degree of freedom.

---

## Test Data

The test data consists of two cases (To be only used for evaluations):


1. **New Boundary Condition**: Evaluation on a system with only the middle mass fixed.
2. **Larger Configuration**: Evaluation on a configuration with 12 masses.

   ***(Test data will be released automatically 1 day before submission for plotting error curves.)***

## Trajectory visualizations

Additionally the visualizations of all the training and test trajectories are provided.

---

## Goal

Use the provided trajectory data to develop a model that:
- Can predictfuture trajectories and forces.
- Demonstrates physical consistency in long rollouts.
- Adapts to both new configurations and boundary conditions.

## Evaluation

Your submissions will be evaluated based on:
- Accuracy of the predicted trajectories and forces for long rollouts.
- Consistency of the trajectories with physical laws.
- Generalizability across new configurations and boundary conditions.

Good luck, and happy modeling!

---

## Getting Started

1. **Download the training data** from `train.zip`.
2. **Build your model** using the training trajectories.
3. **Test your model** on the provided test cases.
4. **Submit your results** as per the instructions.

## Resources

- [Learning Physical Dynamics with Graph Networks](https://arxiv.org/abs/1806.01242)
- [Neural Relational Inference for Interacting Systems](https://arxiv.org/pdf/2002.09405v2)

Feel free to reach out with any questions, and we look forward to seeing your innovative solutions!