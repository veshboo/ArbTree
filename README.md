# arbtree

Augmented red-black tree with arbitrary/generic data type.

I have seen augmented red-black tree with `int` such as count of nodes under
subtree. Arbtree accept generic type as an augmentation.

For maintainence of augmented data when the tree modified, arbtree also expects some callback functions from client. They will be called in appropriate point of;

* insert
* delete
* and internal rotate operation.

## Motivational application

My approach to solve a well-known problem,
**Counting inversions in sequence of number**
with time complexity of O(N * log N)

1. tree := some balanced tree data structure
2. for i <- 0 to n-1
    1. number of elements in tree greater than seq[i] // XXX assumed O(log N)
    2. inversions := inversions + count_i
    3. put seq[i] to tree

seems more natural
than a **clever** approach with divide and conquer (and combine)
similar to merge sort.

When implemented with Java's TreeSet, step 2.1. coded like this

```Java
numGreaterThanIthElement = treeSet.tailSet(seq[i]).size();
```

I expected O(N * log N) but it actually it results in O(N * N) because
the `size()` is not O(1). I think subtree size augmented red-black can help
the problem.

And more applications, with generic.

## Previous works

I searched "generic augmented red-black tree", found a lot out there.
So, what is my point? just practice? hmm...
