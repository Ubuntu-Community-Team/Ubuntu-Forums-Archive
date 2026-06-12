---
title: "&quot;Guided - resize the partition and use the freed space&quot; not showing"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by GreggyZed on 2009-01-27
Hi,

I am trying to have a dual boot of Ubuntu 8.10 and Windows XP SP2 but when I try installing "Guided - resize the partition and use the freed space" option is not displayed.  I already have Windows XP SP2 installed and I have never made a partition on my drive.  Any suggestions on how to make this option appear?

Thanks in advance.

---

### Post by GreggyZed on 2009-01-27
Bump...

I think the problem is that the installer is not recognizing the existence of Windows on my computer.  I re-downloaded the image and burned it again and the problem still persists.

---

### Post by mikewhatever on 2009-01-27
Can you post the output of <sudo fdisk -l> from Applications->Accessories->Terminal. Have you tried accessing the Windows or another partition while running from cd?

Instead of downloading and re-downloading the iso, just check the already existing file for integrity. 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you suspect that something is wrong with the cd, it's also advisable to check the cd for errors.

---

### Post by GreggyZed on 2009-01-28
This is the output from that command:

[B]Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9261    74388951    7  HPFS/NTFS
/dev/sda2            9262        9730     3767242+  12  Compaq diagnostics
ubuntu@ubuntu:~$ 

[/B]
I tried mounting my Hard Drive while using the Live CD and it worked perfectly.  I can edit files, create files, listen to music, etc.

If it helps, my plans for the partitions are as follows:  Have 90% of my hard drive remain the original C Drive partition with Windows (NTFS since I've read that works fine with Ubuntu) and use 10% of my hard drive for Ubuntu.  My plan is to store all of my media and work files in the original C Drive so everything is together.

---

### Post by caljohnsmith on 2009-01-28
It looks like you can't use the "Guided - resize the partition and use the freed space" option because there currently is no unallocated space on your HDD. You could open up gparted first (System > Admin > Partition Editor) and use that to shrink your sda1 Windows partition from the end in order to make room for Ubuntu. Then if I were you, I would create an "extended" partition with that freed space, and inside of the extended partition you can create an ext3 logical partition for your main Ubuntu install, and also a swap partition. Or if you want, after you shrink the Windows partition, just run the Ubuntu installer again and you should then be able to use the "guided" partitioning option. Good luck and let us know how it goes or if you run into problems.

---

