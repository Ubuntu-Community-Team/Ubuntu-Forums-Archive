---
title: "Assigning a Name to a Forked Process"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by senthilmuthiah on 2009-03-27
Dear All:

I have a program in java which I execute using a shell script. I would like to find the process id of this java process immediately after execution so that I could kill it downstream somewhere. I was browsing through pgrep/grep etc., However, the problem here is, since this is a java process the name of the process itself is given as "Java" (which I came to know after using the 'top' command. So, I can't use pgrep/grep/ps since there would be other java processes running in the system which I wouldn't dare to even touch! :frown:

So, here is the problem statement: Either I should find a way by which I could immediately extract the PID of the just initiated or I should assign a 'custom' name for my process.

Any help would be greatly appreciated!

Thanks!

---

### Post by jbrown96 on 2009-03-27
> **senthilmuthiah said:**
> Dear All:

I have a program in java which I execute using a shell script. I would like to find the process id of this java process immediately after execution so that I could kill it downstream somewhere. I was browsing through pgrep/grep etc., However, the problem here is, since this is a java process the name of the process itself is given as "Java" (which I came to know after using the 'top' command. So, I can't use pgrep/grep/ps since there would be other java processes running in the system which I wouldn't dare to even touch! :frown:

So, here is the problem statement: Either I should find a way by which I could immediately extract the PID of the just initiated or I should assign a 'custom' name for my process.

Any help would be greatly appreciated!

Thanks!


I've never used fork in Java, but in C fork() returns the PID of the new process. You run fork(), then check to make sure that it returns >1 (or fail). The integer that it returns is your new PID. You should be able to write it to stdout.

---

### Post by senthilmuthiah on 2009-03-27
Thanks jBrown!

I am actually writing a shell script which initiates a java process.  [I think my usage of the word fork has confused you ]. This is the java process I am interested in and whose PID I would love to know. 

Now what do you think the solution for the problem would be? :confused:

---

### Post by senthilmuthiah on 2009-03-27
Hey Guys! 

Got the solution now:

The PID of the last spawned process is in $! 

So, once I initiate the process I would just store the value of $! in a variable and I would use it to kill it later! :guitar:

Thanks for the support once again!

---

