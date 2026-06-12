---
title: "Uninstall Ubuntu l / reinstall dual boot"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by visionman on 2010-08-13
Hi, I have installed Ubuntu Hardy version 8.10 as the main Operating System on my computer, ( full disc install). I have made a mistake and want to dual boot using XP Pro as the main system and Ubuntu as the second system. Can I do this? I am an absolute beginner, with Ubuntu, Linux, I have the book &#8220;beginning Ubuntu Linux,&#8221; as a reference. Although there is information regarding dual boot systems , nothing as specific as the issue I have described here. I can follow the instructions in the book for creating a partition from an XP installed O/S, for dual booting. The book suggests that XP likes to be the ist system and Ubuntu is happy operating as a second unit. Any suggestions how I should proceed? I have Acronis true Image 2010 if that is any help with this issue Any help resolving this issue welcomed.
 
Visionman

---

### Post by Paul820 on 2010-08-13
Yes you can. If you already have windows installed, just back-up any data you have on windows, defrag the drive and then put the ubuntu cd in. On the partitioning page you can choose to install alongside windows by specifying how much space you want ubuntu and windows to have. You can share it equally or give more to windows or ubuntu, it's up to you.

There is a newer version of Ubuntu than 8.10

---

### Post by jonnywombat on 2010-08-13
The process to achieve what you want is quite simple, but takes a while...

You will need a windows disc and an unbuntu disc before you start.

First do you have any data you want to keep? if not then the easiest way to proceed is to insert your windows disc and install. Make sure when setting up your NTFS partition you first format the whole disk, and leave some free space, say 20 or 30 GB, to use later for ubuntu.

Follow the windows installation process through to the end.

Once complete grab your ubuntu CD (why not upgrade to 10.04) and install this into your free space left over from the windows installation.

Grub will do it's stuff and when you boot up the machine you will get an option screen so you can choose which OS to boot into.

You can install windows second, but you run into problems and you will have to install GRUB separately to set up your dual boot. There are many threads on that subject already.

HTH

Jonny

---

