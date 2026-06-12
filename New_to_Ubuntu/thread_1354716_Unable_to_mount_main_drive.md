---
title: "Unable to mount main drive"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by maneesh77 on 2009-12-14
I got a toshiba l505

I am unable to mount my drive and unable to access the files.

First I attempted recovery and I got this

mounting /sys on /root/sys failed: no such file or directory
mounting /dev on /root/sys failed: no such file or directory

mounting /proc on /root/ proc failed: no such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg

As dumb as I am I tried booting with a Live cd and accessing it through that but no luck
it said wrong fs type 
bad option, bad superblock on dev/sda5, missing code page, or error program

So is all my data screwed or something can be done??

---

### Post by lavinog on 2009-12-14
Open the partition manger/gparted (the name keeps changing)
right click on the partition, unmount if needed, then click check, then apply (the green checkmark at the top)

---

### Post by m3wolf on 2009-12-14
I would also try ```
# lshw -C volume
``` (as root) and make sure your drive shows up. If not it may be a hardware issues.

---

