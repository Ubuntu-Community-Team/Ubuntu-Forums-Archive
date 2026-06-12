---
title: "Wiping the harddrive from within Ubuntu--possible?"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by kelly2thec on 2009-03-31
Hello all, thought I'd put this here since it's been ages since I've done much troubleshooting/computer savvy acts.  I have an old laptop that runs XP that I've just installed Ubuntu on, downloaded all the updates, etc.  Now, a while back I heard from a friend that it's a pretty simple process to reformat the harddrive from within Ubuntu (as though using a boot disk).  But, for the life of me, I can't figure out how to do it.  I searched and read several things, but most of the language was beyond me (I am completely new to Linux/Ubuntu/etc.)

So, yes.  I desire to reformat the drive to erase all traces of Windows and any of the files that were once there, I just want a clean machine with Ubuntu on it.

(Of note: my computer does not have a working optical drive.)

Any and all help would be appreciated. :KS

---

### Post by Cl0ud9 on 2009-03-31
It sound like ou want to use Gparted to reformat a windows partition. It can be installed in Ubuntu with the command:
```

sudo apt-get install gparted

```

It you completely wanted to wipe a disk or partition you could use the following command **at your own risk**:
```

sudo dd if=/dev/zero of=/dev/*device_name*

```
**This command would write zeros on your whole drive and should only be used if you know exactly what you are doing.**

---

### Post by sgosnell on 2009-03-31
I you format the drive, there will be nothing left on it - not Windows, not Ubuntu, not anything.  You will be left with an inoperable computer, at least until you can get a boot device to reinstall an OS.  One possibility, if you have no CD drive, is to prepare an install on a USB drive, boot from that, format the HD, and then reinstall Ubuntu.  Make sure the USB drive is bootable before you do anything foolish, though.

If you did the Ubuntu install the right way, all the Windows files are gone anyway.  If you used the entire disk for the install, the partitioner formatted the drive, and Windows is completely gone.  OTOH, if you left a Windows partition, you can format that with no problem, as long as you're **absolutely sure** which partition you're formatting.

---

