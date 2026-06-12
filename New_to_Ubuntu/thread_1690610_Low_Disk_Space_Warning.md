---
title: "Low Disk Space Warning"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by l_marcelo on 2011-02-18
At start up the Disk Usage Analyzer tool has been showing the following warning:

[COLOR=Blue]Total file system capacity  100%  18.8GB
    Total file system usage 90.9%  17.1GB
[/COLOR]
The initial setup of the disk space was 32GB, later, I increased it to 128GB. However, the message still showing, and it is getting worse as the message is appearing more and more often. Ubuntu 10.04 is installed on top of VMWare.

I ran fdisk -l and the following output is shown:

[COLOR=Blue]Disk /dev/sda: 135.3 GB, 135291469824 bytes
255 heads, 63 sectors/track, 16448 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b3d83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2496    20049088+  83  Linux
/dev/sda2            2497        2610      915705    5  Extended
/dev/sda5            2497        2610      915673+  82  Linux swap / Solaris
[/COLOR]
The dev/sda is showing the 132GB, but the summary does not reflect it.

Cannot tell what is wrong, is it Ubuntu or VMWare or else, please help.

Thank you.

---

### Post by mikewhatever on 2011-02-18
According to the output you posted, the size of /dev/sda is indeed 135GB, but the size of the linux partition, /dev/sda1 is 20049088 or only about 19GB. You have to enlarge /dev/sda1 as well as /dev/sda.

---

### Post by Keiran230 on 2011-02-21
```
sudo apt-get -y install gparted; sudo gparted
```
The easiest way to perform a partition resize is to use gparted. You'll have to unmount the partitions before doing this though, so you might want to use a live disk. The ubuntu live disk will work with that previous command, or you can get the usual gparted live iso from sourceforge.net

---

