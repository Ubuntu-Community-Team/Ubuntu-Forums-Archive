---
title: "How to set processor affinity to a C program?"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by ajaybidari on 2010-12-30
Hi,
I want to set processor affinity to a C program while running it. It has to be done before the C program starts to run. How to do that?
Please help me..

---

### Post by freak42 on 2010-12-30
According to wikipedia you may use the taskset command line program to do that.

hth

---

### Post by ajaybidari on 2010-12-30
> **freak42 said:**
> According to wikipedia you may use the taskset command line program to do that.

hth

But to use taskset command you need to know the PID. How can we know PID of a process before it starts?

---

### Post by blind2314 on 2010-12-30
You can't.
 
Just curious, why does it need to be set *before* the program starts?

---

### Post by freak42 on 2010-12-30
No, you can launch a new program with it, as described in the manpages.

---

### Post by ajaybidari on 2010-12-30
Actually I am implementing parallel version of game of life using open MPI. I am trying to run it on my core i3 machine. I want to compare the execution times when it runs on 1 and 2 cores resp. so I need to run my program on only core strictly.

---

