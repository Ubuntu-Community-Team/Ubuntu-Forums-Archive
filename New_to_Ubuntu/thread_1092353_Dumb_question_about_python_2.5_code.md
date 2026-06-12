---
title: "Dumb question about python 2.5 code"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by N4zgu1 on 2009-03-10
I was trying to learn about python in the Non-Programmers Tutorial For Python by Josh Cogliati

And I found this code:

```
a_var = 10
b_var = 15
e_var = 25
def a_func(a_var):
    print "in a_func a_var = ",a_var
    b_var = 100 + a_var
    d_var = 2*a_var
    print "in a_func b_var = ",b_var
    print "in a_func d_var = ",d_var
    print "in a_func e_var = ",e_var
    return b_var + 10
c_var = a_func(b_var)
print "a_var = ",a_var
print "b_var = ",b_var
print "c_var = ",c_var
print "d_var = ",d_var

```

The output is 

```
in a_func a_var = 15
in a_func b_var = 115
in a_func d_var = 30
in a_func e_var = 25
a_var = 10
b_var = 15
c_var = 125
d_var =
Traceback (innermost last):
  File "separate.py", line 20, in ?
    print "d_var = ",d_var
NameError: d_var

```

My question is: why "in a_func a_var = 15"? . In the code it is never said that "a_var = 15" so where does that 15 comes from?

maybe its a dumb question but Im a noob in programming and I cant understand it

Can somebody explain me?

---

### Post by pyrofreek_9 on 2009-03-10
First off, welcome to the world of programming! :D

On the line:
c_var = a_func(b_var)
the program is calling a_func, and giving it b_var, which is 15.
While the program is running a_func, a_var is actually the value that was passed to it, which in this case was 15!

---

### Post by woodenbrick on 2009-03-10
The names of the variables in this sample are pretty awful, but I think the author of the code was trying to make a point about local variables (variables inside functions) vs. global variables.

If you create a variable inside a function, it wont overwrite the previously defines global variable, instead it hides it.
Maybe a small example might explain better:

```

a = "This is a global variable"

def a_in_function():
    a = "This is a local variable"
    return a

print a
print a_in_function()
print a

```

---

### Post by N4zgu1 on 2009-03-17
Ok, now I understand :) Thank you both.

---

