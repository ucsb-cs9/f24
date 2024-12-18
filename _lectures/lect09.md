---
num: "Lecture 9"
desc: "Stacks, Queues, Deques, Midterm Guide"
ready: true
lecture_date: 2024-10-24 15:30:00.00-7:00
---

Recorded Lecture: [10_24_24](https://drive.google.com/file/d/1XZget22CG9uL-wbEJDhhRg4-heJELz73/view?usp=drive_link)

# Stacks

* We’ve discussed Stack properties in previous lectures, but let’s go through the implementation using Python Lists (implementation from Book)

![Stack.png](Stack.png)

```
# pytests
def test_insertIntoStack():
	s = Stack()
	s.push("There")
	s.push("Hi")
	assert s.size() == 2
	assert s.peek() == "Hi"
	assert s.isEmpty() == False

def test_deleteFromStack():
	s = Stack()
	s.push("There")
	s.push("Hi")
	x = s.pop()
	assert x == "Hi"
	assert s.peek() == "There"
	assert s.size() == 1
	assert s.isEmpty() == False
	y = s.pop()
	assert y == "There"
	assert s.size() == 0
	assert s.isEmpty() == True
```
```
class Stack:
	def __init__(self):
		self.items = []

	def isEmpty(self):
		return self.items == []

	def push(self, item):
		self.items.append(item)

	def pop(self):
		return self.items.pop()

	def peek(self):
		return self.items[len(self.items)-1]

	def size(self):
		return len(self.items)
```

## Big-O analysis

* push() : O(1)
* pop()  : O(1)
* peek() : O(1)

# Queue

* A Queue is linear data structure that has the First In, First Out (FIFO) property
* Analogy: Think about standing in line (no cutting!)
* Similar to a Stack, we can implement a Queue data structure using a Python List

![Queue.png](Queue.png)

```
# pytests
def test_insertIntoQueue():
	q = Queue()
	assert q.isEmpty() == True
	assert q.size() == 0
	q.enqueue("Customer 1")
	q.enqueue("Customer 2")
	assert q.isEmpty() == False
	assert q.size() == 2
    
def test_removeFromQueue():
	q = Queue()
	q.enqueue("Customer 1")
	q.enqueue("Customer 2")
	assert q.dequeue() == "Customer 1"
	assert q.isEmpty() == False
	assert q.size() == 1
	assert q.dequeue() == "Customer 2"
	assert q.isEmpty() == True
	assert q.size() == 0
```
```
class Queue:
	def __init__(self):
		self.items = []

	def isEmpty(self):
		return self.items == []

	def enqueue(self, item):
		self.items.insert(0, item)

	def dequeue(self):
		return self.items.pop()

	def size(self):
		return len(self.items)
```

## Big-O analysis

* enqueue() : O(n)
* dequeue() : O(1)

# Deque

* Pronounced "Deck"
* A Deque is a linear data structure that is more flexible than a stack and a queue
	* A deque is also known as a "double-ended queue"
	* A deque allows us to insert and remove from both ends
		* Unlike a stack where we can only insert and remove from one end (top)
		* And a queue where we can insert in the front and remove from the end of a list
* Similar to a Stack and a Queue, we can implement Deques with a Python List

![Deque.png](Deque.png)

```
# pytests
def test_Deque():
	d = Deque()
	assert d.isEmpty() == True
	assert d.size() == 0
	d.addFront(10)
	d.addFront(20)
	d.addRear(30)
	d.addRear(40)
	assert d.isEmpty() == False
	assert d.size() == 4
	assert d.removeFront() == 20
	assert d.removeRear() == 40
	assert d.isEmpty() == False
	assert d.size() == 2
	assert d.removeRear() == 30
	assert d.removeRear() == 10
	assert d.isEmpty() == True
	assert d.size() == 0
```
```
class Deque:
	def __init__(self):
		self.items = []

	def isEmpty(self):
		return self.items == []

	def addFront(self, item):
		self.items.append(item)

	def addRear(self, item):
		self.items.insert(0, item)

	def removeFront(self):
		return self.items.pop()

	def removeRear(self):
		return self.items.pop(0)

	def size(self):
		return len(self.items)
```

## Big-O analysis

* addFront()    : O(1)
* addRear()     : O(n)
* removeFront() : O(1)
* removeRear()  : O(n)

# Midterm Guide

```
Time:
* In-person (TD-W 1701), Thursday 10/31 3:30pm - 4:45pm PST

Logistics:
* Bring a writing utensil and student ID
* Please write legibly (if we can't read your answer, we can't grade it)
* When leaving the room, you must hand in your exam and present your ID
* Closed book (no notes / book / electronic devices)
* TAs and I will be proctoring the exam. We can answer any CLARIFYING questions

Possible Types of Questions:
* True / False (if False, briefly state why (1 sentence))
* Short Answer - Briefly define / state / describe / ...
* Given some code, write the output / state the O-notation
* Write code satisfying a specification
* Given some partial algorithm, fill in the blank to make it work
* Draw diagrams

Midterm Topics:

Will cover material from the beginning of the class up until the end of week 4's (10/24) lecture
    * Linked Lists won't be asked on the midterm, but will be on the final exam

Python Basics 
- Types
    * I don't expect students to know ALL Python basics, but do expect students to know
    the ones we explicitly covered in lectures and/or assignments
    * int, float, boolean, strings, lists, sets, dictionaries, ...
    * conversion functions (int(), float(), str(), ...)
    * mutable vs. immutable
- Relational / logical operators (==, <, >, <=, >=, and, or, not, ...)
- Python Lists
    * Supporting methods (count, pop, append, insert, ...)
    * List / string slicing [:]
- Understanding under-the-hood functionality of lists and dictionaries
- Strings
    * Supporting methods (replace, split, find, ...)
- Function definitions
- Control Structures (if, else, elif, for, while, ...)

Python Errors / Exceptions
- Runtime vs. Syntax errors
- Exception types (NameError, TypeError, ZeroDivisionError, ...)
- Exception handling
    * try / except / raise
    * Flow of execution
    * Passing exceptions to function / method caller(s) when not handled in try / except
    * Multiple except blocks
    * Handling Exceptions in an Inheritance hierarchy

Object Oriented Programming
- Defining classes and methods
- constructors (defining / initializing default state)
- Shallow vs. Deep equality (overloading __eq__ method)
- Overloading operators (__str__, __add__, __le__, ...)
- Inheritance
    * Know method lookup for inheritance hierarchy
    * implementation for inherited fields / methods
    * overriding inherited methods
    * calling super / base class(es) methods

Testing
- Test Driven Development (TDD)
- pytest

Algorithm Analysis and O-notation
- Know how to derive O-notation for snippets of code

Recursion
- Implementation of recursive functions and O-notation analysis
- Understanding how recursive algorithms are managed by the call stack
- Draw call stack given a recursive function

Binary Search
- Search for items in a SORTED list
- Know the implementation (as covered in textbook / lecture) and O-notation

Linear Data Structures
- Know implementations (as covered in textbook / lecture) and O-notation
for various functionality
    * Stacks, Queues, Deques
```
