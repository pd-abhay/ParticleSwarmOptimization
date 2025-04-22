What is Particle Swarm Optimization (PSO)?
Particle Swarm Optimization is a population-based stochastic optimization algorithm inspired by the social behavior of birds flocking or fish schooling.

Basic Idea
Imagine a group of birds (particles) flying over a landscape trying to find the best feeding spot (optimal solution). Each bird updates its position by looking at:
* Where it has been (its personal best)
* Where the group found the best spot (global best)

How it Works
Each particle has: 
* A position xi ∈ Rd
* A velocity vi ∈ Rd
* A personal best position pi
* A global best position g

Each iteration, particles update their velocity and position using:

Velocity Update
v(t+1) = w.v(t) + c1.r1(pi - x(t)) + c2.r2(g - x(t))

Position Update
x(t+1) = x(t) + v(t+1)

Where:
w: inertia weight (controls momentum)
c1, c2 : acceleration constants (cognitive and social)
r1, r2 ∼U(0,1): random numbers

Components Explained:
* Inertia: Keeps the particle moving in the same direction
* Cognitive Component: Pulls the particle towards its best-known position
* Social Component: Pulls the particle towards the swarm's best-known position

Algorithm Steps:
* Initialize a swarm of particles randomly
* Evaluate the fitness for each particle
* Update personal bests and global best
* Update velocity and position
* Repeat steps 2–4 until stopping criteria (max iterations or convergence)

Advantages:
* No gradient needed (good for non-differentiable or noisy functions)
* Easy to implement
* Fewer parameters than other metaheuristics

Limitations:
* Can get stuck in local optima
* Sensitive to parameter settings
* Slower in high-dimensional search spaces

Effect of varying key hyperparameters:
* Inertia weight (ω): Set inertia weight ω around 0.6–0.8 to balance speed and exploration. Higher ω (≈0.9) sustains exploration—slower convergence but fewer stalls; lower ω (≈0.4) speeds up convergence but risks early collapse.

* Cognitive (c₁) vs. social (c₂) coefficients: Emphasizing c₁ (personal best) yields more diverse search; emphasizing c₂ (global best) accelerates convergence but can cause swarm to cluster prematurely. Keep cognitive/social coefficients c₁ and c₂ near 1.5 each.

* Inject occasional randomness (e.g. re‑initialize 5–10 % of particles every 30 iterations).

* Critical: Inertia weight is the single most sensitive parameter—controls the exploration–exploitation balance.

Signs of premature convergence:
All particles clump together and stop moving (velocities near zero), and the best score stops improving.
