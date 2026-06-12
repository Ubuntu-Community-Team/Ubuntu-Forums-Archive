---
title: "ubuntu missing from boot option,Please help me."
date: 2009-05-30
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-30
I have ubuntu 9.04 installed in one HDD and tried to install opensuse in another ,But now i see only opensuse in the boot option.I want to remove it and have only ubuntu.So i formatted my HDD which has suse but still i see only suse in boot option 

grub> find /boot/grub/stage1
(hd0,3)

grub> root (hd0,3)

grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,3)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


its done but i am unable to see it boot yet 
:(:(:(:(:( Help me

---

### Post by ravi_buz on 2009-05-30
[ATTACH]115689[/ATTACH]
Thats the pic of my partions but i am unable to mount my partition which has ubuntu in it

---

### Post by Elfy on 2009-05-30
can't read the screenshot - too small for me - run ```
sudo fdisk -l
``` from the livecd and post the results please

---

### Post by ravi_buz on 2009-05-30
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c892c89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3648    29302528+  8e  Linux LVM
/dev/sda2            3791       17759   112205992+   f  W95 Ext'd (LBA)
/dev/sda3           17760       19457    13639185    7  HPFS/NTFS
/dev/sda4   *        3649        3657       72292+  83  Linux
/dev/sda5            3791        9012    41945683+   7  HPFS/NTFS
/dev/sda6            9013       17759    70257664    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42170123

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4871    39117824    7  HPFS/NTFS


Sorry for duplicate but i am really worried and didnt get a good replly so i tried to post it in different section

---

### Post by Elfy on 2009-05-30
What error do you get from grub when you try and boot?

Was sda1 where opensuse was - the Linux LVM partition - if so it's not been formatted.

---

### Post by ravi_buz on 2009-05-30
When i tried to boot it showed only opensuse and windows boot (i have deleted windows so no need for that) my opensuse was installed in the 40 gb HDD and i have formatted it the lmv u see is my ubuntu file system

---

### Post by ravi_buz on 2009-05-30
THere is a 74 mb partition and i see grub,boot ,menu list etc.I opened the menu list and found yast ets(i think this belongs to suse) shall i format this one too

---

