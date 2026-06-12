---
title: "Creating a swap file - in a new partition?"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by listerdl on 2009-12-30
Happy new year!

I am creating partitons to dual boot windows 7 and ubuntu 9.10

Should I create a partition for the linux swap?

Thanks !!

---

### Post by mechro on 2009-12-30
Yes, you need to create a swap partition. As far as I can make out the current recommendation is for 1 to 2 times RAM size.

---

### Post by stunningman on 2009-12-30
you should make Swap partition twice the size of your physical ram.if your ram is 1 gb then make swap partition of 2gb in harddisk.

---

### Post by Bucky Ball on 2009-12-30
Install Windows 7 and leave the rest of the disk empty. Install Ubuntu and use 'manual partitioning' when you get to that part of the install.

Your Windows 7 partition will be clearly visible (as an NTFS partition). Don't touch it. You need to create:

/
/home
/swap

... at least although you can create whatever partitions you want as well. The ones mentioned are there by default so all you need to do is choose them.

On reboot your Windows should be picked up and an option on the menu. 

For swap 2Gb will do it regardless of your ram. If you have more than that you will never touch the /swap anyhow (it is rarely used and a machine with 4Gb of ram would happily run without it). Good luck.  ;)

---

