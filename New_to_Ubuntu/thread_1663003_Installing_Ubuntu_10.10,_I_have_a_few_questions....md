---
title: "Installing Ubuntu 10.10, I have a few questions..."
date: 2011-01-09
forum: New to Ubuntu
---

### Post by maxin11p on 2011-01-09
I'm about to install Ubuntu 10.10 onto my system, but I need to know what I should select for the "device for boot loader installation" thing.

And how do I create and assign a Swap partition?

And how do I make it so I can dual boot with Windows XP?
(I have two Primary partitions made already, one with XP, one blank)

---

### Post by Kasami on 2011-01-09
Well if you have your partitions setup, if you load up the live CD, choose install and then choose install ubuntu alongside the image should indicate windows next to ubuntu. Then hit install. It will prompt you about swap and reccomends. If you want to do it manually it is a bit more complicated.

---

### Post by maxin11p on 2011-01-09
> **Kasami said:**
> Well if you have your partitions setup, if you load up the live CD, choose install and then choose install ubuntu alongside the image should indicate windows next to ubuntu. Then hit install. It will prompt you about swap and reccomends. If you want to do it manually it is a bit more complicated.
It shows files next to Ubuntu. And it shows Ubuntu in sda3, where my hard drive only has sda1 and sda2 for partitions. Should I only have one partition on my hard drive, and let the installer make a second partition?

---

### Post by candtalan on 2011-01-09
> **maxin11p said:**
> I'm about to install Ubuntu 10.10 onto my system, but I need to know what I should select for the "device for boot loader installation" thing.

And how do I create and assign a Swap partition?

Is your target system unusual? It is normal to have  the boot loader in the normal boot sector afaik, this is very likely to be the front of your first drive. Often this is the only hard drive. On Windows machines this is usually drive C:, Linux based systems may see this as drive 'a' (sda) and the first partition would be  say, sda1. The boot loader would normally default to boot sector on sda drive.

The loader will normally point to boot files residing in the (Ubuntu) installed partition. If the installed partition (system) is say, sda5, the system (/) will be in sda5, which will include a directory such as /boot containing the boot configuration (grub2), which then also controls how other OSs in the machine boot, including for example, Windows.
hth

With installing 10.10 please be aware of
Bug #659106: 'Maverick installer lost Windows partitions'
[https://bugs.launchpad.net/ubuntu/maverick/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/maverick/+source/ubiquity/+bug/659106)

---

### Post by maxin11p on 2011-01-09
[IMG]http://s271.photobucket.com/albums/jj155/maxin11p/?action=view&current=installing.png[/IMG][http://s271.photobucket.com/albums/jj155/maxin11p/?action=view&current=installing.png ]("http://s271.photobucket.com/albums/jj155/maxin11p/?action=view&current=installing.png")
(I'm a total newb. Can't even get an image to work right...)
Is that okay for installing, and will it dual boot? (sda1 is my Windows partition, sda2 is my empty partition I want to install on)

---

### Post by Kasami on 2011-01-09
That will work and when you click okay it will tell you off for not allocating Swap, =D

---

### Post by maxin11p on 2011-01-09
> **Kasami said:**
> That will work and when you click okay it will tell you off for not allocating Swap, =D
Hahaha. I know.
For some reason, I seriously laughed at your reply...

How much Swap space do you recommend I make?

---

### Post by Kasami on 2011-01-09
It's up to you, I have about 1-2 gigs running but I have a larger hard drive than you.

I would suggest 1 gig, info about swap and choosing it for Ubuntu can be found here:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Kasami on 2011-01-09
Wait a sec, apparently there's a known bug about "installing beside" so I would hold off on the installation if you haven't started yet.

---

### Post by Quackers on 2011-01-09
I wouldn't recommend that you use the "install alongside" option with the 10.10 installer! It has been know to eat existing operating systems!!!! The safest way is to create the partitions yourself by choosing the "specify manually" option in the installer.

---

### Post by candtalan on 2011-01-09
> **Kasami said:**
> Wait a sec, apparently there's a known bug about "installing beside" so I would hold off on the installation if you haven't started yet.

The bug I hit was this one:
Maverick installer lost Windows partitions
[https://bugs.launchpad.net/ubuntu/maverick/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/maverick/+source/ubiquity/+bug/659106)

My own tests showed it worked ok for the normal resize and also for the Advanced (manual ) allocations. I distribute 10.10 Live CDs now, with this warning:

=========
Ubuntu 10.10 Installer Bug
Warning
Most functions in this installer work fine, and are ok. However: One particular option button in this installer will cause data damage, you are advised to avoid it if you have data anywhere on the hard drive!

During the Install Ubuntu process, and from the first of three installer options:
'Install alongside other operating systems'.

You are then offered a facility to re-size a partition to allocate drive space. The re-size facility itself has no problems, if you wish to use it please do. However, two more choices are also shown in this display in a pair of buttons: 
'Use Entire Partition' and 'Use Entire Disk'

Warning: Both of these buttons do the same thing - they use the entire disk, and any other partitions on the disk will be lost.
(Reference:    Bug #659106)
=========

hth

---

### Post by watcher6342 on 2011-01-11
i downloaded 10.10 and then tried to install it on usb drive (16gb) when it said reboot. xp came back up. i changed it to boot from usb but it still booted xp. that was a 32bit system at work. i have 64bit win7 at home. what is my best chance of making this thing work? keep trying on 32bit xp or try 64bit at home? is there something i forgot somewhere?

---

