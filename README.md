# ✅ To-Do List Application in Java

![Language](https://img.shields.io/badge/Language-Java-orange?style=flat-square)
![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20Windows%20%7C%20macOS-lightgrey?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

A console-based task manager written in Java using object-oriented programming. Supports adding, completing, deleting, and filtering tasks with no external libraries or frameworks.

---

## 📋 Table of Contents

- [Features](#features)
- [Concepts Covered](#concepts-covered)
- [Project Structure](#project-structure)
- [How It Works](#how-it-works)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Sample Output](#sample-output)
- [Limitations](#limitations)

---

## Features

| Feature | Description |
|---|---|
| Add Task | Insert a new task by title |
| View All Tasks | Display all tasks with completion status |
| Mark Complete | Mark a pending task as done |
| Delete Task | Remove a task by its number |
| View Pending | Filter and show only incomplete tasks |
| View Completed | Filter and show only finished tasks |

---

## Concepts Covered

- **Classes & Objects** — `Task` and `TodoList` are separate classes, each with a clear responsibility
- **Encapsulation** — `Task` fields are `private`; accessed only through public getter methods
- **ArrayList** — dynamic list with no fixed size limit; grows and shrinks automatically
- **`toString()` override** — controls how a `Task` prints (`[✓]` or `[ ]`)
- **Scanner** — reads user input from the console with input type validation

---

## Project Structure

```
todo-list-java/
├── Main.java      # Contains Task, TodoList, and Main classes
└── README.md
```

All three classes are in a single file for simplicity. The file compiles and runs with one command.

---

## How It Works

### Class Breakdown

```
┌─────────────────────────────────────────────┐
│  Task                                       │
│  ─────────────────────────────────────────  │
│  - title       : String  (private)          │
│  - isCompleted : boolean (private)          │
│  ─────────────────────────────────────────  │
│  + getTitle()    : String                   │
│  + isCompleted() : boolean                  │
│  + markComplete(): void                     │
│  + toString()   : String  → "[✓] title"     │
└─────────────────────────────────────────────┘

┌─────────────────────────────────────────────┐
│  TodoList                                   │
│  ─────────────────────────────────────────  │
│  - tasks : ArrayList<Task>  (private)       │
│  ─────────────────────────────────────────  │
│  + addTask(title)       : void              │
│  + displayAll()         : void              │
│  + markComplete(index)  : void              │
│  + deleteTask(index)    : void              │
│  + showPending()        : void              │
│  + showCompleted()      : void              │
└─────────────────────────────────────────────┘

┌─────────────────────────────────────────────┐
│  Main                                       │
│  ─────────────────────────────────────────  │
│  + main(args) → menu loop + Scanner input   │
└─────────────────────────────────────────────┘
```

### ArrayList vs Array

| | Array | ArrayList |
|---|---|---|
| Size | Fixed at declaration | Grows/shrinks dynamically |
| Deletion | Manual shift required | `remove(index)` handles it |
| Syntax | `tasks[i]` | `tasks.get(i)` |

This project uses `ArrayList<Task>` so there is no hard limit on the number of tasks.

### Deletion — How `ArrayList.remove()` Works

When a task at index `i` is deleted, Java shifts all elements after it one position left automatically.

```
Before delete at index 1:  ["Buy milk", "Call doctor", "Study Java"]
After  delete at index 1:  ["Buy milk", "Study Java"]
```

No manual shifting needed — unlike C arrays where you write the shift loop yourself.

---

## Getting Started

### Prerequisites

- JDK 8 or higher installed

Check with:
```bash
java -version
```

### Compile

```bash
javac Main.java
```

### Run

```bash
java Main
```

---

## Usage

After running, you will see:

```
================================
      TO-DO LIST APPLICATION
================================

--- MENU ---
1. Add Task
2. View All Tasks
3. Mark Task as Complete
4. Delete Task
5. View Pending Tasks
6. View Completed Tasks
7. Exit
Enter your choice:
```

Enter a number from `1` to `7` and follow the prompts.

---

## Sample Output

### Adding Tasks

```
Enter your choice: 1
Enter task title: Complete Java assignment
Task added: "Complete Java assignment"

Enter your choice: 1
Enter task title: Buy groceries
Task added: "Buy groceries"
```

### View All

```
--- TO-DO LIST ---
1. [ ] Complete Java assignment
2. [ ] Buy groceries
Total tasks: 2
```

### Mark Complete

```
Enter task number to mark complete: 1
Task marked complete: "Complete Java assignment"
```

### View All After Marking

```
--- TO-DO LIST ---
1. [✓] Complete Java assignment
2. [ ] Buy groceries
Total tasks: 2
```

### View Pending Only

```
--- PENDING TASKS ---
2. [ ] Buy groceries
```

### Delete

```
Enter task number to delete: 2
Deleted: "Buy groceries"
```

---

## Limitations

| Limitation | Details |
|---|---|
| No persistence | Tasks are stored in memory only; lost when the program exits |
| No edit | To rename a task, delete it and add a new one |
| Single user | No multi-user or session support |

To add persistence, tasks can be written to and read from a `.txt` or `.csv` file using `FileWriter` and `BufferedReader` — a straightforward next step.
