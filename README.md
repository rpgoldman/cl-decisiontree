# INTRODUCTION
This package provides an implementation of an algorithm that can be used to build a decision tree.


# FEATURES

This package provides the following features

* Classification of multiple classes of instances
* Handling attributes with continuous values (A bit clunky for the timebeing)
* Function for selecting attributes can be modified by changing the *attribute-selection-function* variable

# LOADING

To use this package do

    (asdf:load-system 'decisiontree)
   
To ensure that it is installed properly, use:

    (asdf:test-system "decisiontree")

# TRAINING

To build up a set of instances that could be used for training do the following

    (defparameter <list-variable> nil)

    (push (define-instance <class> <attr-value-pair> <attr-value-pair> ...) <list-variable>)

    (create-classifier <list-variable>)

`create-classifier` returns the root node of the decision tree.

**Notes** 

1. `define-instance` is only suitable for use when typing in static data manually. Under program control, you will want to use `make-training-instance`, instead.
2. In the above `<class>` is a *class label* for the instance, and not a Common Lisp class.


# CLASSIFICATION

To classify an instance use 

    (classify <root-node-of-the-tree> <instance> [<default class value>])

This returns the classification (label) of the instance.  You may supply a default value to be returned if the tree cannot classify the instance.  this defaults to `NIL`.

