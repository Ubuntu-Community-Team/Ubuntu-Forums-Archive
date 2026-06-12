---
title: "Limitation of size of USB-installation"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by yc2 on 2011-02-06
Hello,

I read that Live CD installed on USB flash drive has a limitation of size to 4 GB.

I assume this limitation (4 GB) regards the root file system with the system (packages installed, settings) including the data in the home partition etc?

I have two further questions related to this, please.

1. If I need more space, can I then just create another partition on the flash drive and store data there. (using e.g. GParted from Ubuntu or from its own CD)

2. Why is there a limitation to 4 GB? (Since I know that FAT32 files are limited to 4 GB size I assumed that the installation was stored in a FAT32-file on the stick but that is just a wild guess, better to ask. :) )

Thanks.

---

### Post by Lt. Surge on 2011-02-06
> **yc2 said:**
> Hello,

I read that Live CD installed on USB flash drive has a limitation of size to 4 GB.

I assume this limitation (4 GB) regards the root file system with the system (packages installed, settings) including the data in the home partition etc?

I have two further questions related to this, please.

1. If I need more space, can I then just create another partition on the flash drive and store data there. (using e.g. GParted from Ubuntu or from its own CD)

2. Why is there a limitation to 4 GB? (Since I know that FAT32 files are limited to 4 GB size I assumed that the installation was stored in a FAT32-file on the stick but that is just a wild guess, better to ask. :) )

Thanks.

I had heard of someone with 8GB being able to install Ubuntu on half of it and keeping files in another "partition", and of course the flash drive was formatted before this was attempted.

But yes, File Allocation Table files have a distinct limit of 4GB in size, this might indeed have something to do with it, if not being the actual reason.

If all else fails, perhaps invest in a DVD and install Ubuntu from THAT...

If I'm not mistaken there is not one distribution of Linux or any Operating System that constitutes more than 4GB of space to boot and install from, so no worries if that question might follow my answers...

---

### Post by fabricator4 on 2011-02-06
> **yc2 said:**
> Hello,

I read that Live CD installed on USB flash drive has a limitation of size to 4 GB.

I assume this limitation (4 GB) regards the root file system with the system (packages installed, settings) including the data in the home partition etc?

I think you must have misunderstood.  The limit is a minimum, not a maximum.  Because root install takes at least 2.5 - 3.0 GB then it's not possible to install the full Ubuntu on a USB drive smaller than 4Gb.

I'm currently, right now, working on a 10.10 4Gb USB Install.  2.5GB for the OS, and 0.5 GB swap file, about 1GB left for data.

I also have an 8 GB USB drive of 11.04 A1 that boots fine.  I used the 8 GB drive because I thought the Alpha 1 release might be a bit chunky and I honestly can't tell you how big it is right now.  I have a 1GB swap partition on it, the rest is all 11.04 boot drive.

Chris

---

### Post by Lt. Surge on 2011-02-06
> **fabricator4 said:**
> 

I'm currently, right now, working on a 10.10 4Gb USB Install.  2.5GB for the OS, and 0.5 GB swap file, about 1GB left for data.

Chris

Ah, how difficult is it to do that? Because the way I did, I just put it all on a 2GB. If I had a 4GB I would try, though.

---

### Post by fabricator4 on 2011-02-06
> **Lt. Surge said:**
> Ah, how difficult is it to do that? Because the way I did, I just put it all on a 2GB. If I had a 4GB I would try, though.

It's probably easier than trying to get it on a 2GB drive.  Is that a light version you're using?  

I use Gparted to prepare the ext2 and swap partitions, but just run the install normally after that.  When you get to the install select manual for the partitions and don't format them.  You have to make sure the ext2 partition is selected to mount as root ("/") and that grub is installed.

