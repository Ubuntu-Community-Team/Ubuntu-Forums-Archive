---
title: "Can't boot up"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by Edward in CT on 2010-08-20
Somehow I chose a Windows 7 rescue partition to open instead of Ubuntu 10.04.  Well, I clicked out of it and now when I restart my machine it says...
 
error: no such partition
grub rescue>

How do I get back to choosing between Ubuntu or Windows 7 screen.

I have an Acer Aspire Netbook, 10.04 partitioned with Windows 7 Starter.

Help please.  Thanks in advance.

---

### Post by jimbop99 on 2010-08-20
Sounds like grub needs to be re-installed.

[]("https://help.ubuntu.com/community/Grub2")[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Check near the bottom of the page.

---

### Post by Edward in CT on 2010-08-21
So I made a Live CD
I went to Terminal to try and reinstall Grub 2 and typed:

 ubuntu@ubuntu:~$ sudo fdisk -l

I got

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdcaa3f7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown
/dev/sda2   *        1568        1580      104422+   7  HPFS/NTFS
/dev/sda3            1581        6444    39069336    7  HPFS/NTFS
/dev/sda4            6444       19457   104527201+   5  Extended
/dev/sda5           19332       19457     1012063+  82  Linux swap / Solaris

I tried to mount /dev/sda4 with
ubuntu@ubuntu:~$ sudo mount /dev/sda4

I keep getting

mount: can't find /dev/sda4 in /etc/fstab or /etc/mtab

What am I doing wrong?  Thanks for anyone who can help.

---

### Post by Quackers on 2010-08-21
It may be worth re-posting this in the "General Help" forum.

---

### Post by Rubi1200 on 2010-08-21
If you have the LiveCD, use it and post the results of the bootscript linked to at the bottom of my post.

The results will give us a better idea of what is going on and make offering solutions easier.

Thanks.

---

