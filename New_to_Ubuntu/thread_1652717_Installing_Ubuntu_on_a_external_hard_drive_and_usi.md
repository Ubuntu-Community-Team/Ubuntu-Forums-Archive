---
title: "Installing Ubuntu on a external hard drive and using it for other things as well"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by saxman66 on 2010-12-25
I have a Western Digital My Book 3.0 2TB external hard drive. I want to install Ubuntu, install various windows programs like word, and store music and video files onto it. Is this possible/realistic? How would I go about doing so. I would appreciate a detailed guide if possible. Thank you for you help in this matter.

---

### Post by oldfred on 2010-12-25
Yes & no.

You can install Ubuntu to the external drive and store all your data. You can store data in NTFS format that window and Ubuntu will read. But Ubuntu uses linux format for its system, and window programs do not run in Linux. 

If you want windows programs you need windows. Some windows programs may run or only run partially in wine. Some programs like Firefox, Thunderbird, & OpenOffice have both native Windows and Linux versions, so you can install essentially the equivalent program in both windows & Ubuntu.

Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by C.S.Cameron on 2010-12-25
The following step by step is for installing Ubuntu 10.10 to USB device and leaving space for Windows.
While booting windows from the internal drive you should be able to install programs to the usb device rather than to C/Programs.
This is for 16GB drive, adjust your partition size to suit.


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
(Optional swap space, allows hibernation)
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

### Post by amjjawad on 2010-12-26
> **saxman66 said:**
> I have a Western Digital My Book 3.0 2TB external hard drive. I want to install Ubuntu, install various windows programs like word, and store music and video files onto it. Is this possible/realistic? How would I go about doing so. I would appreciate a detailed guide if possible. Thank you for you help in this matter.

Check my signature (Howto avoid Wubi). There's a full guide of howto install to an external HDD.

However, I'd recommend to read oldfred's post carefully before you go further.

Thank you :)

---

