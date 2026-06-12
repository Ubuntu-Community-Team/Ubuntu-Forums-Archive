---
title: "How to adjust dul boot partiton ?"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by ericstrom on 2009-08-04
I am set up to dual boot Jaunty and XP but getting a little short on hard drive space for Jaunty. I would like to reduce the amount of space allocated on the XP side and move that space over to the Jaunty side (currently the hard drive is set up at about 50:50....and would like to adjust to around 80% jaunty and 20% XP). So, two questions ...

Is there an easy way to do that ? 

Is there a way to tell what the minimum amount of space I should allocate to XP and associated programs ?

---

### Post by oldfred on 2009-08-04
You will want to back-up anything important in XP as modifying partitions has a small chance of damage (usually operator error). 
Clean up your hard drive by housecleaning with the windows disk tool.

Run defrag at least twice. Then you can check you c: drive size, if still too large see what you have installed that you do not use.

Use any liveCD to use Gparted to resize the partitions. The partitions  cannot be mounted when editing partitions.

---

### Post by philcamlin on 2009-08-05
> Use any liveCD to use Gparted to resize the partitions. The partitions  cannot be mounted when editing partitions.

heres how to: ( its a little old but it still works)

[http://www.howtoadvice.com/ResizePartition/](http://www.howtoadvice.com/ResizePartition/)

---

