---
title: "Error when trying to run installed Ubuntu from USB"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by goldenboy1 on 2011-01-12
I want to get Ubuntu to run from USB instead of dual booting I will just select boot from USB in the bios.

So when I installed to a USB and tried to boot I got the following:
Buzy Box v1.15.3 ....

(intramfs) stdin: error0

mount: mounting /dev/loop0 on //filesystem.squashfs failed Invalid arguement

can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystem.squashfs



When i installed to the usb it was listed as sdb1 if this helps

Cheers and thanks in advance

---

### Post by C.S.Cameron on 2011-01-12
What method are you using to make the bootable USB's?
Startup Disk Creator from the Live CD works well as does UNetbootin.

If you want a substitute to dual booting I would suggest a Full install to USB:

Following step by step for Full install of 10.10 to USB device, adjust partition size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
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
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by goldenboy1 on 2011-01-13
Following these steps I get as far as entering the username and passwords installation screen.  I enter in all the fields getting check marks indicating everything is ok.  But even after the files are copies and it says ready the next button will not work.

---

### Post by mikewhatever on 2011-01-13
Make sure you don't use any capital letters, spaces and special characters like %&.*,@#.

---

### Post by goldenboy1 on 2011-01-13
Not using caps got me a bit further along yet the installer crashed during configure system locales.  It says I should submit a bug report but I think the files I was asked to send may not have been saved as my live cd session crashed as well.  Oh well, I might try again while I sleep and am thinking perhaps I should try burning another copy of the live CD in case there are problems there.

---

### Post by C.S.Cameron on 2011-01-14
You might check the MD5SUM of your iso to make sure it is not corrupt:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by goldenboy1 on 2011-01-17
This is the first time I admit defeat using Ubuntu now my bios isn't even recognizing the USB drive any longer.

---

