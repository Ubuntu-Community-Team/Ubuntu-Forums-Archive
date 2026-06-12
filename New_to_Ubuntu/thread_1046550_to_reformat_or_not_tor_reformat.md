---
title: "to reformat or not tor reformat?"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by wkuace on 2009-01-21
that is the question. lol I have the 8.04 live cd and it is running perfectly in an old desktop that xp crashed on. i want to wipe xp off of it and install hardy. I'm not sure should i use gparted and reformat it to the ext3 format or just click install and let the cd do its thing?

hard drive still works i salveged files onto a usb so i know its still good.

---

### Post by taurus on 2009-01-21
If you want to use the default partitions (/dev/sda1 for / and /dev/sda5 for swap), then tell the installer to use the whole disk.  But if you want to have something like /dev/sda1 for /, /dev/sda2 for swap, and /dev/sda3 for /home, then you need to use gparted and partition your harddrive first.  Then when you get to the partition screen, use the Manual and mount /dev/sda1 to / & /dev/sda3 to /home.  Don't need to do anything with swap partition since the installer knows what to do with it.  Otherwise, mount /dev/sda2 to swap and you are all set.

The reason you want to have a separate /home so that if you have to reinstall, all your personal settings and files will be saved.

---

### Post by lifestream on 2009-01-21
Yes, why not? The install only takes 15-20 minutes! :) I was in the same situation as you a year ago, and I did it. I have not regreted since. :)

Just be sure to do a /home partition!

Yup, it's way easier if you do the Gparted thing. Pop in the liveCD, sudo apt-get install gparted, run it, and partition :) 
BTW your root  ( / ) partition only needs about 5-10 GB. Use the rest for your /home. 

If gparted complains the drive is in use, do swapoff on a terminal

---

### Post by wkuace on 2009-01-21
all gparted is showing is /dev/sda1  no /dev/sda2/5 anything do i need to create another? if so how big the computer is old and only has 18 gigs

---

### Post by boof1988 on 2009-01-21
> **taurus said:**
> But if you want to have something like /dev/sda1 for /, /dev/sda2 for swap, and /dev/sda3 for /home, then you need to use gparted and partition your harddrive first.

I just wanted to clarify something...  I think that one can create/delete (etc.) partitions during the partitioning step of the installation.  Though it may be a little more challenging (and easier to mess up) than using gparted before starting the installation process.

Someone please let me know if I am mistaken (or just plain wrong).

---

### Post by bwang on 2009-01-21
Yes, you can create partitions during the install process. With an 18 GB disk, its probably better to install everything to one partition.

---

### Post by cexcells on 2009-01-21
When you boot up from the live CD you would select install Ubuntu and follow the screens until you get to the partitioning options. If you select Manual install you have to delete all existing partitions then create a new partition (primary) say 10000 MB ext3 filesystem and / (root)as mountpoint at the start of the drive.
You will then see the large unpartitioned space remaining. Right click in the graph and select new partition and choose logical drive as type and ext3 filesystem with /home as mountpoint but leave about 4000 MB free space at the end.
Finally select the remaining 4000 MB and select linux swap as filesystem for that. 
Proceed and the system will partition and install in one go. If the screen goes dim at anytime it is the powersaving switching off the display. Wiggle the mouse or hit the spacebar to bring it back on.  :popcorn:

---