I followed some instructions to do this first time, (some guy here had a link to the instructions in his sig - can't remember his name) and it worked first time and every time for me.  10.04 and 10.10 on 4GB drives, and 11.04 alpha on an 8 GB.

Whereabouts are you? (rude question!)  Over on this side of the big pond the supermarkets are now selling 4GB USB sticks and SD cards for about $12.  Some of the stationery chain stores (office works) are selling branded 8GB memory sticks for under $20.

About six or seven years ago I bought my first 1 GB for my digital camera and payed $120 grey market.  That was cheap - the street price was about $200 at the time.  Times change.  :eek:

Chris

---

### Post by Lt. Surge on 2011-02-06
> **fabricator4 said:**
> It's probably easier than trying to get it on a 2GB drive.  Is that a light version you're using?  

I use Gparted to prepare the ext2 and swap partitions, but just run the install normally after that.  When you get to the install select manual for the partitions and don't format them.  You have to make sure the ext2 partition is selected to mount as root ("/") and that grub is installed.

I followed some instructions to do this first time, (some guy here had a link to the instructions in his sig - can't remember his name) and it worked first time and every time for me.  10.04 and 10.10 on 4GB drives, and 11.04 alpha on an 8 GB.

Whereabouts are you? (rude question!)  Over on this side of the big pond the supermarkets are now selling 4GB USB sticks and SD cards for about $12.  Some of the stationery chain stores (office works) are selling branded 8GB memory sticks for under $20.

About six or seven years ago I bought my first 1 GB for my digital camera and payed $120 grey market.  That was cheap - the street price was about $200 at the time.  Times change.  :eek:

Chris

Ah yes, I forgot to mention I installed Ubuntu 10.10 Netbook Remix using he 2GB :p

I live in Florida, you?

---

### Post by fabricator4 on 2011-02-06
> **Lt. Surge said:**
> Ah yes, I forgot to mention I installed Ubuntu 10.10 Netbook Remix using he 2GB :p

I live in Florida, you?

Oh, I tried Netbook 10.04 (or something) on my 900SD but I didn't have much luck with it.  I'm in (near) Brisbane, Australia.

C

---

### Post by C.S.Cameron on 2011-02-06
> **yc2 said:**
> Hello,

I read that Live CD installed on USB flash drive has a limitation of size to 4 GB.

I assume this limitation (4 GB) regards the root file system with the system (packages installed, settings) including the data in the home partition etc?

I have two further questions related to this, please.

1. If I need more space, can I then just create another partition on the flash drive and store data there. (using e.g. GParted from Ubuntu or from its own CD)

2. Why is there a limitation to 4 GB? (Since I know that FAT32 files are limited to 4 GB size I assumed that the installation was stored in a FAT32-file on the stick but that is just a wild guess, better to ask. :) )

Thanks.


4GB is the max size of the casper-rw file because it is FAT32.
You can use a separate ext2, 3 or 4 partition named casper-rw for persistence and there will be no limit except for the size of the drive.

1GB is the minimum drive size for a Live install, (no persistence), 2GB for a persistent install, 4GB is the minimum drive size of a Full install.

---

### Post by Lt. Surge on 2011-02-06
> **fabricator4 said:**
> Oh, I tried Netbook 10.04 (or something) on my 900SD but I didn't have much luck with it.  I'm in (near) Brisbane, Australia.

C

Wow how's the weather?

Perhaps the latest incarnation of NBR would work better?

---

### Post by Savio2010 on 2011-02-07
Hi,

Reading this thread much of my doubts of usb installation are clear, but would like to know some more things:

1. If I do a full install on a usb drive is it possible to perform all types of updates.
2. Can I install the new version ofUbuntu as by reading this link, this link states Ubuntu 7.04.
[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)

Thanks in advance for replying. :popcorn:

---

### Post by yc2 on 2011-02-07
Thanks guys, especially C.S.Cameron, I think I finally got it.

I can EXPAND the Casper file up to 4 GB. If I need more I can REPLACE it with a Casper PARTITION and have a system of (theoretically) ANY size.

Thanks.

---

### Post by Savio2010 on 2011-02-07
Hi everybody,

if Ubuntu full installation in done on a USB, can I use the same USB to boot on multiple computers.
In other words is ubuntu full installation portable.

Sorry for posting twice.

---

### Post by yc2 on 2011-02-07
> **Savio2010 said:**
> Hi everybody,

if Ubuntu full installation in done on a USB, can I use the same USB to boot on multiple computers.
In other words is ubuntu full installation portable.

Sorry for posting twice.
Yes, that is the idea.

---

### Post by beew on 2011-02-07
> **yc2 said:**
> Thanks guys, especially C.S.Cameron, I think I finally got it.

I can EXPAND the Casper file up to 4 GB. If I need more I can REPLACE it with a Casper PARTITION and have a system of (theoretically) ANY size.

Thanks.

I don't get it. If you are doing a full install in a usb why use Casper file? If I understand correctly it is used only for live usb. A live usb with persistence is not a full installation, it doesn't support system level update or installation of some propietary drivers. 

For a full installation  you should format your usb in ext3 or ext4 and then just install like you nornally would. You can also create a /home partition if your usb drive is big enough.  Just make sure that you install into the usb drive instead of your internal hard disk, or you would wipe out all your data (choose "manual install" or something like that and then make sure you choose the right drive, something like /dev/sdc , or you can remove your internal hard disk first)

The problem with installing into a usb flash drive, aside from the size limitation, is that it runs rather slow. To have a real functioning portable system maybe you should try install into an external hard drive instead.

---

### Post by yc2 on 2011-02-07
> **beew said:**
> I don't get it. If you are doing a full install in a usb why use Casper file? If I understand correctly it is used only for live usb. A live usb with persistence is not a full installation, it doesn't support system level update or installation of some propietary drivers. 

For a full installation  you should format your usb in ext3 or ext4 and then just install like you nornally would. You can also create a /home partition if your usb drive is big enough.  Just make sure that you install into the usb drive instead of your internal hard disk, or you would wipe out all your data (choose "manual install" or something like that and then make sure you choose the right drive, something like /dev/sdc , or you can remove your internal hard disk first)

The problem with installing into a usb flash drive, aside from the size limitation, is that it runs rather slow. To have a real functioning portable system maybe you should try install into an external hard drive instead.
OK, so I didn't get it then ;)

So there are two ways of doing it?
1. The Casper file or the Casper partition which will create a Live-CD on the USB-device but with persistence (if you choose this option).

2. The full installation onto a USB device. I had no knowledge about this option. I can just run the traditional installer (from the Live CD) but when I come to partitioning, I can choose "manual partitioning" (like I always do) and choose the USB-device partitions instead? Wow, that was new to me!

_Why do you have the pendrivelinux casper file/partition method at all then?_ Why don't you always use the full installation onto USB device? I can only see one reason: It is simpler for a new user just to press one button and get it onto the USB-stick?

Does it also have to do with indentification of hardware? In a full installation the type pf graphics card etc is already determined whereas a Live-CD will identify all hardware on each run ??

EDIT:
Please consider this additional question:
_If I use this full installation onto the USB-stick will this not write the GRUB2 into the MBR of the HDD of the host computer?_ (I do not want this, I want the host computer unaltered and an independently bootable (on different computers) USB-stick with persistence.)

Thanks for all input in this thread.

---

### Post by beew on 2011-02-07
> **yc2 said:**
> OK, so I didn't get it then ;)

Why do you have the pendrivelinux casper file/partition method at all then? Why don't you always use the full installation onto USB device? I can only see one reason: It is simpler for a new user just to press one button and get it onto the USB-stick?




As  far as I know there are two reasons why you would want a live usb instead of a full install in an usb flash drive.

1) A live usb is faster since it runs out of ram. A full installation in a usb flash drive is slow, that's why an external hard drive would be a  much better medium. 

