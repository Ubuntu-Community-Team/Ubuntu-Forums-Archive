---
title: "mounting /sys on /root/sys failed ; mounting /proc on /root/proc failed ; Try passing"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by manuganji on 2010-10-27
I'm running a 64-bit Ubuntu 10.10. My Ubuntu partition is starting with a lot of error messages and stopping at

> mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init.
No init fount. Try passing init= bootarg.
BusyBox v1.15.3(Ubuntu 1.1.15.3 - 1ubuntu5)built-in shell
enter 'help' for a list of built-in commands
(initframs).


I logged in with live CD and tried what I saw in some other threads in these forums. plz help me out. This is the output I get. what should I do now?

> ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          16      128488+  de  Dell Utility
/dev/sda2   *          17        1246     9873408    7  HPFS/NTFS
/dev/sda3            1246        9078    62914560    7  HPFS/NTFS
/dev/sda4            9078       38914   239651841    f  W95 Ext'd (LBA)
/dev/sda5            9078       16911    62914560    7  HPFS/NTFS
/dev/sda6           16911       25396    68157440    7  HPFS/NTFS
/dev/sda7           27354       38914    92849152    7  HPFS/NTFS
/dev/sda8           25396       26563     9372672   83  Linux
/dev/sda9           26563       27353     6346752   82  Linux swap / Solaris

Partition table entries are not in disk order
root@ubuntu:/home/ubuntu# fsck -f /dev/sda8
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda8
Filesystem mounted or opened exclusively by another program?



Thnks in advance

---

### Post by manuganji on 2010-10-29
Please at least direct me to a thread where I may find a solution. I think I have tried fairly enough to search on this forum.

---

### Post by Quackers on 2010-10-29
Doing some searching, it seems some people have had your problem and what they did was boot the Ubuntu Live cd and when the desktop loads they opened a terminal and typed
```
fsck -y /dev/sdaX
```

where sdaX was their Ubuntu partition (sda8 in your case). More details here

[http://ubuntuforums.org/showthread.php?t=1386549](http://ubuntuforums.org/showthread.php?t=1386549)

---

### Post by manuganji on 2010-10-29
> ubuntu@ubuntu:~$ sudo fsck -y /dev/sda8
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda8
Filesystem mounted or opened exclusively by another program?


This is the output i get. Man this is so hard to solve! :(

---

### Post by bioterror on 2010-10-29
> **manuganji said:**
> This is the output i get. Man this is so hard to solve! :(

```
When running LiveCD
sudo umount /dev/sda8
sudo fsck -y /dev/sda8

```

It cant be busy if you're not using it.
Could "fsck -fy" be too rough? :twisted:

---

### Post by KainBox on 2010-10-30
> **manuganji said:**
> This is the output i get. Man this is so hard to solve! :(

trye here   ,at the end
[http://art.ubuntuforums.org/showthread.php?t=1601810&highlight=mounting+dev+on+root+dev+failed+no+such+file+OR+directory](http://art.ubuntuforums.org/showthread.php?t=1601810&highlight=mounting+dev+on+root+dev+failed+no+such+file+OR+directory)

---

### Post by nutsy.ben on 2010-12-30
Well. Got the same problem.

My workaround was to remove the hard drive and plug it as a slave into an external computer. then switch it off and replug the hard drive in the first computer.

Would be happy if there is a solution working faster.

---

