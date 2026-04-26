
# Scheduling
### Core Concepts

- **Scheduling Algorithm**: A method to select a process from the **ready queue** (which resides in RAM) to execute on the CPU.  
- **Ready Queue**: Contains multiple processes waiting to be executed, held in RAM.  
- **Uni-processor System**: Only one CPU exists, so only one process can execute at a time.

---

### Types of Scheduling Algorithms

| Type            | Description                                                                                     | Key Feature                                    |
|-----------------|-------------------------------------------------------------------------------------------------|------------------------------------------------|
| **Pre-emptive** | A running process can be interrupted and moved back to the ready queue before completion.       | Allows CPU to switch between processes during execution (time sharing).            |
| **Non Pre-emptive** | A running process executes fully without being interrupted until completion (burst time).     | Process runs to completion once started on CPU. |

---

### Explanation of Pre-emptive Scheduling

- A process currently running on the CPU may be **pre-empted** (interrupted) and placed back into the ready queue.
- Reasons for pre-emption include:
  - **Time Quantum**: CPU allocates fixed small time slices (e.g., 2 seconds) to each process to ensure fairness.
  - **Priority**: Higher-priority processes may pre-empt lower-priority ones.
  - **Shorter Job First**: Processes requiring less execution time may be prioritized to improve efficiency.

---

### Example for Understanding Pre-emptive vs Non Pre-emptive

- **Non Pre-emptive**: Like a teacher answering *all 5 questions* of one student before moving to the next.
- **Pre-emptive**: Teacher answers *2 questions* per student, then moves to the next student, cycling through all students to ensure fairness and responsiveness.

---

### Advantages of Pre-emptive Scheduling

- **Responsiveness**: All processes get CPU time quickly, preventing starvation of later processes.
- **Priority Handling**: High-priority processes can interrupt lower-priority ones to be executed sooner.

---

### Scheduling Algorithms Mentioned

| Algorithm                           | Type             | Description / Use Case                                         | Notes                          |
|-----------------------------------|------------------|---------------------------------------------------------------|--------------------------------|
| **SRTF (Shortest Remaining Time First)** | Pre-emptive      | Process with the least remaining burst time is executed first | Common in exams & practical use |
| **Round Robin**                   | Pre-emptive      | Processes executed in cyclic order with fixed time quantum    | Ensures fairness & responsiveness |
| **LRTF (Longest Remaining Time First)** | Pre-emptive      | Process with longest remaining time is executed first          | Less common but relevant        |
| **Priority Scheduling**           | Both             | Execution order based on priority values                       | Mostly pre-emptive, sometimes non-pre-emptive |
| **FCFS (First Come First Serve)** | Non Pre-emptive  | Processes executed in arrival order                            | Simple but can cause long wait times |
| **Shortest Job First (SJF)**      | Non Pre-emptive  | Process with smallest burst time executed first                | Improves average waiting time   |
| **Longest Job First**             | Non Pre-emptive  | Process with longest burst time executed first                 | Less common                    |
| **Highest Response Ratio Next**  | Non Pre-emptive  | Uses formula involving waiting and burst time to prioritize    | Balances waiting time and burst time |
| **Multi-level Queue & Feedback Queues** | Both             | Multiple queues with different priorities and feedback        | Useful for complex systems      |

---

### Important Notes

- **Pre-emptive scheduling** allows interruption of running processes to improve system responsiveness and handle priorities effectively.
- **Non pre-emptive scheduling** guarantees process completion once started but may cause delays for other processes.
- **Time Quantum** is a crucial concept in pre-emptive scheduling, especially in **Round Robin** algorithms.
- Priority can dynamically influence scheduling decisions, often leading to pre-emption.
- Scheduling algorithms like **SRTF** and **Round Robin** are frequently highlighted in academic exams like GATE and UGC NET.

---

### Key Insights

- Scheduling algorithms are essential for **efficient CPU utilization** in a multi-process environment.
- The choice between pre-emptive and non pre-emptive scheduling impacts **system responsiveness**, **fairness**, and **process prioritization**.
- **Time quantum** and **priority-based pre-emption** are primary mechanisms for process switching in pre-emptive scheduling.
- Understanding these algorithms is crucial for solving related numerical problems in academic contexts.

---

### Summary Table: Pre-emptive vs Non Pre-emptive Scheduling

