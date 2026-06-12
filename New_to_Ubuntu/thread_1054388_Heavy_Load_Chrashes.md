---
title: "Heavy Load Chrashes"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by DrakeGis on 2009-01-29
Hi All,
I have a big problem. I'm running several numerical optimization routines in R (with some C code) on my laptop. As you probably know these routines are very demanding (specially on processor time, because the dataset is relatively small, I don't need a lot of memory ). I test each routine and they work correctly. When I want to run, for example 2 of them at the same time, I start each instance of R using 

>> nice -19 R 

thus I can still do something else with my laptop (for example read a pdf file or some news from the web). However, most of the time after a while (maybe about half hour ) the computer freezes and I have to restart it using the power button. I have 10GB of swap and 4GB of RAM, a Turion 64x2. I'm monitoring the SWAP and it never get over 10% of usage (The system load goes to about 12)
Question A: Does any one have any idea why I do have such problem ?


It is interesting the fact that if I avoid the 'nice' command, then the computer is as unresponsive as when I use it.
Question B: Why ? By the way so far it seems that without the 'nice' command there is no crash... if that make sense.


I saw that Ubuntu Studio uses a real time kernel to avoid problems with latency. I wonder if a rt kernel is more suitable for intense computation.
Question C: Should I use a rt kernel ?


Since, in this case, I have 2 instances of R running, I guess I could run one R instance in each processor (I have 2).
Question D: Does any one knows how to run a particular application in a specific processor ? 


Thank you for your ideas/suggestions.

---

### Post by mcduck on 2009-01-29
Negative nice would make the program *less nice*. If you want to keep your system responsive you need to use *higher* nice. -20 is the highest priority, 19 is the lowest.

```
nice +19 R
``` 

Also only root is allowed to use negative nice values. So if you used that command as normal user it had no effect at all.

You don't need to do anything to assign the tasks to different cores, the system balances the load automatically between all available processors/cores.

edit: crashing under heavy load sounds like overheating problem. As the system is a laptop there's little you can do about it apart from trying to get all the dust out of it's air vents and trying to make sure the airflow has as little restrictions as possible.

---

### Post by DrakeGis on 2009-01-29
Thanks, but I'm pretty sure 
nice -19 R 
is the way to do it. You can try to do it yourself, and you can see the results of your suggestion too

$ nice +19 R
nice: +19: No such file or directory
$ nice --19 R
nice: cannot set niceness: Permission denied

In any case, this doesn't solve the problem of the freezing. Neither explains why without the nice the routines run without freezing the machine.

---

