---
title: "help with this script :("
date: 2010-05-04
forum: New to Ubuntu
---

### Post by makuab on 2010-05-04
GOAL:
Write a program that reads 100 numbers from the user and prints  out the sum.

```
nc = 0
sum = 0


while nc < 100:
    sum = sum + input("please enter another number: ")
```

current code ^
im a bit stuck, i cant figure out how to make it count every time the user enters a number

---

### Post by sisco311 on 2010-05-04
Your loop will stop when nc is greater or equal to 100.  You have to increment nc by 1 in the loop's body.

---

### Post by makuab on 2010-05-04
> **sisco311 said:**
> Your loop will stop when nc is greater or equal to 100.  You have to increment nc by 1 in the loop's body.
how?

---

### Post by jrlii on 2010-05-04
I'm not sure what language you are in, but something to the effect of 

nc = nc+1

after the prompt should do it, just make sure it is inside your while loop.

---

### Post by r-senior on 2010-05-04
Homework? [-X

$ man bash

and search for ARTITHMETIC EVALUATION

Or ...

[http://www.network-theory.co.uk/docs/bashref/ShellArithmetic.html]("http://www.network-theory.co.uk/docs/bashref/ShellArithmetic.html")

---

### Post by sisco311 on 2010-05-04
> **makuab said:**
> how?

In the same way you increment sum by "*input("please enter another number: ")*". :)

[http://docs.python.org/tutorial/introduction.html#numbers](http://docs.python.org/tutorial/introduction.html#numbers)

---

### Post by makuab on 2010-05-04
> **sisco311 said:**
> In the same way you increment sum by "*input("please enter another number: ")*". :)

[http://docs.python.org/tutorial/introduction.html#numbers](http://docs.python.org/tutorial/introduction.html#numbers)
it doesnt work because i dont have a variable for the amount of times the user enters a number.

---

### Post by lisati on 2010-05-04
+1 for including something like **nc=nc+1** in the loop. Another possible refinement, once you've got the basic program structure sorted out, is to have some kind of input validation, e.g. making sure that only numbers are processed and that non-numeric input doesn't trip things up.

---

### Post by makuab on 2010-05-04
> **r-senior said:**
> Homework? [-X

$ man bash

and search for ARTITHMETIC EVALUATION

Or ...

[http://www.network-theory.co.uk/docs/bashref/ShellArithmetic.html](http://www.network-theory.co.uk/docs/bashref/ShellArithmetic.html)

no not homework,

```
nc = 0
sum = 0


while nc < 100:
    sum = sum + input("please enter another number: ")
    nc = nc + 1
print "Your total is", sum

```

works :D thanks guys

---

### Post by makuab on 2010-05-04
> **lisati said:**
> +1 for including something like **nc=nc+1** in the loop. Another possible refinement, once you've got the basic program structure sorted out, is to have some kind of input validation, e.g. making sure that only numbers are processed and that non-numeric input doesn't trip things up.
and how do i do that :O?

---

### Post by sisco311 on 2010-05-04
> **makuab said:**
> and how do i do that :O?

Start with a good tutorial/book and learn the basics:

[thread=333867]How to start programming - guides and links for many languages[/thread]
[post=1984319]Master Programming Tutorial Thread#Why Python?[/post]

---

