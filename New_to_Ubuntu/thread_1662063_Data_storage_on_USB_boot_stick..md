---
title: "Data storage on USB boot stick."
date: 2011-01-07
forum: New to Ubuntu
---

### Post by Jeffreytooker on 2011-01-07
Hello:

I am a n00bie.  I have run Puppy Linux a little.  I have downloaded Ubuntu 10.04 to a USB stick and am running it on my Emachines/Win7 computer from USB.  Not installed to HDD.  System runs well.  There are a few small problems to work out but not many.  So far 10.04 has let me avoid command line, of which I have a minimal understanding.

First problem is data storage on the boot USB stick.  I tried partitioning a USB stick with Gparted Then making a boot stick from that.  No joy.  The program that makes the boot stick from the DVD wants to erase the disk (USB stick, including partitions) to make a boot stick.  The storage option on the boot disk (stick) program only goes to 4G.  I would like to run a 16G stick.  This leaves a lot of un used memory on the stick.  I would like to store My Documents and stuff from the Win7 on the boot stick.  How does one do it?  I have run searches but find no specific answer.

Thank you.

Jeffrey Tooker

---

### Post by C.S.Cameron on 2011-01-07
Welcome to the forums.

You can increase the amount of persistence by using casper-rw and home-rw partitions.
Windows only sees the first partition on a flash drive and a disk image install must be on the first partition.
You can put stuff from Windows on this partition with out messing up the Ubuntu install.
When booted from the USB you need to go to File System/cdrom to find the stuff. It will be locked, so use Alt F2 then gksu nautilus to access it.

To add persistent partitions to a Startup Disk Creator install:


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

If you prefer to make an UNetbootin install persistent let me know.

---

### Post by Jeffreytooker on 2011-01-07
C.S. Cameron:

I made the three required partitions.  I un plugged the USB and re inserted it.  The three partitions appeared on the desk top.  An individual paine also appeared for each partition. I chose "discard on shutdown" on SU disk creator and chose make startup disk. Immediate error "installation failed" "failed to install boot loader".  First partition on left of bar in gparted has no data in it.  The other two do.  Proper nomenclature appears for all three partitions in the list below the bar.

Jeffrey Tooker
?????

> **C.S.Cameron said:**
> Welcome to the forums.

You can increase the amount of persistence by using casper-rw and home-rw partitions.
Windows only sees the first partition on a flash drive and a disk image install must be on the first partition.
You can put stuff from Windows on this partition with out messing up the Ubuntu install.
When booted from the USB you need to go to File System/cdrom to find the stuff. It will be locked, so use Alt F2 then gksu nautilus to access it.

To add persistent partitions to a Startup Disk Creator install:


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

If you prefer to make an UNetbootin install persistent let me know.

---

### Post by C.S.Cameron on 2011-01-07
In Startup Disk Creator, does CD-Drive/Image show /dev/sr0 and Disk to use show sdb1?

---

### Post by Jeffreytooker on 2011-01-07
CD-drive image /dev/sr0.  Disk to use /dev/sdh1.

Jeffrey

> **C.S.Cameron said:**
> In Startup Disk Creator, does CD-Drive/Image show /dev/sr0 and Disk to use show sdb1?

---

### Post by C.S.Cameron on 2011-01-08
Does it help making the partitions: 
1) FAT32     - 6GB
2) casper-rw - 4GB
3) home-rw   - 6GB

---

### Post by Jeffreytooker on 2011-01-08
Tried suggested partitions.  Same result.  Thank you for all of your help.  I will just use two sticks.  One for Ubuntu 10.04 (8G) and the other (16G) for data storage.  The 16G can hold all of my docs and pictures from my Win7 system.  So if I ever had to use another computer I would have all of my data.  I am learning a lot about Ubuntu.

Jeffrey

> **C.S.Cameron said:**
> Does it help making the partitions: 
1) FAT32     - 6GB
2) casper-rw - 4GB
3) home-rw   - 6GB

---

