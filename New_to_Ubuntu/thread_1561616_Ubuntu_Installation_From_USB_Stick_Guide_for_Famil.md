---
title: "Ubuntu Installation From USB Stick Guide for Family/Friends to use."
date: 2010-08-26
forum: New to Ubuntu
---

### Post by mikodo on 2010-08-26
Hello everyone,

I am a casual user I guess, not very experienced and not having the time to learn, too much of the techy stuff.

I want to install 10.04 on flash drives, to give to family and friends to try and  if they want, install on their HD's.

Before rushing down a wrong path/guide and screwing up ... again ...  would this be a good one for this:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Thanks.  :)

---

### Post by sikander3786 on 2010-08-26
The easiest way to create Live USB I have found is via [Unetbootin]("http://unetbootin.sourceforge.net/"). It is compatible with both Windows and Linux. Only you need an image and a USB drive. It can also download the distro image itself if you don't have one. No extensive knowledge required.

And yes there is a USB creator in the System >>> Administration >>> Startup Disk Creator.

---

### Post by mikodo on 2010-08-26
> **sikander3786 said:**
> The easiest way to create Live USB I have found is via [Unetbootin]("http://unetbootin.sourceforge.net/"). It is compatible with both Windows and Linux. Only you need an image and a USB drive. It can also download the distro image itself if you don't have one. No extensive knowledge required.

And yes there is a USB creator in the System >>> Administration >>> Startup Disk Creator.
Thanks,

I'll look at these options also before proceeding.

Mike :)

---

### Post by C.S.Cameron on 2010-08-26
You can do a Full install to a stick 4GB and over, This will be updateable just like a hard drive install but you can not use the stick to easily install ubuntu to another machine.
Or you can use the start up disk creator from the Live CD and  select the persistent option that will save most changes. It will not allow kernel upgrades. You need a 1GB stick for the basic install and 2GB or larger for a persistent install. Persistence files are limited to 4GB.

Full install:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

### Post by mikodo on 2010-08-26
C.S.Cameron, 

Thank you for the clear and concise instructions. As I see it, I will need to use the start up disk creator from the Live CD option, to allow an install on others' computers, if they wish.

It was very nice of you, to go to the trouble to write all this, in sequence.

It is very helpful. 

Aaah Vancouver!  I have a brother and family living in Horseshoe Bay!  ;)


Mike
Saskatoon.

EDIT: Maybe I'll give them the full install USB stick first. If they like it, I'll offer to dual boot install to their HDD's myself, so as to not let them run the chance of loosing Windows for the time being! So, I will make one start up disk creator, to work with myself.

Thanks again!

---

