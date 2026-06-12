---
title: "Dual-Booting, Partitions and BOOTMGR"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Bendihossan on 2009-03-24
Hey there,

I'm having a little issue with partitions and the Vista bootmgr. I have Ubuntu & Vista dual-booting on my laptop however I re-partitioned my HDD the other night to increase available storage space on one partition (effectively removing space from my Vista partition) and so now Windows complains that the bootmgr is missing when I try to boot it.

I've had a similar problem before where Windows wouldn't boot when I first installed Ubuntu. After much hair pulling and shouting at my laptop I did *eventually* recover it. Done some reading around and apparently the two main solutions are to...
A) Use the Vista Recovery Disk to restore/create a new BootMgr.
B) Use GParted LiveCD to set the BootFlag option to the Vista partition


...or is there a better way of doing this that you clever so-and-so's can suggest? :)

---

### Post by carml on 2009-03-24
Look on google for a recovery disk of Vista,I strongly suggest not to use the original disk that came with your laptop, because it will erase your Vista partition.I say that by personal experience. :)

---

### Post by lindsay7 on 2009-03-24
Download Super Grub. You may have been able to do what you did with it.

---

### Post by Bendihossan on 2009-03-24
Thanks both, I'll have a look at those two and see how it goes.

---

