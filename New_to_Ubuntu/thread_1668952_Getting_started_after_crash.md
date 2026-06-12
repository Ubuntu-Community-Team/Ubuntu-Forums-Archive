---
title: "Getting started after crash"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Engineer65 on 2011-01-17
Working with ubuntu for about 3 weeks.  Finally had it up and running pretty good after working thru themes, sound, lan, and installing programs.  Trying to install GnuCash and having problems.  Seems like I can't install enough other programs to run it.  Finally got GLIB installed ok, then Guile installed ok, but then it wanted SLIB and indicated it was not installed.  I looked in synatics and it showed the main SLIB installed so I can only surmise that it wants an associated program that is not loaded.  The installation asked the question "is SLIB installed?".  I finally decided that it was a question that I needed to answer.  I typed "y" but terminal indicated that was not a valid instruction.  So I tried "yes" and apparently that was a mistake.  "Y's" suddenly appeared down the left side of the terminal screen and just kept running.  I could not make any control work and could enter no command.  I finally used reset button on computer.  It booted back to the "Ubuntu" screen and hung up.  Pressing keys on the keyboard went to a black screen with instructions streaming on it.  They were in a loop of some sort.  Tried booting with "recovery'" but that did nothing either.  I have tried some instructions in the terminal screen that was supposed to get me back to default setting like when I started but that did not work either.  Any ideas what I did??
 
If I have to reinstalled Ubuntu will the files I added to it and programs I added to it still be there or will the install erase them.  Also can I reinstall without any uninstall of Ubuntu?  Think I am too use to wizards with windows.
 
THanks for any help!!

---

### Post by fabricator4 on 2011-01-17
> **Engineer65 said:**
> 
If I have to reinstalled Ubuntu will the files I added to it and programs I added to it still be there or will the install erase them.  Also can I reinstall without any uninstall of Ubuntu?  Think I am too use to wizards with windows.

It sounds like you are doing things the hard way! Many Windows users find Ubuntu easier to use once they get their head around a few differences.

If I can make a couple of suggestions...

Maybe stay with release 10.04 LTS.  LTS stands for long term release; it's very stable and reliable, and will be supported with security and other upgrades for three years from release.  10.10 includes some support for the latest hardware (supposedly) but it seems to be giving the uninitiated more than a few headaches.  I'm running 10.04 here and won't upgrade unless I really have to, and probably even then not before 11.04 is released.

Secondly, all the packages you will really need can be installed using the Ubuntu software center.  I just installed GNUcash to see and it installed flawlessly first time here, on my EeePC.  Click on Applications (top left) then click on Ubuntu software center and find the package you want to install.  Doing it this way will ensure that all dependencies (if any) get installed at the same time.

It sounds like you are downloading the Debian package files and installing them manually. Full marks for effort, but you don't have to make it that hard on yourself just starting out.  Learn to walk before you start building a moon rocket. I'm not trying to be smart here, I think you've probably learned a lot in a short amount of time, but I'm also not surprised that you shot yourself in the foot.  Write it off to experience, and look for the easy ways before the hard.  If it seems hard then ask here. Ubuntu was designed to be easy to learn (for XP users in particular).

To your specific questions, I don't think you should try to recover that installation.  There seems to have been too many unknown changes that have occurred and it might take much longer to fix than it took to break.  You might be able to get it to boot, but you'd always be waiting for the other shoe to drop.

No, your installed programs and data will not be saved: I suggest a full install with a format of the partition.  You might also consider a partition for your home directory only, that way future upgrades do not risk data or user settings, and a single work partition lends itself to backups rather well.

If you want to keep any data, the best thing would be to boot off the live CD, then copy /home/username/* to an external device.

Chris

---

### Post by Engineer65 on 2011-01-18
Thanks for the reply. Will take your suggestion into serious consideration.  Have Ubuntu on separate hard drive but making a partition for "home" still might be a good idea if I can figure that out OK.

---

### Post by fabricator4 on 2011-01-18
> **Engineer65 said:**
> Thanks for the reply. Will take your suggestion into serious consideration.  Have Ubuntu on separate hard drive but making a partition for "home" still might be a good idea if I can figure that out OK.

It's not difficult, though a bit confusing the first time you do it.  You actually need to set up a third partition, which is the for the swap pages.  When you start the installation you will get to the point where it asks you which partition to use.  At this point you select "manual" configuration and make sure you have the correct drive selected if you have more than one.  Delete the existing partitions (probably two of) and make the following partitions:

partiton 1: 30 Gb, partition type ext4, mounts to /, and the boot loader is to be installed.

partition 2: The rest of the drive less the swap partition, ext4, mounts to /home.

Partition 3: The rest of the drive to the end- it should be at least as large as the amount of memory you have in your machine, partition type is swap, no mount point is required.

At this point you can resize the partitions if you wish to fine tune them.  30 Gb should be ample for the operating system, or even 20 Gb.  I'm a bit biased because I run 10.04 on a machine with only 8 Gb of SSD drive.

Next click the tick button to make the changes to the HDD.

In the next part of the installation make sure you have this drive selected if you have more than one in the machine.

Once you finish the install you will have a brand new Ubuntu machine.  /home will still be where you expect it to be in the file system as the use of the separate partition will be completely transparent to you.

If you need help recovering the data, desktop, and application configuration files currently on the HDD start another thread on this topic. It's also not difficult, just confusing the first time since you will have to boot off the CD and mount the hard drive so you can copy the data to an external device.

Chris.

---

