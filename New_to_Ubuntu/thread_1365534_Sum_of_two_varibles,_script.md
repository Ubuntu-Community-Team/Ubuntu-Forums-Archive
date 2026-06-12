---
title: "Sum of two varibles, script"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-12-27
I'm doing a very simple script and trying to add to variables into one, like this

a=5
b=2
SUM=$a+$b

but can't get it to work.

---

### Post by Methuselah on 2009-12-27
> **SpinningAround said:**
> I'm doing a very simple script and trying to add to variables into one, like this

a=5
b=2
SUM=$a+$b

but can't get it to work.

What language are you writing it in?
I'm guessing you're doing this for educational purpose?

Then open a terminal (applications -> accessories->terminal)
Type **python**

a=5 <enter>
b=2 <enter>
sum=a+b <enter>
print sum <enter>

where <enter> means to hit the enter key.
You should see 7 printed.

Python is one scripting language available in linux.
[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

You probably don't want to do arithmetic in the terminal language (bash) since it's not really meant for that and the syntax isn't nice.

---

### Post by The Secret on 2009-12-27
```
[COLOR=Green]#!/bin/bash[/COLOR]

A=10
B=7
SUM=$(($A+$B))

```

---

### Post by SpinningAround on 2009-12-27
> **The Secret said:**
> ```
[COLOR=Green]#!/bin/bash[/COLOR]

A=10
B=7
SUM=$(($A+$B))

```

Thanks Solved it :)

---

### Post by DaithiF on 2009-12-27
just to note that for bash arithmetic expansion it is not necessary to include the '$' preceding variables within the $(( .. )) construct, so:
```
sum=$((A+B))

```
works equally well.

---

### Post by iMisspell on 2009-12-27
> **DaithiF said:**
> just to note that for bash arithmetic expansion it is not necessary to include the '$' preceding variables within the $(( .. )) construct, so:
Aside from readability and preference, is one way better then the other ?

_

---

### Post by DaithiF on 2009-12-27
alas no, my two reasons for preferring it are (1) readability, and (2) personal preference.

---

