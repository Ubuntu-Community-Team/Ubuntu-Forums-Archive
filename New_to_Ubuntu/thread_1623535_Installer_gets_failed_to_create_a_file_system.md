---
title: "Installer gets failed to create a file system"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by spleenboy2000 on 2010-11-16
Absolute beginner to Linux and Ubuntu. I'm about 60 minutes into my brave new world. I have only ever used Windows.
I have a machine with Windows 7. I thought it would be great to have Ubuntu as a dual boot.  I cleared some free space on it and built a partition using the windows disk manager. The optical on my machine is broken, so I formatted the partition, extracted the 10.10 iso onto the new partition, and ran it.
The Ubuntu booted up happily, and the installer started.
On the allocate drive space page, I chose specify partition
I selected the new partion, and pressed the change button.
I changed it to an ext4 journalling file system, ticked the format the partition box and chose the mount point as root /.
I then moved onto the next screen with a map of the world, and get an error: failed to create a file system.

I dont even know where to start. Any help would be greatfully appreciated.

---

### Post by yankysunny on 2010-11-16
Have  u created a swap partition too?

---

### Post by spleenboy2000 on 2010-11-17
No. I did get a warning, but the installer said it was OK to continue, as I only have about a 5 Gig partition, and don't have any space left on my hard drive on the machine.
Do I have to create another seperate partition on the hard drive for swap space in order for the instalation to be successful.
Also, I have a 100Gig of space on my drive, but the windows partition tool would only let me build a 5 Gig partition. I defragged the disk, but it made no difference. Any ideas on any good tools that would let me take advantage of the free space on my drive, and make a bigger partition on my hard drive.
Many Thanks for the help

---

### Post by SuaSwe on 2010-11-17
I'm not familiar with your install method there - I'm assuming that you're not installing Ubuntu on the same partition that the ISO is mounted on? You can't partition and install Ubuntu on a mounted drive.

If you have a USB drive on the PC, I would suggest creating a startup USB drive, booting into the live environment ('Try before installing') and have a look at your partition using the built-in partitioning tool, GParted, to see what partitions can be used, moved, shrunk, expanded, etc. :)

---

### Post by spleenboy2000 on 2010-11-17
Yes, I have put all the instalation files on a partition in windows, and just ran the install exe. It asked me to reboot which I did, I then got a pretty purple screen with an icon which said install ubuntu, and away I went. I am trying to put ubuntu on the same partition I built which I extracted the iso onto
So is it not possible to install ubuntu without either an optical or a usb stick?
Also, when I start up Ubuntu, how do I start gparted?
Many Thanks for the help

---

### Post by SuaSwe on 2010-11-17
From my understanding of your problem, I would say that you cannot install Ubuntu the way you're describing. Basically the partition you're installing on can't be mounted (e.g. in use) when you install Ubuntu on it.

GParted is started by going to System > Administration > Partition Editor once booted into the live environment.

As long as you have a USB drive on the PC, creating and booting into a startup USB should be a doddle! See this page for details: [https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows)

By the way, is the issue now resolved, seeing as the thread is marked as Solved? :)

---

