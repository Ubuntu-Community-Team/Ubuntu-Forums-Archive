---
title: "What is a segmentation error?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Herber on 2009-05-18
I have been trying to Install the 9.4 variant of UBUNTU to a machine for some time now.  I Decided that the machine was perhaps too old to accept the full Ubuntu so I tried Xubuntu.  But I get the same problem:  During the progress bar as the installation begins the progress stops, and the system seems to hang for several minutes before I get a black screen with whit lettering saying "segmentation" error or Fault.  I think that this is when the drivers are being installed (although this is largely a guess on my part).  
  The machine has 380MB Ram and a 300 MHz processor (inspiron 7000 laptop) and has run all previous versions of Ubuntu since 6.1 without problems.

---

### Post by sim-value on 2009-05-18
Have you made the MD5 check of the cd ?

Segmentation Fault is a Memory error Usually happens cause of bad programming

---

### Post by eldragon on 2009-05-18
> **sim-value said:**
> Have you made the MD5 check of the cd ?

Segmentation Fault is a Memory error Usually happens cause of bad programming

and ram erorrs, or cd defects...

it usually means the program tried to access a segment of memory not belonging to it. the kernel prevents it and kills the offending program

---

### Post by Herber on 2009-05-18
thanks for the interest.  I have used a known good disk because I have used the disk to install on another computer, and I did the check sum.  The problem seems to happen in relation to 9.4, weather I use the Text based install, the upgrade option, or the graphical installation mode.  In the graphical install the live disk will hang while trying to boot, with the text based install and the upgrade option I can do the install, but on boot the system hangs during the progress bar while trying to boot.  I can install earlier versions on Ubuntu/Xubuntu (ie 8.10 in Ubuntu, 8.4 in Xubuntu)without problem.

---

### Post by Herber on 2009-08-22
THe problem I was having was solved by this post.

[http://ubuntuforums.org/showthread.php?t=1194565&highlight=Dell+blacklist+Radio_maestro](http://ubuntuforums.org/showthread.php?t=1194565&highlight=Dell+blacklist+Radio_maestro)

I hope this can help someone else I am now a 9.4 user!

---

