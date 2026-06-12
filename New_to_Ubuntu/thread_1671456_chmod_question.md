---
title: "chmod question"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by William S on 2011-01-20
Assume you run the following commandoes from the shell: 

$ cd
$ mkdir folder
$ cd folder
$ chmod 055 ..
$ chmod 055 .
$ ls
$ cd ..
$ cd

As far as I can see this will lock your home directory completely and you can lock it up by using sudo chmod 755, but how do you lock it up without using sudo? Just wondering, because you must have sudo privilgies as soon as you move out of home?

---

### Post by slooksterpsv on 2011-01-20
> **William S said:**
> Assume you run the following commandoes from the shell: 

$ cd
$ mkdir folder
$ cd folder
$ chmod 055 ..
$ chmod 055 .
$ ls
$ cd ..
$ cd

As far as I can see this will lock your home directory completely and you can lock it up by using sudo chmod 755, but how do you lock it up without using sudo? Just wondering, because you must have sudo privilgies as soon as you move out of home?

Like you just want it only accessible by you? If so, just run:

chmod u=wrx,go= <file/folder>

That makes it to where the user (you) can read write and execute, and the group and others cannot do anything with it.

EDIT:

Also, for further clarification, here's how the numbers work:

so when you chmod 055, it changes the permissions like so
chmod u=,go=rx
0 = u , 5 = g, 5 = o
0 = none
1 = x; 2 = w ; 3 = wx
4 = r; 5 = rx; 6 = rw
7 = wrx

Then you can do basic addition to calculate permission numbers: 1 + 2 + 4 = 7 = wrx
4 + 1 = 5 rx
4 + 2 = 6 rw

---

