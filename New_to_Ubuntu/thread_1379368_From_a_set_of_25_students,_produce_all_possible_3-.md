---
title: "From a set of 25 students, produce all possible 3-students combinations"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by hanzj on 2010-01-12
Hello,

So I have a list of about 25 students that I'm looking at. What  I need to do is to produce a list of ALL possible 3-student combination. What's the quickest way to do this?

So for example, let's say the list of students is:
> 
A
B
C
D
.
.
.
.
.
.
Y


I need to produce a list such as the following:
> 
Possibility 1: A, B, C
Possibility 2: A, B, D
Possibility 3: A, B, E
.
.
.
.
Possibility 400: W, X, Y Is there a way I could automate this? Is there a way a computer can help me? I know I can do this manually, but it would be tedious.

Thanks.

---

### Post by Big_astur on 2010-01-12
If u have access to matlab program u can do it easily:

not with letters but with numbers by typing:

nchoosek(1:25,3)

this will give you as result a matrix with 2300 possibilities (as solution for your problem) where each row has a combo, for example:

     1     2     3
     1     2     4
     1     2     5
     1     2     6
     1     2     7
     1     2     8
     1     2     9
     1     2    10
     1     2    11
     1     2    12
     1     2    13
     1     2    14
     1     2    15
     1     2    16
     1     2    17
     1     2    18
    .
    .
    .
    .

---

### Post by hanzj on 2010-01-12
big-astur, 
i don't have access to matlab. do you? if I pass on to you the short list (it's actually just 19), can You pass on to me the list of combinations? Order is not relevant. In other words, [A, B, C] is the same as [C, B, A]

---

### Post by pythonscript on 2010-01-12
```


import itertools
iterations = itertools.combinations('ABCD',3)
for name in iterations:[INDENT]print name
[/INDENT]
```


will print out every 3 letter combination (order unimportant) of the string 'ABCD.' If you have a list of names, I can help you work out a python script that will read them in from a file and output every possible combination, using this method.

---

### Post by hanzj on 2010-01-12
pythonscript, thanks. the list is the following:
> Australia
Brazil
Canada
China
France
Germany 
Indonesia
Korea
Malaysia
Philippines
Singapore
Spain
Switzerland
Taiwan
Uganda
UK 
UkrainePlease note that order is **NOT** important. This means that:
[UK, Ukraine, Uganda] is the same for my purposes as [Uganda, Ukraine, UK]

---

### Post by pythonscript on 2010-01-12
This should be correct, I believe. I came up with 680 combinations; hopefully this is what you're looking for.

[ATTACH]143431[/ATTACH]

[ATTACH]143432[/ATTACH]

Sorry about the *extremely* messy and backwards python code: my night class is taking an exam, so I'm somewhat distracted.

EDIT:  Also, it's self explanatory from the code, but if you use this script again, it reads in from a file ("names.txt") with each name on its own separate line, and outputs to "comb.txt" which I included. Finally, this code is "officially" windows only, because I quickly coded it on a windows machine and left out a few things.

---

### Post by hanzj on 2010-01-12
Thank you so much!!!! Solved

---

