[<< Back to Home](../../index.md)

# Notes

## CH 1: Introduction

1. `map` and `reduce` can be combined to execute "transform and consolidate" workflows.
1. `map` is one-to-one transformation, `reduce` is one-to-any transformation (Assembling/Consolidating)
1. Shopify has 10PB of MP3s would take 20,000 years to play.
1. Hadoop distributes both data storage and processing.
1. Hadoop provides a layer of abstraction on top of DFS that allows us to run highly // MR jobs
1. Spark does more of its work in memory instead of by writing to files.
1. AWS Elastic MR (EMR)
1. AWS approach

## CH 2: Map and // Computing

1. map is powerful lazy function, instructions are saved for evaluating the function and runs only when we ask for the value.
1. Python `map` converts sequence of inputs --> instructions for computing
1. get #cpus

```python
import os
print(os.cpu_count())
```

### 2.1 Pickling

1. Python's version of object serialization or marshalling
1. it allows moving code objects(functions+data) across machines.
1. `pickle-work-pickle` approach
1. `multiprocessing` module does not pickle `1. Lambda functions, 2. Nested functions, 3. Nested classes`
1. Use third party library for them (like `pathos`)

### 2.2 Order and //ization

## CH 3: Function pipelines

- helper functions and function chains
- use `compose` [Write in reverse order] and `pipe` from `toolz` (decode hacker messages)

## CH 4: Lazy Workflows

- Lazy and Eager evaluation
- Some lazy functions:  
  --> `filter`  
  --> `zip`  
  --> `iglob`: Lazy way to query filesystems

- Important other functions: `filterfalse`, `keyfilter`, `valfilter` and `itemfilter`

#### 4.1 Iterators

- **Iterators** can move through in sequence **Generators** generate sequences
- we can loop over items of an iterator, or we can map a function across one.
- The process is defined by method `__iter__()` and returns object with a `__next__()` method.

- All our lazy friends are one-way streets; once we call next. item returned to us is removed from sequence.
- Iterators are not for by-hand inspection, they are meant for processing big data. They use less memory and offer better performance.

#### 4.2 Generators

- generates sequence and don't hold them in memory.
- define function with `yeild` statement.
- Use generator expressions if possible.

```python
from itertools import count, islice
# Generator Expression
evens = (i*2 for i in count()) # Generator
# Create chunks of the evens generator
islice(evens, 5, 10) # Generator
```

#### 4.3 Lazily processing large dataset

- Finding author of Poem problem.