### Post by rockin_goliath on 2009-03-31
[http://pubpages.unh.edu/~asj9/images/install4.png]("http://pubpages.unh.edu/~asj9/images/install4.png")

It will format the disk for you during the installation process. Just make sure you have saved all your important data first.

---

### Post by asmoore82 on 2009-03-31
Is it currently a dual boot with both Ubuntu and XP or did you already replace XP with Ubuntu?

if #1 - I think you want GParted to wipe the XP partition - see below

if #2 - You are already done.

gparted is in the repos:
```
sudo apt-get install gparted
```
and needs to be run with root privilege:
```
gksudo gparted
```

---

### Post by kelly2thec on 2009-03-31
Thanks for the advice thus far and apologies for not being more specific.  What I am attempting to do is get rid of my Windows partition, as was surmised here.  At the moment (via Gparted) my partitions look like this

partition: /dev/sda1; filesystem: ntfs; mountpoint: /boot, /host; size: 92.96 GB; used: 90.48 GB; unused: 2.48 GB; flags: boot

there's also another partition called "dev/sda4" which has no filesystem and is 203.95 MB?  no idea what that is...

In any case, where should I go from here?  Create a new partition, install ubuntu on it, and then erase the old?  I definitely need some very simple instructions, apologies...

---

### Post by asmoore82 on 2009-03-31
did you do that "Install Ubuntu inside XP" option??

---

### Post by zvacet on 2009-04-01
@ 

To reformat your HDD you can use Ubuntu live CD from usb.[Here]("https://help.ubuntu.com/community/Installation/FromUSBStick") is guide how to put Ubuntu on usb.Other solution is to put [Gparted on usb.]("http://gparted.sourceforge.net/liveusb.php")

---

### Post by kelly2thec on 2009-04-01
Hello again.  Thanks for the new tips, I went through everything you guys said and did the following:

-Made my thumb drive into a boot disk.
-Attempted to boot from said thumb drive.

Here is where I hit a snag.  My BIOS has no option to boot from a thumb drive, only HDD, FDD, LAN, and CD-ROM.  I tried booting from FDD, no luck.  And when it goes from FDD -> CD-ROM -> LAN -> HDD it only becomes angry when it can't successfully test the optical drive.  I flashed BIOS, and it didn't help, no new options.

My failure.  It is epic.

:sad:

Alternative advice?  I just want to wipe the horror that is XP and random junk files and programs from this machine and start clean with Ubuntu.

---

### Post by presence1960 on 2009-04-01
> **kelly2thec said:**
> Hello again.  Thanks for the new tips, I went through everything you guys said and did the following:

-Made my thumb drive into a boot disk.
-Attempted to boot from said thumb drive.

Here is where I hit a snag.  My BIOS has no option to boot from a thumb drive, only HDD, FDD, LAN, and CD-ROM.  I tried booting from FDD, no luck.  And when it goes from FDD -> CD-ROM -> LAN -> HDD it only becomes angry when it can't successfully test the optical drive.  I flashed BIOS, and it didn't help, no new options.

My failure.  It is epic.

:sad:

Alternative advice?  I just want to wipe the horror that is XP and random junk files and programs from this machine and start clean with Ubuntu.

Why don't you back up data you want to save and use the Live CD. Boot the Live Cd and choose guided install: use entire disk. This will install Ubuntu to your HDD wiping everything in the process.

Or as long as you didn't use wubi to install Ubuntu use gparted to delete the XP partition. Then you can add the unallocated space to your Ubuntu partition or create a partition for data storage.

---

### Post by sgosnell on 2009-04-01
I agree.  Back up your data files, and do a fresh complete install from the live CD, using the entire disk.  That should get rid of XP, and use the currently unused space.  Everything should more efficient.

---

### Post by toehead2 on 2009-04-01
I believe the original poster said that his optical drive didn't work so the live cd isn't a option.

---

### Post by presence1960 on 2009-04-01
> **kelly2thec said:**
> Hello all, thought I'd put this here since it's been ages since I've done much troubleshooting/computer savvy acts.  I have an old laptop that runs XP that I've just installed Ubuntu on, downloaded all the updates, etc.  Now, a while back I heard from a friend that it's a pretty simple process to reformat the harddrive from within Ubuntu (as though using a boot disk).  But, for the life of me, I can't figure out how to do it.  I searched and read several things, but most of the language was beyond me (I am completely new to Linux/Ubuntu/etc.)

So, yes.  I desire to reformat the drive to erase all traces of Windows and any of the files that were once there, I just want a clean machine with Ubuntu on it.

(Of note: my computer does not have a working optical drive.)

Any and all help would be appreciated. :KS

Sorry didn't see the end of post which said you don't have a working optical drive. Still no problem. Do this:
1. if gparted is not already installed open a terminal and run ```
sudo apt-get install gparted
```
2. Open gparted either in terminal: ```
sudo gparted
``` or System > Administration > Partition Editor
3. Make sure the XP partition is unmounted then delete the XP partition in gparted by right clicking on it and choose Delete. Click apply. 
4. You will not be able to add this space to your Ubuntu partition because it (Ubuntu) is mounted. Since your BIOS will not boot a USB drive you must have an optical drive to boot the Live CD so you can add the free space from the former XP partition to the Ubuntu partition.
5. If this is not possible you can create a data  storage partition from gparted. Right click the unallocated space and choose new. A dialogue box will come up. Choose ext 3 as file system and click apply. You will now have a data partition where XP once resided.

P.S. out of curiosity if you can't boot a usb drive and you have no optical drive how did you install Ubuntu? I know an iso can be mounted, especially in windows with the likes of Alcohol 120%.

---

### Post by egalvan on 2009-04-01
> **kelly2thec said:**
>   What I am attempting to do is get rid of my Windows partition, At the moment (via Gparted) my partitions look like this

partition: /dev/sda1; filesystem: ntfs; mountpoint: /boot, /host; size: 92.96 GB; used: 90.48 GB; unused: 2.48 GB; flags: boot

there's also another partition called "dev/sda4" which has no filesystem and is 203.95 MB?  no idea what that is...

In any case, where should I go from here?  Create a new partition, install ubuntu on it, and then erase the old?  I definitely need some very simple instructions, apologies...

It appears you have a wubi install, so wiping the XP partition will also wipe Ubuntu.

If erasing the entire drive, and re-installing Ubuntu is what you are wanting...
then here are a few links that may be of help...

as usual, BACK UP IMPORTANT DATA you may have on that drive FIRST.


[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

This next one has this as one of the reasons to use it
**your laptop doesn't have a CD or a floppy drive.**
which seems to fit you to a "t"

*Install GNU/Linux without any CD, floppy, USB-key, nor any other removable media*
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)


[http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive](http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive)


Straight from the Community Docs:
[I]Installing without a CD drive over a network. 
Installing without a CD drive or network capabilities from a hard drive
Installing from Windows without using floppies, a CD, or any other removable media. 
Installing using a spare partition from an existing Linux system to house the Ubuntu CD image[/I]
Surely there will be an option to suit your needs
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

