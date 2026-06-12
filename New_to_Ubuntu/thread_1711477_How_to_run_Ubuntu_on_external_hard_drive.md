---
title: "How to run Ubuntu on external hard drive"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by larrymo on 2011-03-21
Reply to
Install Ubuntu on an external hard drive
I tried Ubuntu from a Live CD and I was really impressed. I really want to install it now and play with it and slowly convert to it. The problem is, I don't have too much empty space on my laptops hard drive. I have about 20GB of space left. I want to do one of two things:

1. Install Ubuntu on an external hard drive and have it run off of that. Has anyone done this and if you have, did you notice and noticeable performance bottlenecks due to the USB/Firewire interface?

2. I can also add a partition to my hard drive for all my personal data, install Ubuntu on the same hard drive, and have both Windows and Ubuntu share the same personal files off of the new partition. This way I can go back and forth between the two OS's very easily. Are there any issues with this?

I want to know what the experienced users here would recommend and if there are any problems I will run into. 

I need advice on one more thing and that is how much space to allocate for the swap, ext3 (I think that's what it was called) and whatever other partition I will need for Ubuntu. My system has 2GB of ram. I will do some development, office work, surfing, CAD design (if possible), DVD authoring (if possible), etc...

Any help would be appreciated and please offer your advice as soon as you can. I am very eager to install Ubuntu and start working with it.

Thanks in advance.

How to run ubuntu on external hard drive

1.download a VM drive...VMware, ect.
2.downloadd ubuntu latest version...Unbutu
3.install VM program follow install advice.
 
This will run both OS systems side by side.

---

### Post by eriktheblu on 2011-03-21
> 1. Install Ubuntu on an external hard drive and have it run off of that. Has anyone done this and if you have, did you notice and noticeable performance bottlenecks due to the USB/Firewire interface?
I do this; no noticeable speed drop. The bottleneck is more likely to be the speed of the disk rather than the interface. I use USB; it runs better than the Vista install on the internal disk.

---

### Post by eriktheblu on 2011-03-21
> how much space to allocate for the swap
As a general rule, double the system memory.

EXT3 is a file system format. EXT4 is a bit better so I would recommend that instead. It is available from 9.04 on.

For the file system partitions, a frequent tactic is to have separate partitions for / and /home. Any part of the file system can be designated to whatever partition you like, but beyond the dedicated /home, the functionality diminishes.

With Ubuntu, you can get away with 10-20 GB for /, and I wouldn't bother with more than 30. With / and swap, you can allocate the remainder to /home, or leave unformatted space between partitions for future expansion.

If you are going to make it a permanent install, I suggest creating a small (~256 MB) EXT4 partition on the internal disk to use as /boot. This should allow you to continue to boot to Windows even if the USB drive is not connected. An Ubuntu install will alter the MBR of your primary disk, and may cause errors otherwise.

Personally, I physically remove the internal HDD when I install to USB to prevent and modification to it.

---

### Post by kseise on 2011-03-21
> **eriktheblu said:**
> Personally, I physically remove the internal HDD when I install to USB to prevent and modification to it.

I will second this.  I have a company laptop that I have velcroed an external onto.  I set the BIOS to boot from USB if detected.  Under normal conditions, the USB drive blends in with the laptop lid and just sits there.  When I need Linux, it runs just fine.  When I first set it up though, I left the hard drive in the laptop and screwed it up.  

There is a CAD program out there call DraftSight which does pretty decent CAD and will read and write dxf and DWG files.  Nothing else that I know of will read and write DWGs for free.

---

### Post by C.S.Cameron on 2011-03-21
Step By Step for install to External HDD follows, adjust partition size to suit, those shown are minimum:

Check MD5SUM of the Ubuntu iso file.
Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 400MB.
Location = Beginning.
"Use as:" = "NTFS file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 2.77GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 600MB, Beginning, Ext2, and Mount point = "/home" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.

---

