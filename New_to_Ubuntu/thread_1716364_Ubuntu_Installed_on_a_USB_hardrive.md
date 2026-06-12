---
title: "Ubuntu Installed on a USB hardrive"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by kitsuneclem on 2011-03-28
is it possible to install It on a USB hardrive

early last night i was installing ten-point ten and My USB hard drive showed up on the install partition manager

which made me wonder:

Is it possible or rather Is it Practical to install Ubuntu on a USB hard drive

(i post this here cause IM an absolute greenhorn when it comes to Ubuntu

---

### Post by Nickjpost on 2011-03-28
Yes, though it is best to make sure that your USB hard drive is at least 16G. You can use that drive to boot your Ubuntu OS from ANY computer. Pretty nifty, yeah?

---

### Post by kitsuneclem on 2011-03-28
> **Nickjpost said:**
> Yes, though it is best to make sure that your USB hard drive is at least 16G. You can use that drive to boot your Ubuntu OS from ANY computer. Pretty nifty, yeah?
320Gs actually 

 Kool  ty I'll have to do that some time :)

---

### Post by I2k4 on 2011-03-30
My mistake, deleted.

---

### Post by eriktheblu on 2011-03-30
Only thing to watch out for is it overwriting the MBR of your primary disk.

---

### Post by C.S.Cameron on 2011-03-30
Step by step for installing 10.10 on USB drive:

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
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "NTFS file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
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
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