### Post by oldfred on 2011-01-08
With either 8GB or 16GB you can do a full install. It will be a little slower than a hard disk install as both USB and writes to flash are a little slower. You also have to be careful to install grub2 to the MBR of the flash drive. Now with Maverick you have to use manual install to even get the choice of where to install. C.S.Cameron usually suggests to disconnect hard drive, so grub cannot install itself to the internal drive which it usually does if you do not specify.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
Also has instructions from C.S.Cameron for 10.10 (he may want to add more info, I am not trying to steal his thunder:))
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)

---

### Post by C.S.Cameron on 2011-01-08
As OldFred suggests a full install should do as you want.
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
Make "New partition size..." about 8GB.
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

### Post by Jeffreytooker on 2011-01-08
Gentlemen:

Thank you both for all of the information.  At present I do not want to do a full install.  I a previous encounter with Ubuntu (about 2 years ago), I did a full install and had some bad experiences with it.  For now I prefer to run from USB.  I will keep the full install instructions in mind if I decide to go that way.

Jeffrey

---

### Post by C.S.Cameron on 2011-01-08
Sorry, the instructions above are for Full install to USB stick, not internal HDD.

---

### Post by Jeffreytooker on 2011-01-08
I guess I am just uninformed.  How does full install to USB stick vary from the USB stick I made with Startup Disk Creator in Ubuntu 10.04?  I see that it has an adjustable partition.  are there any other benefits?

Jeffrey

---

### Post by C.S.Cameron on 2011-01-09
An install to USB stick made with Startup Disk Creator, Universal and UNetbootin is a disk image or Live install, just like running the Live CD from USB stick, filesystem of the O/S is FAT32.
You can not update or upgrade the install or modify the kernel. You also can not install proprietary drivers. You can use the drive to install Ubuntu to a computer.

The Full install described above is just like an install to internal hard drive. The Fat32, (or if preferred, NTFS), partition at the beginning will allow it to be used for copying stuff from a Windows machine.
The O/S filesystem is ext3 or 4. 
You cannot use the flashdrive to install Ubuntu to a computer.

Initial disk image install is about 700MB without persistence, initial full install is about 2.3GB.

See also [http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by Jeffreytooker on 2011-01-09
The information above is enlightening and encouraging.  I have only two questions.  Can a "full install" USB be operated on the computers of others, and can the "full install" USB be upgraded from 10.04 to 10.10 without loosing data stored on USB?

Jeffrey

---

### Post by C.S.Cameron on 2011-01-09
Sure, you can move a Full install flash drive from one computer to another as long as you don't install proprietary drivers not common to all machines.
You can use Update Manager to upgrade from 10.04 to 10.10 just like an internal install.

---

### Post by Jeffreytooker on 2011-01-09
Starting USB full install per your directions.  Wish me luck.

Thank you.

Jeffrey

---

### Post by C.S.Cameron on 2011-01-09
Good Luck

---

### Post by Jeffreytooker on 2011-01-09
Full install went very well.  DVD did not auto boot.  Booted from boot list.  All updates loaded.  Made the five partitions.  I am able to find all files and disks to save to except, the 8G FAT on the full install boot disk. I have located the boot disk as /dev/sdh.  However when I look in /dev sdh is not there.  How does one do a "save as" to sdh1?  Everything else working well, so far.

Jeffrey

---

### Post by C.S.Cameron on 2011-01-09
The FAT32 partition should show up on as an icon on the desktop or look in Places/Computer.

Edit:
Have a look at the drive using gparted to find the FAT32 partition's mount point.

---

### Post by Jeffreytooker on 2011-01-09
I found the FAT 32 partition on the USB "full install" USB disk.  It is listed as windows.  All well for now. I will create [solved] post.

Thank you.

Jeffrey


> **C.S.Cameron said:**
> The FAT32 partition should show up on as an icon on the desktop or look in Places/Computer.

Edit:
Have a look at the drive using gparted to find the FAT32 partition's mount point.

---

