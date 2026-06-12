---
title: "Hard drives being assigned wrong order"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by down_shift on 2010-01-06
Hi I just did a fresh install of ubuntu server and I then added a 2nd HD. 

This HD was then assigned /dev/sda and the drive with my was moved to /dev/sdb. Are there reasons why it's doing this?  I plan on adding a few more drives also. Will it change again?

---

### Post by bodhi.zazen on 2010-01-06
Most likely yes.

This is why it is better to mount by UUID or LABEL.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by louieb on 2010-01-06
a drive assigned to sda , sdb, ... mostly depends on where it is plugged into the mother board. 
It can be affected by the boot order set in BIOS too. Some BIOS allow  a temporary change in the boot order - that can change the a drives sd@ too. 

For the reasons above it is best  to use UUID or a label in assigning mount points. (as suggested by bodhi.zazen) , A partitions label or UUID does not change.  If you use labels it will be up to you to insure no 2 partitons have the same label. If you use UUID just be aware that re-formating a partition will change its UUID.

---

### Post by down_shift on 2010-01-06
If I were to put in 4 HD's and create an array out of them, should I bother giving each drive a label?

---

### Post by louieb on 2010-01-07
labels are given to partitions - not drives.
Have not worked with arrays - can't answer that.

---

