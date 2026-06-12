---
title: "plugged in external USB drive, how do I access it?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by kazimir82 on 2009-01-19
Recently installed Ubuntu 8.10 on my PC.

Just plugged in an external USB harddisk which I normally use on my work machine (Windows XP).

Perhaps this is an ultra noob question :oops: but... how do I access the drive??

---

### Post by collinp on 2009-01-19
In your file manager (which most everyone will call nautilus, its real name), there should be something in the side bar that says "Removable Media" or something similar. That is more than likely your hard drive; click on it to access it.

---

### Post by kazimir82 on 2009-01-19
Thanks for your fast answer!

Exactly where do I find this file manager, or nautilus? When I click Places -> Computer, I get into a "File Browser". It shows my regular harddrives there on the left, but no USB drive or 'removable media'.. :confused:

---

### Post by taurus on 2009-01-19
Did you use the _safely remove hardware_ option in windows the last time you use your external harddrive before you unplugged it?

Otherwise, open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by kazimir82 on 2009-01-19
Yes, I always do the 'safely remove hardware' routine before unplugging the drive. (either that, or I shutdown the entire PC).

I tried what you suggested, both commands (especially the first) give me lots of numbers and stuff I don't understand :oops:
Exactly what am I looking for? (I normally don't use the Terminal)

Isn't there something in the File Browser, e.g. when I go to Home or Computer, shouldn't the USB drive appear there somewhere?

---

### Post by taurus on 2009-01-19
If you don't understand about an output, just post it here.  I am sure someone will walk you through mounting your windows partition.

---

### Post by zwygart on 2009-01-19
Normally if you insert a amovible media it will mount automatically, put a icon on the desktop and open a file browser. But it seems that this not happens. So please again post the output of ```
sudo fdisk -l
```
To copy the output : select with the mouse then press CTRL+SHIFT+C. In the post press CTRL+V and the job is done. If this is to hard try this command```
sudo fdisk -l > fdisk
```This will create a file called fdisk in the current directory (your home) containing the output. Copy it or append the file.

In the output it will have a entry wich represents your drive normally /dev/sdb or /dev/sdc. Remember the letter b or c or another then do this commands each presseded by sudo to get root```
mkdir /media/USB
mount /dev/sdb /media/USB
```
Now you should have a icon on the desktop called USB or something else.
Click on it and the job is done.

Before doing this check at Places>Computer>Filesystem>media
Try out the icons there, may be one is your drive. After that do what I told and retry Places>Computer>Filesystem>media.

---

### Post by kazimir82 on 2009-01-19
Here's the output:

```
kazimir@linuks:~$ sudo fdisk -l
[sudo] password for kazimir:

Disk /dev/sda: 320.0 GB, 320000000000 bytes
255 heads, 63 sectors/track, 38904 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8         269     2104515    c  W95 FAT32 (LBA)
/dev/sda3             270        1485     9767520   83  Linux
/dev/sda4            1486       38904   300568116+  fd  Linux raid autodetect

Disk /dev/sdb: 320.0 GB, 320000000000 bytes
255 heads, 63 sectors/track, 38904 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000082

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           7       56196   de  Dell Utility
/dev/sdb2   *           8         269     2104515    c  W95 FAT32 (LBA)
/dev/sdb3             270        1485     9767520   83  Linux
/dev/sdb4            1486       38904   300568116+  fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5d06edc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

```

```
kazimir@linuks:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             9.2G  7.3G  1.5G  83% /
varrun                2.0G  100K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  104K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
gvfs-fuse-daemon      9.2G  7.3G  1.5G  83% /home/kazimir/.gvfs
kazimir@linuks:~$

```

If I understand correctly, the "sdc" thing should be my USB drive? (my external is 500GB, the two internal drives are 320GB each)

---

### Post by taurus on 2009-01-19
```
sudo mkdir /media/sdc1
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
ls -la /media/sdc1
```

---