| Feature                | Pre-emptive                           | Non Pre-emptive                        |
|------------------------|-------------------------------------|--------------------------------------|
| Process interruption   | Allowed                             | Not allowed                          |
| Process execution time | May be divided into multiple CPU bursts | Runs until completion (burst time)  |
| Responsiveness         | Higher                             | Lower                                |
| Complexity             | More complex due to context switching | Simpler                             |
| Examples               | Round Robin, SRTF, Priority (mostly) | FCFS, SJF, Priority (sometimes)     |

---
### Core Concepts and Definitions

| Term              | Definition                                                                                  | Nature (Point/Duration)                       | Example/Explanation                                       |
|-------------------|---------------------------------------------------------------------------------------------|----------------------------------------------|-----------------------------------------------------------|
| **Arrival Time**  | The time at which a process enters the ready queue (ready state).                           | Point of time                                | Entering the bank at 11:00 AM.                             |
| **Burst Time**    | The actual CPU time required by a process to execute.                                      | Duration                                     | Time to deposit money, e.g., 15 minutes.                   |
| **Completion Time** | The time at which the process finishes execution.                                         | Point of time                                | Leaving the bank at 12:00 PM.                              |
| **Turnaround Time** | Total time spent by the process in the system (Completion Time - Arrival Time).           | Duration                                     | 12:00 PM - 11:00 AM = 1 hour (60 minutes).                |
| **Waiting Time**  | Time the process spends waiting in the ready queue or for resources (Turnaround Time - Burst Time). | Duration                                     | 60 mins - 15 mins = 45 mins waiting in bank queue.        |
| **Response Time** | Time from process arrival to first time CPU is allocated (First CPU service time - Arrival Time). | Duration                                     | Time spent waiting before first communication with clerk. |

---

### Detailed Explanation of Each Time

- **Arrival Time**: Marks the exact moment a process arrives and enters the ready queue. It is a **point in time**, not a duration.

- **Burst Time**: Represents the actual execution time a process requires on the CPU. It is a **duration**, dependent on CPU processing speed or workload.

- **Completion Time**: The point in time when the process finishes execution. Unlike burst time, this is not a duration but a timestamp.

- **Turnaround Time**: Calculated as

  $$
  \text{Turnaround Time} = \text{Completion Time} - \text{Arrival Time}
  $$

  It indicates the total time a process spends in the system, including both execution and waiting.

- **Waiting Time**: The time a process spends waiting in the queue or idle due to interruptions. It is calculated as

  $$
  \text{Waiting Time} = \text{Turnaround Time} - \text{Burst Time}
  $$

  The bank analogy clarifies this: although depositing should take 15 mins, the total time in the bank was 60 mins, so 45 mins were spent waiting (e.g., queue, form filling, interruptions).

- **Response Time**: Measures how quickly a process starts receiving CPU attention after arrival, calculated as

  $$
  \text{Response Time} = \text{Time CPU first allocated} - \text{Arrival Time}
  $$

  This reflects the delay before a process begins execution, such as waiting in queue before the clerk starts processing the form.

---

### Additional Insights

- **Burst Time** depends on CPU capabilities and process needs, and can sometimes be known in advance (e.g., process predicts it will take 15 minutes).

- **Waiting Time** often occurs due to I/O operations or interruptions. For instance, a process may pause CPU execution to perform I/O tasks (e.g., reading from disk, printer/scanner usage), causing additional waiting time.

- There are two types of processes based on CPU usage:
  - **CPU-bound processes**: Require significant CPU time continuously.
  - **I/O-bound processes**: Frequently wait for input/output operations, leading to more waiting time.

- Understanding these times is crucial before attempting to solve numerical problems involving various CPU scheduling algorithms such as FCFS, SJF, Round Robin, etc.

---

### Summary Table: Relationships Between Times

| Formula                          | Meaning                                         |
|---------------------------------|------------------------------------------------|
| $$ \text{Turnaround Time} = \text{Completion Time} - \text{Arrival Time} $$ | Total time in system                             |
| $$ \text{Waiting Time} = \text{Turnaround Time} - \text{Burst Time} $$    | Time spent waiting (not executing)               |
| $$ \text{Response Time} = \text{Time CPU first allocated} - \text{Arrival Time} $$ | Delay before process starts execution            |

---

### Key Takeaways

- **Arrival and Completion times are points in time**, while **Burst, Turnaround, Waiting, and Response times are durations**.
- The **waiting time** is crucial for evaluating process delays due to queues or interruptions.
- The **response time** indicates system responsiveness from process arrival to first CPU allocation.
- These concepts form the building blocks for analyzing and solving CPU scheduling problems in exams.
- Clear understanding aids in correctly applying scheduling algorithms to compute these times.

---
