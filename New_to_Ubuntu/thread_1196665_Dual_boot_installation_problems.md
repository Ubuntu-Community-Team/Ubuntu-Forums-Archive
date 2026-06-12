---
title: "Dual boot installation problems"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by noobie joe1 on 2009-06-25
[SIZE=2]I've recently installed Ubuntu on a system already running Windows Vista Home Premium. The method i used was to shrink drive using windows then install Ubuntu 9.04 using disk.  One place i might have messed up during installation was when i was asked to enter name password etc i pressed the back button. When i did this i noticed a changed in the top info bar about partion space. First time i saw about 19.5 gigs free but after pressing back button it said 2 gigs free. Anyway to proceed after completing installation i opened firefox and it alerted me to security updates. I tried to install but i got a message saying not enough space required for installation and that I needed to use sudo get-apt clean.  Whats going on here. Also when i go to computer in places i see that there is one drive that has a total of 70 gigs 40 used and about 20 free. On Fllesystem it says there are only 73megs left. Whats going on here.  Is Filesystem the place where Ubuntu OS is stored? What is Filesystem and how do i fix the problem with space?

ps im totally new to Linux[/SIZE]

---

### Post by presence1960 on 2009-06-25
> **noobie joe1 said:**
> [SIZE=2]I've recently installed Ubuntu on a system already running Windows Vista Home Premium. The method i used was to shrink drive using windows then install Ubuntu 9.04 using disk.  One place i might have messed up during installation was when i was asked to enter name password etc i pressed the back button. When i did this i noticed a changed in the top info bar about partion space. First time i saw about 19.5 gigs free but after pressing back button it said 2 gigs free. Anyway to proceed after completing installation i opened firefox and it alerted me to security updates. I tried to install but i got a message saying not enough space required for installation and that I needed to use sudo get-apt clean.  Whats going on here. Also when i go to computer in places i see that there is one drive that has a total of 70 gigs 40 used and about 20 free. On Fllesystem it says there are only 73megs left. Whats going on here.  Is Filesystem the place where Ubuntu OS is stored? What is Filesystem and how do i fix the problem with space?

ps im totally new to Linux[/SIZE]

I think you already answered your own question, when you hit the back buton it said 2 gigs. if you failed to adjust that & proceeded with the install then that is what you have 2 GB for Ubuntu.

Just to be sure open a terminal and run this command ```
sudo fdisk -l
``` BTW that is a lowercase L. Post the output back here please. We'll see what you have then.

---

### Post by noobie joe1 on 2009-06-25
here is the output from sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52084d18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9404    73994328    7  HPFS/NTFS
/dev/sda3            9405        9729     2610562+   5  Extended
/dev/sda5            9405        9707     2433816   83  Linux
/dev/sda6

---

### Post by presence1960 on 2009-06-25
Looks like you only have 2+ GB for your Ubuntu partition. I would start over. First thing I would do is defrag Vista at least once, maybe twice before using Vista's disk management tool to shrink Vista's partition to create space for ubuntu. While you are in there you may as well delete those Ubuntu partitions you created as well. Once you have shrunk Vista and deleted those partitions I would boot the Ubuntu Live CD. Choose "use ubuntu without changes". When the desktop loads go System > Administration > Partition Editor. Create two partitions from the unallocated space: 1 for Ubuntu (/ or root) and one for swap. I recommend swap 1 to 1.5 times your RAM. If you have 1 GB RAM then make swap 1 or 1.5 GB. Then create the second partition from the remaining space as ext3 or ext 4.. Click the green apply check mark to apply the changes. When complete close Partition Editor. Click the Install icon on the desktop to begin installation. When you get to the "Prepare disk space" window choose "manual option. Highlight your intended Ubuntu partition and set parameters for Partition Type (primary, extended or logical), Use As ( Filesystem (usually ext 3 or ext 4) Mountpoint (/). When complete click OK or ADD. Then highlight the intended swap Partition and set parameters for Partition Type and Use as ( set to swap). Click OK or ADD. Now continue with the installation.

Prior to doing all this I suggest you do some reading and familiarize yourself with what it is you are about to do. here are a few links to get you started:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  -for a free pdf Ubuntu Pocket Guide which has a great step by step on the installation process.

---