If you have no intention  of doing system level update the live usb option is probably just as well (with C.S. Cameron's method you can have more than 4 G peresistence)

2) A full installation doesn't have an installer, so unlike a live usb with persistence you can't use it to install Ubuntu into another computer.

> Does it also have to do with indentification of hardware? In a full  installation the type pf graphics card etc is already determined whereas  a Live-CD will identify all hardware again?????Not really. The full installation  has the option  of installing propietary graphic drivers but you don't have to, whereas the live usb doesn't have the option. With a full install you can either choose not to install the propietary graphic driver so it would remain  portable except it may not work on the particular pc that requires the propietary graphic driver, or, you can install the graphic driver when plugged into the computer that uses that propietary graphic driver and uninstall it before you remove the drive so it would remain  portable (kind of a pain, but it works)

I have a full installation into an external drive and I haven't installed any propietary graphic driver so it works basically on  all computers with a intel graphic card. I installed the noveau driver experimental package (the drivers themselves already installed by default) so now it also works on  computers with  newer Nvidia cards with full compiz effect. Haven't tried the open source ati driver though. I have no access to computers with ati graphic cards at this point.

---

### Post by beew on 2011-02-07
> 
Please consider this additional question:
If I use this full installation onto the USB-stick will this not write the GRUB2 into the MBR of the HDD of the host computer?? (I do not want this, I want the host computer unaltered and an independently bootable (on different computers) USB-stick)


