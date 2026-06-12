---
title: "A big trouble with my data, my ubuntu, my HDD"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by hafthanhf on 2009-07-26
Hi all, I've got a big trouble with my data, my HDD while trying to edit the fstab file.
I installed Ubuntu and window XP (dual boot, Ubuntu first), after that, I tried to make my Ubuntu mount other ntfs partition automatically but, after modified the fstab file, my data on E: and C: partitions was disappeared. And now, I can not mount them anymore.
How must I do to make it work again, and get my data back (now I am using windows XP, must I reinstall ubuntu to fix this problem)
thanks a lot!

---

### Post by Liolikas on 2009-07-26
sudo fdisk -l
Show what you have (or screenshot of partition magic if windows)

---

### Post by hafthanhf on 2009-07-26
> **Liolikas said:**
> sudo fdisk -l
Show what you have (or screenshot of partition magic if windows)
Here is the screenshoot of "sudo fdisk -l" and fstab: 
at that moment, srceenshoot of partition magic look like the following:
Primary         Logical
Ubuntu 11GB    |XP-9GB|Linux swap 700MB|PROGRAMS-20GB|DATA-37GB|
XP, PROGRAMS and DATA are ntfs

now, I've merged the Ubuntu and XP partitions into XP (ntfs), but I still can not see any data in the DATA partition (I know that they are still all there).

---

### Post by Liolikas on 2009-07-26
df -h
If you have 0% in data(/dev/sda6 so there is no data there really.

---

### Post by Bucky Ball on 2009-07-26
Okay, firstly, you installed Ubuntu first which can be worked around but problematic for the novice (better to go Windows first then Linux as Windows demands the first partition on the drive (primary), Ubuntu does not (and does not need to be on the primary partition - it can exist on a logical drive in an extended partition).

Secondly, There is no Ubuntu swap (sda3 is a windows extended partition) or anything else. You have and/or had  '/' (root partition) on the first partition (sda1), first and only drive, and that is it for Ubuntu.

Lastly, your fstab suggests you've removed whatever was on sda1 (read the message it gives before the UUID).

---

### Post by hafthanhf on 2009-07-26
I don't think so, before I modified the fstab, I had 30GB of data in DATA.
But now, although the PQ magic show that I have nearly 100% free space in it, I can not copy a 10GB file to it, the OS said that:the disk is full.
By the way, I've tried some testing tool in Hirent boot CD, and the tool from Samsung can not detect my HDD (a samsung HDD).
and When I reinstall ubuntu, I can not mount it. Ubuntu said that there is something wrong with its file structure or file system

---

### Post by Liolikas on 2009-07-26
Try some to google for some ntfs repair crap for windows.
Basically ntfs is not Ubuntu fs and not long time ago ntfs was read only.

---

### Post by hafthanhf on 2009-07-26
thanks you guys, I've tried GNUparted
Now, I can mount the DATA, but, I still can not get my data back. :(

---

### Post by Bucky Ball on 2009-07-26
Can you see it there or is it gone? If it is permissions only, they can be changed.

---

### Post by hafthanhf on 2009-07-26
> **Bucky Ball said:**
> Can you see it there or is it gone? If it is permissions only, they can be changed.
Thank you, Bucky, I still cann't see any sign of it. May be it is gone. :(. I will try more approaches to recover it. Can you suggest me the best recovery software in ubuntu?

---

### Post by Bucky Ball on 2009-07-27
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

That will get you going but it could take awhile. There are other apps about but can't think of them right now. This might be of use also:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Google 'recover deleted data ubuntu' or something like that. Maybe someone will chip in with the other apps I can't remember. :)

---

### Post by hafthanhf on 2009-07-27
> **Bucky Ball said:**
> [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

That will get you going but it could take awhile. There are other apps about but can't think of them right now. This might be of use also:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Google 'recover deleted data ubuntu' or something like that. Maybe someone will chip in with the other apps I can't remember. :)
Bucky ball, thanks you so much, I've tried some recovery software, but it take me much time, so I decided to give it up, and formated my HDD.
Now I will begin my new Ubuntu. Thank you all once again

---

