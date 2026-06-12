---
title: "Grub loading...error 18 (cannot boot system)"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by djftl on 2009-11-03
Hi guys,

I installed Ubuntu side by side with windows, and I had problems. I retried to install in within windows and it worked fine except that the boot menu had Linux Ubuntu, recovery boot amd windows to chose from. When I choose to boot through windows it had another screen where it listed windows and ubuntu. 

When I chose Ubuntu, everything worked fine without any problems. I ran my system like this for 3 months until yesterday when I had to uninstall the problem-some Ubuntu since I wanted to use that partition (80G). I deleted that partition but not the windows partition that had the working Ubuntu directory.
After all this I could not boot, message GRUB loading Stage1.5
GRUB loading, please wait...ERROR 18

I checked for some solution in this forum could not find relevant to my situation or when I did use it, that solution did help me.
I fdisk in the terminal and this is my partitions
#ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09790978

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14164   113772298+   7  HPFS/NTFS
/dev/sda2           14165       30400   130415670    f  W95 Ext'd (LBA)
/dev/sda5           14165       17502    26812453+   7  HPFS/NTFS
/dev/sda6           17503       17652     1204843+   7  HPFS/NTFS
/dev/sda7           17653       30400   102398278+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdeef99c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19777   158858721    7  HPFS/NTFS
/dev/sdb2           19778       30401    85337280    5  Extended
/dev/sdb5           19778       28326    68669811    7  HPFS/NTFS
/dev/sdb6           29964       30401     3518203+   7  HPFS/NTFS
/dev/sdb7           28653       29901    10032561   83  Linux
/dev/sdb8           29902       29963      497983+  82  Linux swap / Solaris
/dev/sdb9           28327       28630     2441848+  83  Linux
/dev/sdb10          28631       28652      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 6007 MB, 6007357440 bytes
240 heads, 63 sectors/track, 776 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa8a7a8a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         776     5866528+   7  HPFS/NTFS
Partition 1 has different physical/logical endings:
     phys=(774, 239, 63) logical=(775, 239, 63)
ubuntu@ubuntu:~$ 
#
Please help me to recover my grub as my Ubuntu 9.04 was working fine within windows, now I can't even boot from windows.

I tried this post [http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/](http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/). I could not mount them.

Thanks in advance.

---

### Post by LarsW_Tierp on 2009-11-03
Hi.
Take a look at this link: [How to fix your windows mbr...]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/")

---

### Post by djftl on 2009-11-04
Thanks I've enabled the universal repo and it downloaded some software but still could not do anything.
#ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
#
I went to download it and now I can't install it. Please help!!!

---

### Post by kansasnoob on 2009-11-04
> **djftl said:**
> Thanks I've enabled the universal repo and it downloaded some software but still could not do anything.
#ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
#
I went to download it and now I can't install it. Please help!!!

Did you download a tar.gz?

There's a link to the .deb here, much easier to install:

[http://penguininside.blogspot.com/2009/06/fixing-windows-mbr-from-linux.html](http://penguininside.blogspot.com/2009/06/fixing-windows-mbr-from-linux.html)

Note that it says:

**Remember that this procedure will only work for Windows XP/2000/2003 MBR.**

---

### Post by djftl on 2009-11-22
Hi guys,

I had to reinstall windows to get back my mbr. System is running well.

Thanks for the attempts.

Regards,

---

