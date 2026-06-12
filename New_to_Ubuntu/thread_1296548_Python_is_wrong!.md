---
title: "Python is wrong!"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Peacefulpieofdeath on 2009-10-20
Ok this is a python shell (python 2.6.2)

> 
[B]>>> a=71.6
>>> 47-a
-24.599999999999994
>>> 57-a
-14.599999999999994
>>> 60-a
-11.599999999999994
>>> 73-a
1.4000000000000057
>>> 75-a
3.4000000000000057
>>> 75-a
3.4000000000000057
>>> 85-a
13.400000000000006
>>> 87-a
15.400000000000006
>>> 90-a
18.400000000000006
>>> 47-7
[/B]why is it 000000000000006 and stuff... it should not be... i would like the awnser as a 18.4 for example, it should not be off.

---

### Post by ZER01NE1NE on 2009-10-20
This is an Ubuntu forum, not a Python forum. I'd suggest [http://python.org/](http://python.org/) for this question. But it looks like a problem with rounding floating-point numbers in Python.

---

### Post by Daveski on 2009-10-20
"There are four distinct numeric types: plain integers, long integers, floating point numbers, and complex numbers. In addition, Booleans are a subtype of plain integers. Plain integers (also just called integers) are implemented using long in C, which gives them at least 32 bits of precision (sys.maxint is always set to the maximum plain integer value for the current platform, the minimum value is -sys.maxint - 1). Long integers have unlimited precision. Floating point numbers are implemented using double in C. All bets on their precision are off unless you happen to know the machine you are working with."

[http://docs.python.org/library/stdtypes.html](http://docs.python.org/library/stdtypes.html)

---

### Post by Simian Man on 2009-10-20
That's just the deal with IEEE floating point numbers.  There's no way around it short of creating your own number classes.

---

### Post by Can+~ on 2009-10-21
That's actually a problem about the standard used (IEEE) on the FPU (Floating point unit) on every modern processor today.

For precise numbers in python, refer to the Decimal module.

---