No, if you make sure it installs the boot loader in your external device. I don't remember which step is that (there is a difference between the 10.04 and 10.10 installer) But if you choose "advanced' at some point you would be able to specify where the bootloader is installed. I have not done that, but you can of course always remove your internal hard drive first if you are worry.

---

### Post by yc2 on 2011-02-07
Thanks beew, many things here I had no idea about.

I was recently abroad and needed backup for my laptop. I bought an Iomega external drive (320 GB). They have really developed. Super small, super quick, no external power needed. (I am sure WD and other brands are the same.) It really worked well with my old laptop.

4-5 yrs ago I had to buy all in all ten WD and Iomega. They worked fine but were much bigger and had external power.

So, an external HD is probably a very good option, thanks for advice.

---

### Post by C.S.Cameron on 2011-02-07
> **Savio2010 said:**
> Hi,

Reading this thread much of my doubts of usb installation are clear, but would like to know some more things:

1. If I do a full install on a usb drive is it possible to perform all types of updates.
2. Can I install the new version ofUbuntu as by reading this link, this link states Ubuntu 7.04.
[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)

Thanks in advance for replying. :popcorn:

Yes you can do full updates and upgrades, just like a real HDD.

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

### Post by C.S.Cameron on 2011-02-07
> **beew said:**
> 
1) A live usb is faster since it runs out of ram. A full installation in a usb flash drive is slow, that's why an external hard drive would be a  much better medium. 

Are you sure? I have tried benchmarking each type of flash drive install and not noticed a significant difference in boot speed or operating speed.

---

### Post by yc2 on 2011-02-07
Thanks for all good advice here. You have really looked into this matter. The only thing I have noticed was a big difference between USB-flash and USB-HDD for copying. What I counted in hours for the flash I counted in minutes for the HDD.

(When using a USB-installation I guess the _amount_ of RAM is significant? The more you can cache the quicker you can work.)

EDIT: I had better add it was mostly for copy/WRITE of large amounts of data.

---

### Post by fabricator4 on 2011-02-07
[QUOTE=yc2;10438117
(When using a USB-installation I guess the _amount_ of RAM is significant? The more you can cache the quicker you can work.)[/QUOTE]

Yes, to a point.  Nothing can help when moving very large amounts of data of course.  Typically for flash RAM, the write speeds are much slower than read speeds.  You can use Disk Utility to benchmark the read/write speeds to see exactly what's going on.  It's also interesting to see that some of the older USB sticks, and those using older technology are particularly slow at writes.  I got a branded 8MB SD card for my 900SD very cheap a few weeks ago and found the write speeds are pretty slow. 

Chris

---

