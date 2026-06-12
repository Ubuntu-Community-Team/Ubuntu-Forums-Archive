---
title: "Not enough disk space for updates"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by startrekkie96 on 2009-08-31
I'm brand new to Ubuntu. When I finished installation, and started using the OS, I get the update manager popping up on me. When I try to download the updates, I get an error saying I don't have enough disk space and suggesting that I run a cleaning command. I ran the command, which helped, but I still get the message. I fear that when I installed Ubuntu, I may not have partitioned much of my hard drive at all to Ubuntu. Is there any way to fix this? I'm open to uninstalling and reinstalling the OS, seeing as I don't really have anything on here yet.

---

### Post by colau on 2009-08-31
> **startrekkie96 said:**
> I'm brand new to Ubuntu. When I finished installation, and started using the OS, I get the update manager popping up on me. When I try to download the updates, I get an error saying I don't have enough disk space and suggesting that I run a cleaning command. I ran the command, which helped, but I still get the message. I fear that when I installed Ubuntu, I may not have partitioned much of my hard drive at all to Ubuntu. Is there any way to fix this? I'm open to uninstalling and reinstalling the OS, seeing as I don't really have anything on here yet.
Can you post:
```

sudo fdisk -l
df -h

```

---

### Post by startrekkie96 on 2009-08-31
Okay, here we go:
This is from your first command:
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29ef29ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33387   268181046    7  HPFS/NTFS
/dev/sda2           33714       37539    30718976    7  HPFS/NTFS
/dev/sda3           37539       38913    11040768    7  HPFS/NTFS
/dev/sda4           33388       33713     2618595    5  Extended
/dev/sda5           33388       33692     2449881   83  Linux
/dev/sda6           33693       33713      168651   82  Linux swap / Solaris

Partition table entries are not in disk order

And this is from your second:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   16M 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  100K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  172K  1.5G   1% /dev
tmpfs                 1.5G   76K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sr0              1.7G  1.7G     0 100% /media/cdrom0
/dev/sda1             256G  169G   88G  66% /media/disk

Thank you for the help.

---

### Post by colau on 2009-08-31
Looks, short of space for ubuntu.
During installation, creating at least 8 GB partition for ubuntu is better as you have free spaces.
Mount your other drives(/dev/sda2, /dev/sda3) and post ```
df -h
```
System>Administration>gparted
Backup your data before partitioning.
Reinstallation is preferable.

---

### Post by startrekkie96 on 2009-09-01
Okay, so as far as backing up data goes, do I want to just back up data on the Ubuntu account? Or Windows too? If it's just Ubuntu, I don't care, because I installed it 3 days ago. But if you mean Windows too, I'd rather just reinstall. What do I do to reinstall? I realize these are stupid questions, but I don't know anything about Ubuntu, and very little about disk partitions.

---

### Post by matsuzine on 2009-09-01
Hi, startrekkie96.  You really should backup your data on the hard drive, windows or not, before making any changes to the partitions -- that's install or using gparted.  During installation, the ubiquity installer automatically creates new partitions, formats them, or resizes them, and this can sometimes go wrong.  

I think I read about a bug in the installer that makes the automatic sizing of partitions too small, so you might have to use the manual option in the installer if you decide to reinstall.  Since that is almost identical to using gparted to resize partitions, there's not a whole lot of difference assuming everything goes smoothly.  Personally, I would probably resize the partition in gparted after backing everything up.  This can take a while, depending on your machine.

---

### Post by cyaquino on 2009-09-02
In my very similar case, Ubuntu didn't take the free space and took only 2GB.
Now I have /dev/sda5 after a free 31GB space. How can I move that to the beginning of the free space, and then how can I resize the Ubuntu partitions?
Should I operate from a CD boot or what?
 
I'm downloading the ISO image of gparted-live, and hope to fix the issue with it...

---

### Post by startrekkie96 on 2009-09-03
Okay, so I have plenty of free space, but I need to add more to the Ubuntu partition. I checked my disk management, and it shows only 4 Gb, almost all of it used. And yes, I did use the automatic settings, so I must've got the version with the bug. I looked in my Administration file and couldn't find gparted, and the console window doesn't take it either. Do I need to get if from the package manager?

---

### Post by bacardiandwatermelon on 2009-09-03
I have always found it easiest to use partition magic to resize my windows partitions, and leave the rest as unallocated space, then when installing ubuntu choose the use unallocated space option.

---

### Post by Katalog on 2009-09-03
Alan Pope just posted up a screencast on partitioning that may be of some help, as it goes into a little more detail about how you go about setting up a dual boot during the partitioning phase of the Ubuntu installation:

[http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning](http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning)

Sometimes being able to watch a video of someone actually performing a procedure is better than using a written guide. I know it is for me, because I'm more a visual learner. Hope this helps!

---

### Post by startrekkie96 on 2009-09-06
So I have resolved the problem. Thank you to everyone for the help. To uninstall Ubuntu, I used the disk manager on windows to erase the partition (big mistake). Immediately, my machine starts refusing to boot, giving me Grub Error 22. To fix the problem, I used Super Grub Disk, a very easy program that I would recommend to anybody. It removed Grub, and I then reinstalled Ubuntu with a larger partition. Thanks to everybody for the help!

---

