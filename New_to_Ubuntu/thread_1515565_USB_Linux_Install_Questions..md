---
title: "USB Linux Install Questions."
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Goodkimchee on 2010-06-22
The title is a bit misleading: I'm trying to run a dual-boot system, Ubuntu 10.04 & Win7, but I'm running Ubuntu off a Usb key (Sony 4Gb). I would love to have all the graphical bells & whistles running off the key e.g. Compwiz, etc, but for some reason, not all the updates install, and Ubuntu won't let me run Nvidia drivers, or run Compwiz.  

So I'm a bit stuck. I read on pendrivelinux.com that this happens sometimes, and more work needs to be done, but they don't tell you what other work needs to be done or where to get that sort of help so here I am.  If anyone could direct me to the proper post/thread/websites to make Ubuntu run completely off usb with saves to the system, that would be just splendid.

many thanks.

---

### Post by marshmallow1304 on 2010-06-22
How did you put Ubuntu on the USB drive in the first place?

---

### Post by C.S.Cameron on 2010-06-22
If you want all the bells an whistles of a full install, update and upgrade install Nvidia drivers etc then you should probably do a full install.
You can install to flash drive just the same as to normal hard drive.
A 4GB flash drive is just about minimum.
If this is your first time doing a full install then I would recommend the following method:

Turn off and unplug the computer.
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
Make "New partition size..." about 250MB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 2.5 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (250 MB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Once you are a bit more familiar with the process you can omit disabling the hard drive, but be sure to select the root of the flash drive in "Advanced" as the destination for grub.
Swap area on this size drive is probably useless.

---

