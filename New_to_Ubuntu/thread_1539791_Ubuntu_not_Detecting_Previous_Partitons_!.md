---
title: "Ubuntu not Detecting Previous Partitons !"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by hunkgagan on 2010-07-27
Hi,
 
I have Windows 7 Professional previously installed on my notebook and now I am trying to install Ubuntu 10.04. But it is not showing my any previous partition, just showing the completely unallocated disk. Thus I am not able to install the Ubuntu on my system because I cant let my previous data.
 
Please Help.
 
Thanks .

---

### Post by wojox on 2010-07-27
What does 

```
sudo fdisk -l
```

Return.

---

### Post by hunkgagan on 2010-07-27
I dont know much of command line and currently I am using windows. While installing the Ubuntu Partitioner is not showing any previous partition.

---

### Post by Wim Sturkenboom on 2010-07-27
If it's a live CD that you're trying to install from, use it in live mode. Open a terminal and run fdisk -l (lower case L)
```

root@btd-techweb01:~# fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1024     8225248+  83  Linux
/dev/hda2            1025        1090      530145   82  Linux swap
/dev/hda3            1091        4278    25607610   83  Linux
/dev/hda4            4279        4865     4715077+   5  Extended
/dev/hda5            4279        4865     4715046   83  Linux
root@btd-techweb01:~#

```You should get something like above; you might need to use sudo in front of the command.

---

### Post by hunkgagan on 2010-07-29
Thanks Everyone.

That was my MBR problem. I Updated my mbr with utility in windows. And now everything is working fine.

---

