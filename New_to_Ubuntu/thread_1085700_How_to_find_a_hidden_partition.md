---
title: "How to find a hidden partition"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Martynwills on 2009-03-03
I loaded Ubuntu 8.10 a few days ago and it didn't give me any option but to partition the whole disk. Fair enough I thought - take the plunge and fully abandon Microsoft. 

I thought that's what I had done, but I have just noticed that Ubuntu only lists my hard drive as being 200Gb in size whereas I know its total size is 250Gb

How can I find out what the missing 50Gb of hard disk is doing?

Ubuntu boots automatically when I turn the laptop on - there is no option for a different partition and no mention of microsoft or windows.

Suggestions appreciated

:confused::confused::confused:

---

### Post by taurus on 2009-03-03
Open a terminal and post the outputs of these commands, running one at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h 
free -m
```

---

### Post by gandaran on 2009-03-03
install gparted (sudo apt-get install gparted), then you can have a look at the whole disk and find what's missing

---

### Post by Martynwills on 2009-03-03
> **taurus said:**
> Open a terminal and post the outputs of these commands, running one at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h 
free -m
```

> sudo fdisk -l
```
[sudo] password for martyn: 
```
(it won´t let me enter any password though...)

> cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e94b1cd3-1844-442a-a698-f31049c80b6a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2a515f44-a5a1-4196-94d9-89f0ff2bd63a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

> df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             221G  3.7G  206G   2% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  108K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  104K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile

```

> free -m
```
  total       used       free     shared    buffers     cached
Mem:          3038        540       2498          0         19        241
-/+ buffers/cache:        279       2758
Swap:         8895          0       8895

```

translation please!!

---

### Post by taurus on 2009-03-03
You can enter your password.  It's just that the cursor doesn't move so make sure you type in the right one and hit Return.

---

### Post by philinux on 2009-03-03
Just enter your password. You wont see it.

---

### Post by Martynwills on 2009-03-03
cheers

> fdisk -l


```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3204370a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29267   235087146   83  Linux
/dev/sda2           29268       30401     9108855    5  Extended
/dev/sda5           29268       30401     9108823+  82  Linux swap / Solaris

```

---

### Post by Bölvaður on 2009-03-03
> **Martynwills said:**
> .... 200Gb in size whereas I know its total size is 250Gb

Recheck and see if it isn't 200 GiB and 250 GB, as those are not the same (you can thank harddisk producers for this confusion).

Also EXT3 is a journaling system that uses (not a tiny) part of each partition.

This may explain this. At least that has been the conclusion in countless threads on this forum about this matter where people suddenly found many GiB "missing".


*added*

Btw welcome to the forums :) Take off your coat and have some cookies :)

---

### Post by mkvnmtr on 2009-03-03
You will find that installing gparted and then opening the partition editor will allow you to see what you have a little clearer than the terminal command. Don't try to use it to do anything to your partitions. If you decide to work on your partitions you should do it from a live disk so that your partitions are not mounted.

---

### Post by Martynwills on 2009-03-03
I´ve installed Gparted. I can find it by using the tracker tool, but is there a way to have it listed as an application on the applications tab? I´ve tried edit menus and it just doesn´t show up.

---

### Post by gandaran on 2009-03-03
> **Martynwills said:**
> I´ve installed Gparted. I can find it by using the tracker tool, but is there a way to have it listed as an application on the applications tab? I´ve tried edit menus and it just doesn´t show up.
you find it in system » administration » partition editor

---

### Post by Martynwills on 2009-03-03
Thanks very much for all the help. I feel like i´ve plunged down the rabbit hole :D

---

