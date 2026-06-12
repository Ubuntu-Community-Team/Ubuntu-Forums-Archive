---
title: "Ubuntu slow runing"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by markomk on 2008-12-23
hi,few days ago my laptop its getting slow :S to run ubuntu need maybe 6-10 minutes any tip how to fix this?

---

### Post by linux_tech on 2008-12-23
For a start, disable a few unnecessary services.
click system > preferences > sessions.
Deselect some services you do not need.
ie.
Tracker
Tracker Applet
Bluetooth manager

---

### Post by Dedoimedo on 2008-12-23
Can you please give us more info?
How did it start? Any special symptoms? Did you install anything?
Dedoimedo

---

### Post by mkvnmtr on 2008-12-23
Another thing to check that is easy to froget. How fill is the hard drive? If it is nearly full it can cause strange problems.

---

### Post by Raynman37 on 2008-12-23
If you go into the terminal and type "top" it will show you the processes that are using your CPU the most.  If you can copy and paste the ones that are using a lot of resources, it may help people figure out what the problem is quicker.

> user@computer:~$ top

---

### Post by billgoldberg on 2008-12-23
If you have been using it for a while, and all of the sudden it's getting slow, it's most likely that you are getting out of disk space.

But just to be sure, open up a terminal and post the output of top.

---

