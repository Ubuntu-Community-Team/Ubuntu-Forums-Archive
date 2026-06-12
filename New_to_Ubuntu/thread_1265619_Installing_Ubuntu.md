---
title: "Installing Ubuntu"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by RemmyNumber7 on 2009-09-13
Having problem installing Ubuntu.I wiped and formated my Hard Drive. Put the disk in to install. And it get's to about 61%. Then it just stops, Dose the hard drive have to be formated in a special partition in order to install?? . Not even the cdrom lite will run past a % . this is a 40gig hard drive 2+ gig processor and 1.5 gig of ram. Any insight to this problem. I installed it before on this hard drive. And didn't have any problems

---

### Post by K7522 on 2009-09-13
You don't need to format before the install, since the install itself has a partition tool. Please ensure that you wrote the disk at the slowest possible speed to reduce errors, try to use -R instead of -RW CD/DVD and try the install again. 

It looks like a CD issue, but just have patience with it.

---

### Post by RemmyNumber7 on 2009-09-13
Thank you K7522 . I did change the rom now it loads to 61 % the freezes any answers for this

---

### Post by nhasian on 2009-09-13
most likely burning a CDR at the slowest speed will resolve your installation issue.  if it does not, please download the Hard Disk Diagnostic tools from your HD Manufacturer's website and see if your hard disk is functioning properly.  if you do get errors you may need to replace your HD data cables (IDE or sata ribbon) or you may have a bad hard disk.

---

### Post by sgosnell on 2009-09-13
When you initally boot from the live CD, choose to check the disk for errors.  If you have a bad burn on the CD, you'll never get an install, and bad burns are not at all uncommon.

---

### Post by RemmyNumber7 on 2009-09-15
> **sgosnell said:**
> When you initally boot from the live CD, choose to check the disk for errors. If you have a bad burn on the CD, you'll never get an install, and bad burns are not at all uncommon.
 
 
I did check the disk and there were no errors it just goes to a certain percent then stops working. usely during installing the file system

---

### Post by RemmyNumber7 on 2009-09-15
Dose the speed of the cd  rom have anything to do with making the ubuntu cd finish the instalation of the operating system???

---

### Post by RemmyNumber7 on 2009-09-15
I didn't burn the disk of Ubuntu. Just put it in the cdrom drive.

---

### Post by zeroseven0183 on 2009-09-15
You mean you have the LiveCD (brown) with you? Or did you download the ISO from the site ?

---

### Post by QIII on 2009-09-15
Can you run Ubuntu in a Live session?

Select the option to run without making changes to your system and let us know if that works.

---

### Post by RemmyNumber7 on 2009-09-16
no i have a Ubuntu disk it is 2008 bootale disk just having problems loading it

---

### Post by RemmyNumber7 on 2009-09-16
no i don't have a live disk  just a 2008 bootable disk having problems to install

---

### Post by RemmyNumber7 on 2009-09-16
Just a question?   will there be installing errors if you use a 32 bit Ubuntu os disk on a 64 bit system???

---

### Post by oldfred on 2009-09-16
The 32bit version runs just fine on 64bit systems. If your 64 bit system has more than 3GB of memory it may be better to use the 64bit Ubuntu. I have a 64bit system and have been running the 32bit versions for almost 3 years. I hae jsut installed the 64 bit to test my system but am still primarily 32 bit for now.

I bought a stack of music CD's by mistake and burn mostly coasters with them. They just are not good enough for data, though they may work for music.

---

### Post by RemmyNumber7 on 2009-09-17
Ok if not the 64 bit system. Can it be a motherboard why Ubuntu won't install from a cd-rom 54x .And not one i burned.That option works for QIII: Select the option to run without making changes to your system and let us know if that works. This is what it say's on the disk. Ubuntu 2008 Edition Bootable Installation CD  with a little Penguin with the word Linix under it. I don't understand why it wont fully install. Any more idea's.

---

### Post by wobin77 on 2009-09-17
Well, i had a simular problem. My problem was my wifi card. Ubuntu would just stop a certain percentage. Unplugged my wifi (linksys WUSB54G) and all installed perfect.

---

### Post by Iksf on 2009-09-17
Download a fresh ISO, burn a fresh disk, bet that solves the problem

---

### Post by egalvan on 2009-09-17
> **oldfred said:**
> The 32bit version runs just fine on 64bit systems. If your 64 bit system has more than 3GB of memory it may be better to use the 64bit Ubuntu. I have a 64bit system and have been running the 32bit versions for almost 3 years. I hae jsut installed the 64 bit to test my system but am still primarily 32 bit for now.

Absolutely. 32bit software on 64bit hardware is OK.
Although 32bit WILL access more than 4GB of RAM if it is PAE-enabled.
The Server Edition of Ubuntu 32bit is such an animal.


> I bought a stack of music CD's by mistake and burn mostly coasters with them. They just are not good enough for data, though they may work for music.

Except for a few bytes of extra information in the run-in area (which is ignored by data drives anyway),
and the "pirate-tax" added on...
there is NO difference between data and music CD-R's.
(well, OK, music CD's are available in more colors :) )


The quality of the manufacturing has FAR more to do with this.

---

### Post by RemmyNumber7 on 2009-09-19
I got it installed. I got a new problem now. Ya see i first installed it on a Pentium 2 system and a 40 gb hard drive.That system had a onboard video built in it. 
 
I tryed to install it on a penium 4 system amd processor. With a 80 gb hard drive. this newer system has an AGP in it. A geforce 6600 video card. after doing alittle research online about it. nvidea don't support Ubuntu linux 8.10 ver. Any way i found another video card ATI and they have a driver for it. Now i can't even start the computer. So i guess it's the front panel is wronge. the motherboard is ATI. I guess if i can't get the front panel it boot i'll switch to another motherboard. Anyway i thank everyone who gave me some input on the problem i had before. I found out the problem i had before was the mounts in linux.

---

