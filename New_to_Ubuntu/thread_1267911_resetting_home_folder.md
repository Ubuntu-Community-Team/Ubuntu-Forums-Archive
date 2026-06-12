---
title: "resetting home folder"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by DarinB on 2009-09-16
i had a grub 17 and i ended up clean installing ubuntu on the system partition. i did manually installed it as root....i have a separate /home hdd and /music hdd, how do i get them to become the actual home and music and to mount automatically, should i clean install it differently??? or how do i get what i have to work ????? at least it boots up and window is still there

---

### Post by tomBorgia on 2009-09-16
You can specify what to mount where on the partitioning bit of the install process... you select the device (e.g. /dev/sdb2) then set a mount point as /home (remember NOT TO FORMAT IT!!!) and it'll automagically set everything up... I've found if you use the same username on the new system it all goes accross smoothly and you'll even have most of your program configs from the .program folders.

If your not going a clean install use gparted (which is the same a the program used in the isntall process to partition the disk) and set the disks up... or you can edit the /etc/fstab file manually... plenty guides for that online ;-)

---

### Post by halitech on 2009-09-16
Info here on using a seperate /home partition

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Since you already have the partition you can probably skip to the section on using it

---

### Post by DarinB on 2009-09-16
please explain i do not need to move anything on a clean install just make sure that the seperate hdd home folder is used pointed to when i boot up?? sorry some stuff is way over my head i think if i learn how to do it i can then clean install karmic which was my main point in buying a new pc with so many hdd's i do have my music hdd now mounting auto but stuck from there

---

### Post by tomBorgia on 2009-09-16
> **halitech said:**
> Info here on using a seperate /home partition

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Since you already have the partition you can probably skip to the section on using it

You won't need to move anything on a clean install, just set up a / (system) partition, a swap partition and then set the mountpoint for your home and music disks as /home and /music (or whatever).

The url in hailtech's post above is a pretty good guide.

---

