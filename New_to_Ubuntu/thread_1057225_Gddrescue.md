---
title: "Gddrescue"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by aguywithfeet on 2009-02-01
Ok im trying to run gddrescue on a cd. From what i read i will be able to possibly recover the music even though there are scratches.(correct?)

My problem is i can't find the executable and i can't seem to find what to call my cdrom in order to do it from the terminal prompt.

Perhaps someone could give me a little walkthrough if it's not to much?

i installed gddrescue through the synaptic package manager, so i assume it is properly installed as it says it is.

---

### Post by Michael.Godawski on 2009-02-01
hi,

to rescue one file the syntax is as follows:

```
ddrescue -v /path/to/damagedfile /path/to/rescuedfile
```[I]

To rescue a whole drive use this syntax:
[/I]```

ddrescue -v /dev/sdx /path/secureddata.iso

```Example: To rescue a very important document from a CD run this:


```
ddrescue -v --max-retries=-1 /media/cdrom1/importantdocument.pdf ~/Documents/importantdocument.pdf ~/Documents/importantdocument.log



```

---

### Post by aguywithfeet on 2009-02-04
MY problem is i cannot figure what my cdrom's name is to type it in. 
i did fdisk but cannot make heads or tails of it.here is what i get when i type in "sudo fdisk -l"
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x102545d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
eric@eric-desktop:~$ 

and here is just "fdisk"...

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

 while im at it, is there any kind of tutorial that retrains us windows people into the linnux people? These commands and such are completely foreign.

---

### Post by cesium62 on 2009-03-19
Try the 'df' command (after inserting the CD into your system).  On my system, at the moment, I get:

$ ~/rescue$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6            236648355  74482871 150141235  34% /
varrun                  516956       236    516720   1% /var/run
varlock                 516956         0    516956   0% /var/lock
udev                    516956        60    516896   1% /dev
devshm                  516956        24    516932   1% /dev/shm
/dev/sda3               197599     92788     94771  50% /boot
tmpfs                   516956     39788    477168   8% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon     236648355  74482871 150141235  34% /home/cesium/.gvfs
/dev/scd0                 4922      4922         0 100% /media/cdrom0

And /dev/scd0 is pretty clearly the path I want.

Cs

---

### Post by dentman on 2010-09-29
Here was my bash

Df= /dev/sr0 which is my cd rom

So I used this to get ALL files off. No log file but you could add that with this ~/Documents/thenameofyourfolder.log

Thus

ddrescue -v --max-retries=-1 /dev/sr0 ~/Documents/ddrescue

or with log

ddrescue -v --max-retries=-1 /dev/sr0 ~/Documents/ddrescue ~~/Documents/ddrescue.log

---

