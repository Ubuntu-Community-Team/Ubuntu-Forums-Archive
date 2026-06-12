---
title: "install on usb for real (not trail version)"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by GaretJax on 2010-09-06
I am running Ubuntu 10.04 on my computer and I wanted to install it on my 4gb USB drive.  So I followed the instructions on the Ubuntu.com download page where I was instructed to use the 'Startup Disk Creator'.  This worked great, but when I boot off the USB drive, the Ubuntu that is installed on their is running in that trail mode, and it asks me for my language each time and if I want to use trial mode or install on a computer.  Plus is doesn't appear to be utilizing all 4gb of my USB drive because I tried to download a program that was only 30 mb and it said I didn't have enough room.

Can I install Ubuntu on the 4gb USB drive so that it runs in full production like it would on a regular computer drive?

---

### Post by e79 on 2010-09-06
Yes it can be done. You should be able to find all informations you need here :

[http://ubuntuforums.org/showthread.php?t=1512856](http://ubuntuforums.org/showthread.php?t=1512856)

[http://ubuntuforums.org/showthread.php?t=1494031](http://ubuntuforums.org/showthread.php?t=1494031)

[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

[http://heshambahram.wordpress.com/2010/05/05/live-usb-with-ubuntu-10-04-lts/](http://heshambahram.wordpress.com/2010/05/05/live-usb-with-ubuntu-10-04-lts/)

and here :  [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Hope this helps

---

### Post by wilee-nilee on 2010-09-06
The standard Ubuntu distro unpacks to about 2.9 gigs leaving very little space on a thumb of that size.

---

### Post by C.S.Cameron on 2010-09-06
I run 10.04 Full install on a 4GB thumb drive ok, just not lots of room for storing photos, movies etc, but you can put them on a second drive.

Attached instructions are for an 4GB drive:

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
Make "New partition size..." about 250MB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 750 MB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (0 GB), Beginning and "Use as" = "swap area" then OK.
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

### Post by GaretJax on 2010-09-09
C.S. Cameron. I like your instructions. They are straight and to the point. I did as you said, but I am wondering why the 250MB FAT32 Windows partition. After I installed it this way, there was only only 966KB used on that partition.

And I was surprised to see 2.3GB used as the base Ubuntu installation size. I think I will redo this installation on an 8GB USB drive.

---

### Post by C.S.Cameron on 2010-09-09
The FAT32 partition is for saving stuff from a Windows computer, If you only use Linux computers it is not needed.

---

### Post by GaretJax on 2010-09-10
OK. I redid the install to an 8 GB and it works great.  Thanks for all your help.

---

