The code can be downloaded and directly run after installing the required libraries and the CPLEX optimiser by IBM.

This project implements the Heterogeneous Truck Fleet Optimization (HTFO) problem using two approaches: a Mixed Integer Linear Programming (MILP) formulation solved with CPLEX, and a Genetic Algorithm (GA) tuned with Taguchi’s L16 orthogonal array design. The goal is to minimize the total logistics cost of distributing goods from depots to medical shops and food shops using trucks of different capacities and costs.  

The setup involves three types of trucks, each with a specific capacity, fixed hiring cost, and per-unit delivery cost to medical and food shops. Additional constraints include driver hiring cost, a maximum operational time per trip, and per-shop service times. Demand for each shop is randomly generated between 5 and 14 units, with ten medical shops and ten food shops included in the simulation.  

The CPLEX MILP model defines binary decision variables representing whether a shop is served by a given truck type in a given trip, and whether a truck is active in that trip. Constraints ensure that each shop is served exactly once, truck capacity and trip time limits are respected, and truck activation is tied to actual deliveries. The objective function combines per-unit delivery costs, truck hiring costs, and driver hiring costs, with the solver minimizing the total cost.  

The Genetic Algorithm provides a heuristic solution method. Assignments of shops to truck-trip pairs are represented as chromosomes. The cost function accounts for delivery costs, driver and truck fixed costs, and penalties for violating load and time constraints. Tournament selection, single-point crossover, and random mutation are used to evolve populations over generations.  

Taguchi’s L16 design is used to explore different GA parameter configurations, covering population size, crossover probability, mutation probability, and iteration count. For each configuration, average costs are computed over multiple random seeds. Results are summarized in a table, and the best configuration is selected for a final run on the actual demand data.  

The output of the program compares the optimal solution from CPLEX against the best GA solution, reporting the costs and percentage deviation. This enables evaluating the efficiency and accuracy of the heuristic relative to the exact optimization model.  

This implementation demonstrates both exact and heuristic approaches to solving a real-world vehicle routing and fleet assignment problem. It shows how optimization solvers like CPLEX can guarantee optimality under constraints, while metaheuristics like GA can provide near-optimal solutions more flexibly when scaling to larger or more complex problem instances.  

This work was inspired by the paper *"A mixed integer non-linear programming model and a genetic algorithm for a heterogeneous truck fleet optimization problem"* published in Sādhanā by the Indian Academy of Sciences. The paper can be accessed here: https://www.ias.ac.in/describe/article/sadh/049/0237

