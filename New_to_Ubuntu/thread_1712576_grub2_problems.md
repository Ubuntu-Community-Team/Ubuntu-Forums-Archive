---
title: "grub2 problems"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by mattrixx on 2011-03-22
As the title says I've got problems with grub.

There are lots of tutorial's and howto's on how to manipulate grub. They all do similar things, but I just don't understand how they can work. So my question is not can you help me fix grub but can you help me understand the instructions.

Perhaps I should have labelled this how does mount work?
But it is also how does grub2 decide the value of its "prefix" variable?

This is the last howto I found,
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

*note I do have a separate boot partition.
firstly,

>  If you have a separate /boot partition run these two commands first. Most users do not have a separate /boot partition. sdXZ is the boot partition.
Code:
### Run these two commands only if you have a separate /boot partition
sudo mkdir /mnt/boot
sudo mount /dev/sdXZ /mnt/boot  # Example: sudo mount /dev/sda6 /mnt/boot
Code:
sudo mount /dev/sdXY /mnt  # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdX # Example: sudo grub-install --root-directory=/mnt /dev/sda 

Q1 you mount /dev/sdXZ in the live-cd file tree at /mnt/boot; but then you mount /dev/sdXY one level lower than sdXZ?
Don't you loose access to sdXZ when you mount sdXY? (can you even mount on a non-empty directory?) What if sdXY already has a boot directory?

Q2  then the "grub-insall" creates .mod files in  /mnt/boot/grub in the live-cd file tree (with root at mnt), but on sdXZ file tree it is installed to /grub. BUT when the MBR is written wont the "prefix" be set to (sdX,Y)/boot/grub instead of (sdX,Z)/grub

> A Only If You Have a Separate /boot partition.
If you have a separate /boot partition run these commands. Most users do not have a separate /boot partition and should go to the normal partition section. sdXY is the main partition. sdXZ is the boot partition.
Code:
sudo mkdir /mnt/temp /mnt/temp/boot  
sudo mount /dev/sdXY /mnt/temp  # Mount the main Ubuntu partition. Example: sudo mount /dev/sda5 /mnt/temp
sudo mount /dev/sdXZ /mnt/temp/boot  # Mount the /boot partition. Example: sudo mount /dev/sda6 /mnt

Q3 Here you create /mnt/temp/boot in the live-cd file tree, but when you mount /dev/sdXY don't you loose access to the "boot" directory. Then if sdXY's file tree doesn't have a /boot directory the mount will fail?

---

### Post by samcot on 2011-03-22
May I offer [Rescatux and Super Grub2 Disk]("http://www.supergrubdisk.org/")?

---

### Post by oldfred on 2011-03-22
+1 on samcot's supergrub links. They should work.

This is from my notes:

If separate /boot
$ sudo mount /dev/sda2 /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

You mount the main partition which normally includes the /mnt/boot within the /mnt, but when it is a different partition you have to tell it explicitly where /boot is. In my example you do not have to create a mount point as the /mnt is a standard default.

---

### Post by b0b138 on 2011-03-23
First thing to understand is how linux accesses partitions.

Lets assume you've got three partitions on one disk. These will be referred to as sda1, sda2, and sda3.  sda is the disk, the number is the partition. (if you had 2 drives, the second would be sdb)

Now in windows, everything is c: d: and so on.

In linux, it all starts at / (called root)  This is kind of the equivalent of c:...barely.  So what linux allows you to do, is have various folders on different partitions if you wanted.  If windows had a boot folder and you wanted it on a different partition/disk, it would then be d:\boot or e:\boot. But on linux, its always /boot. It doesn't matter where you have boot mounting, theres a separate file that says what is mounted where.


To answer your questions... the first partition on the disk (sda1) is the same whether you're booted to the disk or a live cd. To access it you have to mount it.

sudo mkdir /mnt/boot is just creating an empty folder so you have somewhere to mount a partition to.

