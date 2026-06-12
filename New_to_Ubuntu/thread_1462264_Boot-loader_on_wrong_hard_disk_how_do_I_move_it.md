---
title: "Boot-loader on wrong hard disk how do I move it?"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by deadlockedgamer on 2010-04-25
I installed ubuntu 10.04 rc on my machine. I had my files backed up to my second hardrive which was not even set to boot from in bios. However my bios do not support usb boot so I use plop to boot from usb and install. Ubuntu would then list a bunch of errors and not start. Upon adding my second hardrive as second boot device in bios it booted. However the drive no longer has a file-system and cannot be mounted. I would like to move my boot-loader over to the correct drive so I can reformat and use my second hard disk. I think the spoofed boot up is what caused the issue. I managed to recover most of my files with a cli program! :D

---

### Post by oldfred on 2010-04-25
Are you sure you just are not booting the wrong drive? In BIOS you set which drive to boot.

You can just reinstall boot loaders, windows, grub legacy or grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you are going to do a full install on the second drive, just install it there and be sure to use the advanced button at the end of partitioning to choose the correct drive ( should be the same drive as you install Ubuntu to).

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by Gone fishing on 2010-04-25
This guide should do the trick [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) 

obviously you are using grub 2 so you can skip down to Overwriting the Master Boot Record

---

### Post by deadlockedgamer on 2010-04-25
here is my output from terminal 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea065

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005ebe5

   Device Boot      Start         End      Blocks   Id  System
I would like to make sure the bootloader is on the 80gb drive. Can I do this without a live cd since I am booted into the harddrive install? if so what modifications do I make to the instructions on [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) ?

---

### Post by oldfred on 2010-04-25
This is for grub2 which with 10.04rc you have:

reinstall from working system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

---

### Post by deadlockedgamer on 2010-04-25
you posted this 5 minutes after I did the other instructions as if a live cd but without it. Now I boot to grub rescue how do I fix that?

---

### Post by deadlockedgamer on 2010-04-25
I found a live cd so I can use that to follow instructions

---

### Post by Gone fishing on 2010-04-25
The link I gave you above explains how to fix grub2 and load it onto the mbr from a live CD.

---

### Post by deadlockedgamer on 2010-04-25
ok about to follow this but first does it hurt that I will be using a 9.10 cd with a 10.04 install? shouldn't because they are both grub 2 right?

---

### Post by deadlockedgamer on 2010-04-25
didn't work looks like it may be because I put grub on the wrong section where do I put it?

---

### Post by deadlockedgamer on 2010-04-25
nvrm it did work thanks!

---

### Post by oldfred on 2010-04-25
Glad you got it working. :)

---

