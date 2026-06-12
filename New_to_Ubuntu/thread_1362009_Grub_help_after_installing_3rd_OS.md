---
title: "Grub help after installing 3rd OS"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by running_rabbit07 on 2009-12-22
I just installed Kubuntu 9.10 beside Windows 7 and Ubuntu 9.04. I told the install not to install grub out of fear that it would make the others non-bootable. Here is where everything is,```
rabbit@rabbit-desktop:~$ sudo fdisk -l
[sudo] password for rabbit: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0defc2af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14444   116021398+   7  HPFS/NTFS
/dev/sda2           14445       16994    20482875   83  Linux
/dev/sda3           16995       30401   107691727+   5  Extended
/dev/sda5           17110       26910    78726532+  83  Linux
/dev/sda6           16995       17109      923674+  82  Linux swap / Solaris
/dev/sda7           26911       30251    26836551   83  Linux
/dev/sda8           30252       30401     1204843+  82  Linux swap / Solaris

Partition table entries are not in disk order

```What do I have to do to menu.lst in order to add Kubuntu to the list? 

Thanks.

---

### Post by oldfred on 2009-12-22
Copy one of your 9.04 entries to the bottom of menu.lst. Then open up from your Kubuntu /boot/grub/grub.cfg and find the UUIDs, partition and kernel & initrd versions and copy them over.  i.e. just about everything, but in the menu.lst format instead of the new grub2 format.

---

### Post by running_rabbit07 on 2009-12-22
Thanks Fred. Problem solved and enjoying KDE. After installing Windows 7 on my wife's machine and mine. I needed something to show off that had the same high quality look.

---

