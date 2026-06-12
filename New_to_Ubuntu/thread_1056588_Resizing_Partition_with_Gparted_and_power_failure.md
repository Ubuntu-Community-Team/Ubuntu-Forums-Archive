---
title: "Resizing Partition with Gparted and power failure"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by xeidy on 2009-01-31
Hi,

I was resizing a partition (which was formatted in windows vista) although no OS on it. For I don't know what reason it was talking so long, several hours and i left it unattended and later i found that due to some power failure the computer shutdown.. and I think all the partition tables on the drive are now messed up and corrupted and can't even access anything...

is there a way to get it back to normal? (by saving the data on it as well)


thanks.

---

### Post by caljohnsmith on 2009-02-01
How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
Please post the output, and also for whichever partition you tried to resize, how about trying:
```
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt && ls -l /mnt
```
Replace sdaX with the partition, and please post the output. We can work from there if you want.

---

