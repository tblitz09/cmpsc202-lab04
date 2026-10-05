# Lab 4: Concept Review

This lab reviews the foundational concepts of algorithms and data structures that we have covered in the first half of the course. 

**Instructions:** To complete this lab, you may work in groups, but you must write your solutions yourself. Choose two of the topics below that you need to review and complete the corresponding problems. Where relevant, you are given the answer and must provide the justification as your solution. Once you have completed the lab, push your changes to your forked repository.

**Topics:** asymptotic analysis, data structures, empirical comparison of algorithms, pseudocode, greedy algorithms. 

## Asymptotic Analysis (COMPLETED)

1. Use the rules from lecture 07 to prove that $T(n) = 5 \log n + 7n$ is $\mathcal{O}(n)$.

Drop constants: log n + n
Summing is a max: n
O(n)

2. True/False/Possibly: $T(n)$ is $\mathcal{O}(n^2)$?

**Answer**: Yes

**Justification**: Big O means upper bound so everyting below and slower than it will be true. n^2 is slower than n, so n^2 is a big O of the algorithm. 

3. True/False/Possibly: $T(n)$ is $\Omega(n \log n)$?

**Answer**: No

**Justification**: Omega is a lower bound so everything above and faster than it will be true. n log n is slower than n, so n log n cannot be a omega of the algorithm. 

4. For any algorithm, we can give a trivial lower bound. What is that lower bound?

**Answer**: $\Omega(1)$

**Justification**: Every algorithm will run at least one step, making omega for every algorithm no matter what be omega of 1 or constant time. 

5. Is there a corresponding trivial upper bound? Why or why not?

**Answer**: No

**Justification**: No because there is no definitive amount of steps that the algorithm will make as it always will vary. Lower bound covers the fastest while upper bound covers the slowest. You can't get faster than constant time, but you can get slower forever. 


## Data Structures (BEST FOR MIDTERM)

1. You are programming a robot to navigate a maze. As the robot moves forward, it records each intersection it passes. When it hits a dead end, it needs to retreat to the most recently visited intersection to try a different path.

**Answer**: Stack

**Justification**: Stacks are the easiest data type to delete the value of the last index using pop. This program seems to want to remove from the most recent intersection (value in stack) and go from there. 

2. A server receives a massive influx of data packets from a streaming video application. To prevent the video from skipping or playing out of order on the user's end, the server must process and forward these packets in the exact sequence they were received.

**Answer**: Queue

**Justification**: 

3. An atmospheric monitoring system reads temperature data from 10,000 sequentially numbered sensors (IDs 0 through 9999). Throughout the day, the system needs to constantly update and read the current temperature of randomly selected sensors based on their ID number to build localized weather maps.

**Answer**: Array

**Justification**: 

4. You are building a lightweight syntax checker for a code editor. Its sole job is to scan a document and ensure that every opened parenthesis `(`, bracket `[`, and brace `{` is matched with its corresponding closing character in the correct nested order.

**Answer**: Stack

**Justification**:

## Empirical Comparison of Algorithms (BEST FOR MIDTERM) (COMPLETED)

1. A student is benchmarking an algorithm that takes a list as its input. They run it on progressively larger randomly generated lists, doubling the number of elements ($n$) and record the following execution times:

- $n = 1000$: 0.12 seconds
- $n = 2000$: 0.94 seconds
- $n = 4000$: 7.61 seconds
- $n = 8000$: 60.85 seconds

 Based on this empirical data, what is the most likely asymptotic time complexity of the algorithm? **Hint**: Calculate the doubling ratio between each pair of consecutive runs.

 **Answer**: Cubic time complexity, $\mathcal{O}(n^3)$

**Justification**: So the execution time when doubling the number of elements is equal to multiplying the previous by 8 (.94/.12, 7.61/.94, and 60.85/7.61 are all around 8). 2^3 = 8, so we know the running time is close to the equation of n^3 because that 2 represents the doubling. Making it big O of n^3. 

 2. Two students write separate algorithms to compute a metric over an array of 10 million integers. Both algorithms perform exactly one mathematical operation per element, meaning both have a theoretical time complexity of $O(N)$. However, during benchmarking, Algorithm A consistently runs 15x faster than Algorithm B. Why might theoretical Big-O analysis fail to predict this massive performance gap? 

**Answer**: Big-O is the asymtotic upper bound meaning that it is upper bound for the best running time of the worst case. The two alogrithms may share the same upper bound, but may not have the same actual running time. Being an upper bound does not mean that the running time will be perfectly represented by Big O, but instead what the best running time could be. 

 3. Scenario: To measure the running time of algorithms for an empirical comparison, a developer writes the following benchmarking script:

```python
import time

large_array = [i for i in range(1000000)]
start = time.time()
myAlg(large_array)
end = time.time()

print("Time:", end - start)
```

They run this script exactly once for each algorithm on their laptop while streaming a movie in the background. Identify at least three distinct methodological flaws in this benchmarking setup that make the results unreliable.

**Answer**: First and most importatnly, they only run the script once meaning that the running time will only be one value instead of being represented by an average of many different runs to be more exact on what the running time could be. Second, they are running the script on a laptop only. Different computers could have faster loading and execution times which can change running time. Lastly, a movie is streaming in the background which is taking memory and execution power from the computer to help load this algorithm. All these add up to make the times less reliable. 

## Pseudocode (COMPLETED)

1. Analyze the exact number of times the `do_work()` function is called in the following pseudocode, assuming $N \ge 1$.

```
count = 0
for i = 1 to N do
    for j = i to N do
        do_work()
```

Write a closed-form expression for the number of times `do_work()` is called in terms of $N$.
do_work() will be called N^2 times. A for loop from 1 to N will run N times and a nested loop will multiply itself to the begining loop. Calling the do_work() function N^2 times.

2. Analyze the exact number of times the `do_work()` function is called in the following pseudocode, assuming $N \ge 1$.

```
i = N
while i > 0:
    for j = 1 to i:
        do_work()
    i = floor(i / 2)
```

If $N=16$, how many times is `do_work()` called?

**Answer**: 31

**Justification**: So the algorithm assigns i to the N value that is given. Then while this i value is above 0 it will run a for loop that runs from 1 to i which in this case is 16. This will run do work 16 times then assign i the value of half of i. In this case, i will become 8. Then the for loop will run 8 more times, with a total of 24 do work calls. i will become 4 and run the for loop 4 times, making the total 28. i will become 2, run the for loop 2 times, with a total of 30 calls. i will become 1 and run the loop 1 time, making the total 31 calls. i will become 0 and the while loop will stop. Making 31 calls to do work. 

## Greedy Algorithms

You are organizing a film festival but only have access to a single screen. You are given a list of $n$ films, each with a specific `start_time` and `end_time`. You want to screen the maximum number of films possible.

Consider the following three greedy strategies:

- **Shortest First**: Always pick the film with the shortest duration (that doesn't conflict with already chosen films).
- **Earliest Start**: Always pick the film that starts the earliest (that doesn't conflict).
- **Earliest Finish**: Always pick the film that finishes the earliest (that doesn't conflict).

Which of these three strategies guarantees an optimal solution (maximum number of films)? For the two strategies that fail, provide a counter-example (a small set of film times) where the greedy choice results in a sub-optimal schedule.

**Answer**: The earliest finish strategy guarantees an optimal solution.

**Justification**: