---
title: "slow boot up"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by natman on 2009-05-25
Hi,
When i press the on button on my laptop i get the grub menu then a line saying
"booting from (hda0,ext3) long number sequence.."
this stays there for about 10sec then normal boot up happens and its fine after that. Why is that line just hanging there. I ran the following in a terminal and got
> natman@natman-laptop:~$ sudo fdisk -l
[sudo] password for natman:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bcb0fb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       19628   156122112    7  HPFS/NTFS
/dev/sda3           19629       20920    10377990   83  Linux
/dev/sda4           20921       38913   144528772+   5  Extended
/dev/sda5           20921       21163     1951866   82  Linux swap / Solaris
/dev/sda6           21164       38913   142576843+  83  Linux
natman@natman-laptop:~$


can anyone help?

---

### Post by natman on 2009-05-28
*bump

---

### Post by pastalavista on 2009-05-28
10 seconds seems about right to me for that first screen. There are hardware checks going on that can usually be skipped. [This tutorial]("http://ubuntuforums.org/showthread.php?t=89491") may help.

---

### Post by OffAxis on 2009-05-28
I'm not sure about that specific hang, but a good all-purpose app for researching boot problems is boot chart.
```

sudo apt-get install bootchart
```

There's good documentation on their website.

[www.bootchart.org](www.bootchart.org)

---

