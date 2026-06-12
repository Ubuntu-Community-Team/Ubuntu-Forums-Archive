---
title: "Python self learning"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by hdanap on 2011-03-19
Hi guy,

1st i will say, this is not an assignment im readn/learning python on my own.

i came across this problem, i really dont understand it, i know how to write doctest when it come to numbers but i really don't know what the book wants me to do, if i could be channeled in the right direction.

Question:

Write Python code to make each of the following doctests pass:
 """
  >>> type(fruit)
  <type 'str'>
  >>> len(fruit)
  8
  >>> fruit[:3]
  'ram'
"""

am i supposed to write a function or just write code in a script

pls help

my attempt


def word(s):
    """
    >>> type(fruit)
    <type 'str'>
    >>> len(fruit)
    8
    >>> fruit[:3]
    'ram'
    """
    fruit='ramadana'
    if s == fruit:
        x= type(fruit)
        y= len(fruit)
        z= fruit[:3]

---

### Post by ikt on 2011-03-19
> **hdanap said:**
> Hi guy,

1st i will say, this is not an assignment im readn/learning python on my own.

i came across this problem, i really dont understand it, i know how to write doctest when it come to numbers but i really don't know what the book wants me to do, if i could be channeled in the right direction.

Question:

Write Python code to make each of the following doctests pass:
 """
  >>> type(fruit)
  <type 'str'>
  >>> len(fruit)
  8
  >>> fruit[:3]
  'ram'
"""

am i supposed to write a function or just write code in a script

pls help

my attempt


def word(s):
    """
    >>> type(fruit)
    <type 'str'>
    >>> len(fruit)
    8
    >>> fruit[:3]
    'ram'
    """
    fruit='ramadana'
    if s == fruit:
        x= type(fruit)
        y= len(fruit)
        z= fruit[:3]

Probably better asking here:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

fwiw I use the python docs as a reference a lot.

[http://docs.python.org/library/doctest.html](http://docs.python.org/library/doctest.html) should help you :)

---

### Post by hdanap on 2011-03-20
i figured it out, this is the code that did the trick


fruit= 'ramadana'

def word(s):
    """
    >>> type(fruit)
    <type 'str'>
    >>> len(fruit)
    8
    >>> fruit[:3]
    'ram'
    """
    #s=str(s)
    #x=type(s)
    #y=len(s)
    #z=s[:3]
    #print type(s)
    #print len(s)
    #print s[:3]


the commented code could be uncommented and the test still works

---

