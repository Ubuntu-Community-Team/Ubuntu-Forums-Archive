---
title: "Dual booting windows and ubuntu"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by ludarabota on 2009-03-01
Ok I need some help with dual booting Ubuntu 8.10 and Windows Vista 32bit. I currently have 2 SATA hard drives, the first one is 250GB and the second one is 750GB. The first HDD is split into 2 NTFS partitions, one 60GB partition for windows and a second empty partition which I would like to partition again leaving ~60GB for Ubuntu and the rest for windows files (NTFS file system).  What steps do I need to take so I can split the 2nd partition in 2 (one for ubuntu and one for windows files) and how do I install Ubuntu so that I can keep my current windows installation and have an option of booting either Windows or Ubuntu on computer restart. Any help would be greatly appreciated. Thanks

---

### Post by Svensk023 on 2009-03-01
well if I were you, i would use one HDD per OS, but thats just me.

But to answer your question, do as follows:

Once you reach the partition section of the install process, choose "manual partition"
Once you're in the manual partition manager _delete_ the empty NTFS partition (please be careful that you dont touch your windows partition) after its deleted you can select the unallocated space and format a 60GB ext3 primary partition for Ubuntu. you will need to also make a swap partition, give it twice the amount of RAM memory you have. Then with the rest of your unallocated space, format that as a FAT32 partition, which will just be free space that both Ubuntu and Windows can use.

---

### Post by Bodsda on 2009-03-01
Hi.

I would be inclined to install ubuntu onto the free hard drive just for simplicity but as you asked about partitioning the first one il tell you how.

Boot into the ubuntu live cd and open a terminal

Applications >> Accessories >> Terminal

In the new window type
```
gksudo gparted
```
This will bring up the partitioning tool.

Right click on the second partition and click 'resize'.
In the new window change the size of the partition to '60000' (60gb) and then click in the (Free space following) box which should then change to a number resembling the free space left.

click ok, then hit apply in the toolbar (where all the icons are(the tick))

This will make a new partition of 60gb after the windows partition and leave the rest of the space as unpartitioned free space.

Install
======

When you get to the part of the install where it asks you to choose how to install, click 'manual'

Locate the hard drive with your newly made partition, click it then press the edit button. Change the filesystem to 'ext3' or it might say 'ext2 journaling', then change the mountpoint to '/' and click ok.

We also need to create a swap area. In the unpartitioned area right click it and select 'new' make the partition size 2xRAM, so if you have 2gb of RAM the swap size should be 4000(4gb). In one of the boxes (i forget which one) change the option to 'swap area' and click ok. The hit apply or next whichever it is. 
Hope this helps

Bodsda

---

### Post by ludarabota on 2009-03-01
I guess I forgot to mention that my second 750GB HDD was already full with movies, music, pics etc. so I can't use it for Ubuntu. The only free space I have is the 180GB on my second partition of my windows boot drive. 
So I can safely delete the second partition of my boot drive, format it and split it in 3 partitions, 1 60GB ext3 partition for Ubuntu, 1 4GB swap partition (I have 2GB of ram) and the rest I can partition in NTFS (so I can use it for file storage for both Ubuntu and Vista). Is installing Ubuntu going to leave my Windows partition untouched? Do I need to take further steps to asure the system will have a dual boot option?
Thanks for the help.

---

### Post by ClaytonOT on 2009-03-01
Defrag your computer, prior to the partition, to reduce the risk of Windows corruption and other data loss. GRUB has come up for me on both of my dual-boot installs so I think you'll be alright.

---

### Post by ludarabota on 2009-03-01
defrag the windows partitions? What does it have to do with ubuntu.

---

### Post by handy on 2009-03-01
If you can manage it, separate drives for each OS is the way to go.

---

### Post by stalkier on 2009-03-01
> **Svensk023 said:**
> well if I were you, i would use one HDD per OS, but thats just me.

But to answer your question, do as follows:

Once you reach the partition section of the install process, choose "manual partition"
Once you're in the manual partition manager _delete_ the empty NTFS partition (please be careful that you dont touch your windows partition) after its deleted you can select the unallocated space and format a 60GB ext3 primary partition for Ubuntu. you will need to also make a swap partition, give it twice the amount of RAM memory you have. Then with the rest of your unallocated space, format that as a FAT32 partition, which will just be free space that both Ubuntu and Windows can use.

+1 on one OS per disc. I use a SATA hdd for my Windows and a separate IDE drive for my Ubuntu. Works very nicely.

---

