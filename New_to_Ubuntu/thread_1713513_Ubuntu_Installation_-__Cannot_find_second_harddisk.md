---
title: "Ubuntu Installation -  Cannot find second harddisk."
date: 2011-03-24
forum: New to Ubuntu
---

### Post by spinedk on 2011-03-24
Hey,

First of all, i absolutely love Ubuntu. However i am having some "basic" problems with the installation of ubuntu 10.10 desktop. I can only find one harddrive when i am installing ubuntu (booting from USB).  However i can see in GParted, that the other drive is their - however not formattet  and not partionet and can therefore not use it. 

I am completely new to Ubuntu. Hope some of you out there can help me out with this - i know - a very basic problem.

Beforehand . thanks you.
Kasper
[EMAIL="spinedk@gmail.com"]spinedk@gmail.com[/EMAIL]

---

### Post by sadiqdude on 2011-03-24
try to make that hdd as master or else use partition magic and format ur hdd completly:D:D:D

---

### Post by fabricator4 on 2011-03-24
> **spinedk said:**
> USB).  However i can see in GParted, that the other drive is their - however not formattet  and not partionet and can therefore not use it. 


What is supposed to be on the second hard drive?  Have you run chkdsk on all Windows (NTFS, FAT32) partitions?

Try the installer, go into select partitions manually, and see if the program will see the second drive (you have to scroll down the list of devices and select sdb or whatever the second drive is designated).

The installation will not change anything on the hard drive until this point - you can always back out or even turn the machine off without making any changes. It seems a characteristic of this problem that Gparted cannot see the partions, but the partitioner in the installer can.  The partitioner in the installer will not fix the problem with respect to Gparted from what I can gather - People have reported the problem _after_ installing Ubuntu.

A common reason for this happening is a conflict (or corruption) of GUID partition information after windows has written MBR information.  Have a look at [this post]("http://ubuntuforums.org/showthread.php?t=1510017").

You should also google "gparted not finding partitions" as there seems to be other information out there as well.

BTW, if you're using the 10.10 maverick LiveCD you should specify the partitions manually when you do install.  Do not use the "Install alongside another OS" option.

Chris

---

### Post by Dutch70 on 2011-03-24
Hi and welcome to UF

Can you not format & partition it from Gparted?

It's better to do that before installing. Also, you may want to unplug any hdd you're not installing Ubuntu onto, just to be safe.

---

### Post by spinedk on 2011-03-24
Hey - thank you - i found out how to partition it.

However, now i see on the second harddrive that it as created something called "Lost and Found" and i 7gb. I cannot access this folder. 

What is this "Lost and Found" folder?

---

### Post by Dutch70 on 2011-03-25
Glad you got your partitioning straightened out. :)

Remember, Google is your friend. I found quite a bit of info on the lost & found folder by doing a search for...
> lost and found folder ubuntu

---

