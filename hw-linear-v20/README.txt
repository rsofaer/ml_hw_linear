MLPR Homework: Linear Models

The purpose of this assignment is to implement and understand
the basic learning algorithms for linear classifiers.

Your assignment should be sent by email to the TA
- Send your email in plain text (no msword, no html, no pdf).
- late submissions will be penalized.
- you must implement the code by yourself, but 
  you may discuss your results with other students.
- Include your source code as attachment(s).


++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
The following learning algorithms must be implemented
with ridge (L2) regularization:
- the perceptron algorithm
- direct solution of linear regression
- on-line (stochastic) linear regression
- on-line (stochastic) logistic regression

the dataset with which to test the algorithm is called
uci-spambase. It is a two-class classification problems from
the UC Irvine machine learning dataset repository
(http://www.ics.uci.edu/~mlearn/MLRepository.html):

The dataset contains 4601 samples with 57 variables.
The task is to predict whether an email message is spam
or not (see ../datasets/uci-spambase/spambase.names for details).

The data is available in comma-separated-value format
in the file ../datasets/uci-spambase/spambase.data

The Lush code to read the data and format it is provided.

You simply need to edit the file main.lsh and implement
the algorithms. The best design is probably to write
a linear classifier class, with different methods (or
sub-classes) for the various learning algorithms.

Your training code should
  1. start by computing and displaying the loss and 
     the error rate on the training set and test set.
  2. make a training pass over the training set
  3. compute and display the loss and the error 
     rate on the training set and test set.
  4. iterate to 2 until convergence (pick a criterion).

________________________________________________________________
Things you might need to know about lush:

- scalars are zero-dim arrays. If 's' is a scalar '(s)' returns 
  its content (as a number), and '(s 45)' writes 45 in it.
- dot-product: '(idx-dot v1 v2)' returns a scalar
- outer product '(idx-m1extm1 v1 v2)' returns the outer 
  product of 'v1' by 'v2'.
- cumulative outer product '(idx-m1extm1acc v1 v2 a)' accumulate 
  outer product of 'v1' and 'v2' into matrix 'a'.
- tanh function: '(tanh x)' 
- sign function: '(sgn x)'
- solving a linear system ax=b: '(solve-hh a b)' or '(solver-lu a b)'.
- looping over the rows of two matrices 'x' and 'y' simultaneously: 
   '(idx-bloop ((rx x) (ry y)) (your-code-goes-here rx ry))'
  variable 'rx' will be equal to each row of 'x' in succession,
  and 'ry' to each row of 'y' (or element if 'y' is a vector).
- printing: '(printf "%g\n" some-number)' works like its C counterpart
- directing outputs to a file: 
  '(writing "some-file" .... (printf "%g\n" some-number) ...)'


________________________________________________________________
QUESTIONS:

1 - implement:
    a - the perceptron learning algorithm
    b - linear regression with square loss 
        trained with stochastic gradient descent
    c - linear regression with square loss trained
        by direct solution of a linear system.
    d - the logistic regression algorithm trained 
        with stochastic gradient descent


    REMEMBER TO TAKE CARE OF THE BIAS PARAMETER!!!
    The bias is implemented a separate parameter,
    don't forget to update it in your code.

     ==> include your code as attachment.

2 - Experiments with the Spambase dataset

      - set the training set size to 1000 
        and the test set size to 1000.
      - The stochastic gradient method for linear regression
        and logistic regression require you to find good 
        values for the learning rate (the step size, eta).
    a - what learning rates will cause linear regression
        and logistic regression to diverge?
    b - what learning rate for linear regression 
        and logistic regression that produce
 	the fastest convergence?
    c - implement a stopping criterion that 
        detects convergence.

    d - train logistic regression with 10, 30, 100, 500, 
        and 3000 training samples, and 1000 test samples. 
        for each size of training set, provide:
        - the final value of the average loss, and 
	  the classification errors on the training 
	  set and the test set
        - the value of the learning rate used
        - the number of iterations performed

    e - what is the asymptotic value of the training/test 
        error for very large training sets?

3 - L2 and L1 regularization
    When the training set size is small, it is often helpful
    to add a regularization term to the loss function.
    The most popular ones are:
    L2 norm:   alpha*||W||^2    (aka "ridge regression")
    L1 norm:   beta*[ SUM_i |W_i| ]  (aka "LASSO")

    a - how is the linear regression with direct solution
        modified by the addition of an L2 regularizer.
    b - Modify you logistic regression code to add the
        L2 and L1 regularizers to the cost function.
	Can you improve the performance on the test set
	for training set sizes of 10, 30 and 100.
	What value of alpha nad beta give the best results?
