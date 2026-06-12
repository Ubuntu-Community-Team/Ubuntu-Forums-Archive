---
title: "Planning to Install ubuntu in Second HDD"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by halovivek on 2009-09-30
Hi 
I am planning to Install in Ubuntu in second hard disk.
My computer is having one physical hard disk with 4 partition each.
Now i am planning to add one more physical hard disk around 500 GB and planning to make another 5 partition in that one.
My question:-
1. How to install ubuntu in second hard disk with 100 GB space for that partition.
2. Or i have to delete all the first Hard disk partition or copy here to do so.

---

### Post by wildman4god on 2009-09-30
When you boot from the live cd, the guided mode (which is default) will let you choose which hard drive you want to use, but it will use the whole hard drive unless you already have an OS on that hard drive, then it will try to dual boot. If you want specifcaly 100 MBs on the separate hard drive then in live cd goto the partition editor in system > administration and manually partition the second hard drive with 100 mb as well as swap space, which should be at least the same amount as your ram preferably more. you could also do this in the installers partitioner but gparted is easier IMHO. Then goto the installer select the second hard drive and manual mode, then select your 100 MB partition as your root (/) and your smaller parition as swap (/swap) then click next and off you go. hope that helps.

---

