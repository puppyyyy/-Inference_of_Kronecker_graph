# Inference-of-Kronecker-Graph
This repository contains code to reproduces the results in the paper "*Analysis and Approximate Inference of
Large and Dense Random Kronecker Graph*".
## About the code
* `code_Analysis_and_ Approximate Inference` contains 
  * **theorem.m**: test for Theorem 2
  * **proposition.m**: test for Proposition 1, 2
  * **corolarry.m**: test for corolarry 1
  * **generate_data.m**: generate a shuffled graph under our model
  * **parameter_inference.m**: the approach proposed (Algorithm 1- Algorithm 3)
  * **realgraph_test.m**: applying our model on realistic graphs
  * **hard_thresholding_test.m**: using Iterative Hard-thresholding (IHT) rather than soft thresholding in Algorithm 3
  * `func` contains 
    * **generate_PK.m** : generate probability matrix using K times Kronecker power
      * Parameters:
        * -P1: Kronecker initiator
        * -K: Iter times
      * Output: Kronecker probility matrix of size $m^K$ by $m^K$
    * **generate_Theta.m**: generate coefficient matrix
      * Parameters: 
        * -K: Iter times
        * -m: Kronecker initiator size
        * -p: Parameter of P1
      * Output: coefficient matrix of size $m^{2K}$ by $m^2$ 
    * **shuffle.m**: using a permutation matrix to shuffle a graph
      * Parameters: 
          * -A: Adjacency matrix of size N by N
          * -shuffle_prop: The shuffle proportion, in other words, the Hamming distance d_H(pi,I) <= shuffle_prop * N
          * -N: The number of nodes
          * -pi_init_array: Vector of size N
       * Output:
          * -Pi_vector: Vector of size $1$ by N meets with Pi(i,pi_vector(i)) = $1$
          * -A_shuffle: The adjacency matrix of the shuffled graph
     * **de_noise.m**: de-noise by constructing an estimator S_approx_shrink of SK
       * Parameters:
         * -A:  Adjacency matrix of size N by N
         * -N: The number of ndoes
         * -bar_p: Constant between 0 and 1
         * -c: The number of choosen singular values
       * Output: an estimator S_approx_shrink of $N$ by $N$
     * **solve_convex_relaxation_func.m**: the implement of Algorithm 3
        * Parameters: 
          * -y_block: Vector of size $N^2$
          * -Theta_block: Coefficient matrix of $N^2}$ by $m^2$
          * -N: The number of nodes
          * -x_init: Initial value of x
          * -lambda: The hyperparameter in soft thresholding
          * -max_iter: Maximum number of iterations
          * -tolerance: Condition for exiting an iteration
        * Output: vector of size $m^2$