sudo mount /dev/sdXY /mnt/boot is mount that partition to the folder that was just made so you can access it. now instead of /mnt/boot being empty, you'll see whats in the sdXY partition. The sdXY is your /boot partition. You also have to mount the main root partition (you have to mount both because you have them on seperate partitions)

sudo grub-install --root-directory=/mnt /dev/sdX   is running the grub-install command, --root-directory is letting it know where your / partition is mounted, and /dev/sdX is telling it what disk to install grub to. 

hope this helps some

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) has all the info

---

### Post by mattrixx on 2011-03-23
Perhaps I should have labelled this how does mount work?
But it is also how does grub2 decide the value of its "prefix" variable?

Thanks bob,
Actually sdXZ is the boot patition and its the second mount that I dont understand

In the first case,
mount sdXZ to /mnt/boot, then
mount sdXY to /mnt

so are the files in /mnt/boot on sdXY or sdXZ?

In the second case,
mkdir /mnt/temp/boot in the live-cd file tree
mount sdXY on /mnt/temp, then
mount sdXZ on /mnt/temp/boot 

So where are you mounting sdXZ, on boot in the live-cd file tree where you created it or in sdXY's file tree?

oldfred:
I see the same problem,
grub installs its .mod files to (root-directory)/boot/grub
ie /mnt/boot/grub in the live-cd file tree

ie /boot/grub in sda2's file tree
ie /grub in sda1's file tree

when grub writes the MBR on sda what is the "prefix" variable set to?
(some partition )/boot/grub ?

which is either,
(sda,2)/boot/grub    which doesn't exist or
(sda,1)/boot/grub    which doesn't exist either.

---

### Post by oldfred on 2011-03-23
I think you are mixing up the install of grub to the /boot partition where it already is, to the install of grub to the MBR.

The grub install command is to install the boot loader to the MBR of the drive. But the MBR has to know where the grub files and kernel are which is in /boot.

 GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

To actually install grub to the boot partition you have to run, which downloads the grub files & sets them up:
sudo apt-get install grub-pc grub-common

This also installs grub to the MBR.
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by mattrixx on 2011-03-23
> **oldfred said:**
> I think you are mixing up the install of grub to the /boot partition where it already is, to the install of grub to the MBR. 

Sorry oldfred, I wasn't very clear;  I was talking about the .mod files etc that "grub-install" creates at the same time as writing the MBR. Both of these are done by "grub-install".
will edit my post

---

### Post by oldfred on 2011-03-23
If you want to reinstall grub2, you can do this. We normally have it doen from a chroot as there are system problems. You have to have internet as uninstall will work, but system is not bootable until new files are downloaded from internet. 

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
kansasnoob- full chroot one line version with &&----
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by mattrixx on 2011-03-23
Thanks for that oldfred,
Grub2 is a thing of the past, I've managed to get Grub legacy working.

As I said in the beginning, this thread was more about understanding the instructions.

I still cant see how either of these code segments can possibly work,

1
$mkdir yippee yippee/whoopy
$mount /dev/sda1 yippee/whoopy
$mount /dev/sda2 yippee

2
$mkdir yippee yippee/whoopy
$mount /dev/sda2 yippee
$mount /dev/sda1 yippee/whoopy

---

### Post by oldfred on 2011-03-23
/ is the main install. Some actually with servers install many of the folders off root to separate partitions.

Then to mount all the folders you have to separately mount each folder into the root mount or you do not have a full system.

Explaination of file structure
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
[http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)

---

### Post by mattrixx on 2011-03-24
> **oldfred said:**
> 
Then to mount all the folders you HAVE to separately mount each folder into the ROOT mount 



I disagree, you can mount partitions on any "legal" directory you want, not just in the root.
In my case I'm mounting on yippee and whoopy, I'm just not telling you where in the file tree they are. I see no need for absolute paths.

What makes a directory "legal" I'm not sure. Seems to be different for different versions of *nix.

---

