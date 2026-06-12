---
title: "zombie programs"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by AtariRaccoon on 2009-11-02
Well, I've put this up before, but now I've finally found out the program that's been clogging up my process and hard drive use.

With using <top> in the terminal, I've found the errant program

update-apt-xapian-index  running under user root and is listed as a Zombie

The problem of course being is that it seems to execute automatically.  From what I found, it's either after I install anything and/or after I give sudo permission (either graphically or in terminal)

So what is this Zombie program doing while I'm doing something else and slowing things down to a craw, or even worse, freezing my sytem fully for a good 20 mins or so?

---

### Post by Locke_99GS on 2009-11-03
A zombie process doesn't do anything, and consumes nearly no resources. When a process calls another process and the child process exits, it sits as a zombie waiting for a *wait()* to be issues to it. It holds the exit information for the process. 

It's nothing to worry about.

---

### Post by AtariRaccoon on 2009-11-03
Good, that's one good thing... 

but still, why does update-apt-xapian-index keep running so often, eat 100% of my CPU resources, cause my hard drive to constantly read/write and lock everything up for 20 mins.  I can't make my mouse cursor move untill whatever it does finishes.  I'm tempted to go root on it and (not delete but) move the program itself to a different folder just to keep it from whatever is trying to run it, though I bet that'll break something.

---

### Post by AtariRaccoon on 2009-11-03
> **AtariRaccoon said:**
> Good, that's one good thing... 

but still, why does update-apt-xapian-index keep running so often, eat 100% of my CPU resources, cause my hard drive to constantly read/write and lock everything up for 20 mins.  I can't make my mouse cursor move untill whatever it does finishes.  I'm tempted to go root on it and (not delete but) move the program itself to a different folder just to keep it from whatever is trying to run it, though I bet that'll break something.

EDIT UPDATE:
I just found out that the program is a recurring problem for many and is STILL attempting to be resolved.  See:
[https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/363695](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/363695)

---

