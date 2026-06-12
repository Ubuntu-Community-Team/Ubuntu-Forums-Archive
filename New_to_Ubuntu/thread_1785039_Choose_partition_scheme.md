---
title: "Choose partition scheme"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by Wray on 2011-06-17
I have read much information here and on the man pages and am more confused than ever.

Is there a consensus on how many/what size partitions are optimum.  I am running a 1Tb drive
for Ubuntu and a 1Tb for Windows in a dual boot setup.

In my abysmal ignorance ubuntu is currently installed in a single giant partition .
what is the best utility to partition/repartition a disk?

I do not store audio or Video files on this disk so all partitions can be generously sized 

Can i repartition it without a re install?

---

### Post by pqwoerituytrueiwoq on 2011-06-17
you can resize/move later using gparted on a live cd (resizing is fast moving is SLOW)
but it i s recommend that you back up important data before doing so due to the slight chance of failure
if you are not storing lots of videos/music/a few million pictures you really don't need more than a 40 gb hard drive so it will not matter how big you make them

if you plan on adding a ssd to be a boot drive for ubuntu you should make a separate /tmp and /var partition

just give / 10gb or more and /tmp 4 gb or more /var is probably fine with 2 gb or more
give swap 500mb more than your total ram

---

