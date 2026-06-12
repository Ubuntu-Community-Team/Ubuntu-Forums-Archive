---
title: "Does Startup Disk Creator save settings and files?"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by zer010 on 2011-01-29
I can't remember if the Startup Disk Creator in Ubuntu creates a LiveDisk that saves settings, files and installed apps.  If it does, great! If it doesn't, can someone point me to a utility that will do this?  Thanks.

---

### Post by jd2012 on 2011-01-29
Looking at the Startup disk creator's Help file, section "Requirements" its states quote:

> 
The USB drive capacity should minimally be large enough to hold the 
contents of the Ubuntu download image and any additional data you 
plan to store. The minimum recommendation is 1 GB, however 2 GB is suggested. 


Doesn't say anything specifically about saving settings, just data.
Anyone with SDC experience?

---

### Post by zer010 on 2011-01-29
I guess that about answers my question.  I guess I should've looked a little harder. Thanks.
Edit: The help file also lists Persistence as a feature.

---

### Post by zer010 on 2011-01-29
Perhaps I spoke too soon.  I created a LiveUSB with the Startup Disk Creator but the two options at the bottom, 'allocate free space to save data' was not available. I booted up the liveUSB and started doing updates which seemed to go fine. Then I went to install the restricted extras and it said there wasn't enough space in /apt/cache(?).  This is a 4GB flash drive by the way.  I thought about installing straight from disk to the flash drive, but I read that  /tmp will run up r/w cycles and could damage the flash drive......

---

### Post by [Snc] on 2011-01-29
> **zer010 said:**
> Perhaps I spoke too soon.  I created a LiveUSB with the Startup Disk Creator but the two options at the bottom, 'allocate free space to save data' was not available. I booted up the liveUSB and started doing updates which seemed to go fine. Then I went to install the restricted extras and it said there wasn't enough space in /apt/cache(?).  This is a 4GB flash drive by the way.  I thought about installing straight from disk to the flash drive, but I read that  /tmp will run up r/w cycles and could damage the flash drive......

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Then you have to choose to "store in reserved extra space" (the casper file), this also saves your network settings, FF settings, etc ...

---

### Post by zer010 on 2011-01-29
> **'[Snc] said:**
> [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Then you have to choose to "store in reserved extra space" (the casper file), this also saves your network settings, FF settings, etc ...
That's the thing, "store in reserved extra space" is not an option. It's all greyed out.

---

### Post by C.S.Cameron on 2011-01-29
If the persistence option is not working, (did you try installing to sdx1 not just sdx?), the following is another method of getting persistence:


Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start Startup Disk Creator.
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by zer010 on 2011-01-30
Thank you for your time and response, CS. I'm not sure if persistence is or isn't the problem I'm having.  After doing the basic update/upgrade, the flash drive wasn't bootable.   I think I'm just going to go ahead and perform a straight install to the flash drive as if it was a HDD. As I won't be using it that often, the rewrite cycles of /tmp shouldn't be too bad.   I should then be able to partition it it the usual : /, /home, swap  format that I'm accustomed to.  If anyone has any reason why this would be a bad idea, let me know.

---

### Post by [Snc] on 2011-01-30
> **zer010 said:**
> Thank you for your time and response, CS. I'm not sure if persistence is or isn't the problem I'm having.  After doing the basic update/upgrade, the flash drive wasn't bootable.   I think I'm just going to go ahead and perform a straight install to the flash drive as if it was a HDD. As I won't be using it that often, the rewrite cycles of /tmp shouldn't be too bad.   I should then be able to partition it it the usual : /, /home, swap  format that I'm accustomed to.  If anyone has any reason why this would be a bad idea, let me know.

Well, to my knowledge, it is wise, to disconnect all the hard drives, if you do that, to make your boot sector 100% secure

more info here: 
[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)

---

### Post by C.S.Cameron on 2011-01-30
> **zer010 said:**
> Thank you for your time and response, CS. I'm not sure if persistence is or isn't the problem I'm having.  After doing the basic update/upgrade, the flash drive wasn't bootable.   I think I'm just going to go ahead and perform a straight install to the flash drive as if it was a HDD. As I won't be using it that often, the rewrite cycles of /tmp shouldn't be too bad.   I should then be able to partition it it the usual : /, /home, swap  format that I'm accustomed to.  If anyone has any reason why this would be a bad idea, let me know.

It is not a good idea to update, upgrade a Live USB. The casper-rw file will quickly fill and you won't be able to boot.
Also the kernel is part of a squashfile and can't be upgraded.

Following is a step by step for a full install of 10.10. The FAT32 partition is so you can still use the flash drive for data on a Windows machine.

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

### Post by zer010 on 2011-01-31
CS, it looks pretty good until I start looking at the system requirements.  Even in Ubuntu's documentation, the recommended drive space is 5GB.  Since I'm using a 4GB flash drive, perhaps I should go with a smaller distro.  My first choices are Xubuntu or Lubuntu because I'd like to stick with the Ubuntu/Debian base. I guess I could go with a minimal install and build up from there.

---

### Post by C.S.Cameron on 2011-01-31
I have the previous method working on a 4GB flash drive but the following is probably a little more reasonable.
I haven't tried Lubuntu yet but have only heard good things, I think I will try it right now.

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
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = ~4 GB, Beginning, Ext4, and Mount point = "/" then OK.
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

### Post by zer010 on 2011-02-03
I think I'm gonna call this thread solved and post a new thread to discuss further progress and issues.....

---

### Post by Garthhh on 2011-02-03
I ran mint9 [ubuntu 10.04] installed on a 8g flash drive for about a month on a notebook with a bad hdd
I just did the install straight to the flash, as if it were any other hdd & let the install use the entire thing
I was using 6g for just programs & downloads, all my data music, pics... being stored on a 250g ntfs formatted exhdd [backup]
the set up worked reasonably well 
Firefox was noticeably slow
chrome worked well

I also played around with puppy linux, which also worked fine & had a footprint of 2g

once I figured to have downloads go on the exhdd, no issues with space

using a usb is great way to do an extended test drive, better than a live cd
it allows you to play around with all your favorite apps

---

