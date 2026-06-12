---
title: "problem booting ubuntu 10.04 lucid"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by prabhata on 2010-08-07
Hi there,
regards.

On my dell laptop latitude D400, 160 GB hdd XP2 is there. XP2 had 4 partition on harddisk. 
I put ubuntu 10.04 live CD in drive and went in Gparted, deleted one empty partition and made it unallocated. And choose that partition to install ubuntu 10.04 lucid. Here it is clear that i didnot install ubuntu side by side of XP2.

Installation finished very nicely. But when restarting then following mesaage is coming....

         "GNU GRUB version 1.98-1ubuntu7
minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions.

grub>_"

The entire screen looks like a Terminal or Command Prompt. I tried the  reboot command, but it simply brought this screen up again.   So...is there anything that I can do?

One more point is that b/c i am not reaching to the point where we choose either operating system so i can't use XP too.
waiting with regards...
prabhata

---

### Post by neoargon on 2010-08-07
Couldn't you try installing again

---

### Post by prabhata on 2010-08-07
[LIST=1]
[*]I put live cd 10.04 and in terminal typed sudo fdisk -l
[/LIST]

then i got the result..
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003309a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4844    38909398+   7  HPFS/NTFS
/dev/sda2            4845       19458   117380587+   f  W95 Ext'd (LBA)
/dev/sda5            4845        9688    38909398+   e  W95 FAT16 (LBA)
/dev/sda6            9689       14532    38909398+   e  W95 FAT16 (LBA)
/dev/sda7           14533       19273    38076416   83  Linux
/dev/sda8           19273       19458     1483776   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

Here Sda1 is my xp and sda5 and sda6 is the partition in XP which you can see in "my computer" of windows XP. 
and sda7 is the partition i installed Linux.

Pls tell me if i can do something for it. Or should i reinstall everything ?
prabhata

---

### Post by arochester on 2010-08-07
This is interesting to me.

I have 3 Dell C400s. (I am writing this from one.) They all boot perfectly. Only if I load something like Debian do I have to edit the boot line to get the correct video.

What you describe sounds like a video problem - which just shouldn't exist.

Check your install disk and reinstall.

---

### Post by prabhata on 2010-08-07
> **arochester said:**
> This is interesting to me.

I have 3 Dell C400s. (I am writing this from one.) They all boot perfectly. Only if I load something like Debian do I have to edit the boot line to get the correct video.

What you describe sounds like a video problem - which just shouldn't exist.

Check your install disk and reinstall.

Sorry for the late reply. I was reinstalling that's why i am replying late.
But now problem is changed. After reinstallation when restarted computer then error message came---

"error- out of disk
grub rescue>"

And nothing more happened..
Pls help..
With regards waiting...
Prabhata

---

### Post by ajgreeny on 2010-08-07
Do you know where you installed grub during the installation process?

It should have gone on to /dev/sda, not onto a partition, eg /dev/sda6, which may be your problem.

Try restoring grub from the live CD before re-installing the whole OS.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It would also be helpful if, using the live CD, you downloaded and ran the boot_info_script from meierfra, which shows all the grub setup info that could help solve your problem.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by prabhata on 2010-08-07
> **ajgreeny said:**
> Do you know where you installed grub during the installation process?

It should have gone on to /dev/sda, not onto a partition, eg /dev/sda6, which may be your problem.

Try restoring grub from the live CD before re-installing the whole OS.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It would also be helpful if, using the live CD, you downloaded and ran the boot_info_script from meierfra, which shows all the grub setup info that could help solve your problem.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)


Thank you for your reply and sharing your knowledge. 
Actually i am new with ubuntu and i don't know where did i installed grub during the installation. I put live cd in the drive. followed instructions about language and keyboards etc. And when it asked for partition then i selected the largest area on the device and then started installation. Installation wizard never asked me where to install grub specially. So i don't know. 

Anyhow i reinstalled it and the problem has been changed. Now when i boot then error message is coming.

"error- out of disk
grub rescue>"

And nothing more happened..
Pls see the case
with regards
waiting 
prabhata

---

