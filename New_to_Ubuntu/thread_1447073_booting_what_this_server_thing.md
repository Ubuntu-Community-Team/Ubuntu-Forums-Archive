---
title: "booting? what this server thing?"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by littlboz on 2010-04-04
okay, so everything is running beautifully on my Ubuntu but when I start  my computer it has 
 
 Ubuntu generic 2.6.31-20
 Ubuntu server 2.6.31-14
 Ubuntu generic 2.6.31-14
 
 What are these they also each have a safe mode to boot from? I am  booting with the first one.
 
 It also has my other windows XP operating system and another one which I  think is the system back up (I think).
 
 I think the three ubuntus are the partitions that I made when I  installed. one was a swap, another was home, and the other was root.

I am wondering which is which and why I would need to go into the other 2  (the others besides the first).

oo and which one is my home and which one is the root?

---

### Post by Choragos on 2010-04-04
Every time you install or upgrade your Ubuntu, the old kernels are still there.  Notice that you have generic  2.6.31-20 and 2.6.31.14.  This is so that if the upgrade crashes or otherwise sucks, you can boot into the old one.  The server seems to indicate you installed the server software as well.

Basically, you just need to boot into the latest generic listed.  This will probably be the first and default choice.  Nothing to worry about.  If these become too cumbersome, you can uninstall them using the synaptic package manager (just be very careful).

---

