---
title: "Ubuntu settings for USB stick?"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by Georg99 on 2010-09-17
Hi to everyone,
I am a newbie in Linux and very impressed from Ubuntu.
I installed Ubuntu 10.04 LTS to an USB stick and after that to an external USB harddrive. Both are running fine.
I made some software updates and some changes to the desktop settings on the USB harddrive.
How can I save changes and settings when I boot Ubuntu from my USB stick? First of all, the screen resolution when Ubuntu starts?


Regards
George

---

### Post by garvinrick4 on 2010-09-17
> **Georg99 said:**
> Hi to everyone,
I am a newbie in Linux and very impressed from Ubuntu.
I installed Ubuntu 10.04 LTS to an USB stick and after that to an external USB harddrive. Both are running fine.
I made some software updates and some changes to the desktop settings on the USB harddrive.
How can I save changes and settings when I boot Ubuntu from my USB stick? First of all, the screen resolution when Ubuntu starts?


Regards
George
If you made it from unetbootin or something of that nature and did not have the selection to have persistence which is ability to save changes then you cannot.
Startup disk creater in Ubuntu will give you the choice of saving up to 4 gig of changes. That is the largest you can get because it uses Fat as format and it is only allowed 4 gig of persistence. Just make sure you pick correct drive when making, I am sure you know that but had to mention.

---

### Post by Georg99 on 2010-09-17
I installed from WinXP "Ubuntu-10.04.1-desktop-i386.iso" with "Universal-USB-Installer-1.7.9.7.exe" to the stick.

Sorry, but I didn't understand what to do with Disk Creator? I want to start Ubuntu from the USB stick.

---

### Post by C.S.Cameron on 2010-09-17
Following is procedure for full install to 8GB flash drive,
Adjust partition sizes as you wish.

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

### Post by cj.surrusco on 2010-09-17
+1 for full install. It will be faster and easier than setting up persistence.

---

### Post by C.S.Cameron on 2010-09-17
If you wish a persistent disk image pendrive with more than 4GB save space:

This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

### Post by Georg99 on 2010-09-18
Thanks for all the help. 
I will try your suggestions asap and will come back again.



Regards
George

---

### Post by ujjainnaga on 2010-09-18
after installing E1550 huwei 3g modem the problem started.
i cant delete or modify the content of any pen drive.
pls help me out.
these are the steps i have followed:

gksu gedit /etc/udev/rules.d/15-huawei-e1550.rules

SUBSYSTEM=="usb",SYSFS{idProduct}=="1446",SYSFS{id   Vendor}=="12d1",RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1  --product 0x1446 --type option-zerocd


pls help me out!!!!!!!!!!!!!!:p

---

### Post by garvinrick4 on 2010-09-18
There are some different ways of doing this install on pendrive with casper but for a absolute new comer why not just let him put in Ubuntu cd and boot off of it and use
Sytem to Admin to Startup Disk Creator and just use the slider it give him his four gigs
of persistence. Click install and be done with it for now until he gets more comfortable with
Linux. At least he can make a Operating System and have a live CD at same time for future use. Even has spot to reformat drive since he is having that trouble also. I think sometimes we are all guilty of giving instructions to new comers that they have no idea what is going on  and we take for granted these commands. Just a personal opinion not trying to start an argument in this thread.
 New comers make sure you choose the right drive and it is NOT THE SDA that is your enternal HDD know matter what way you make this Thumb drive install. It will be sdb or sdc according to how many USB drives you have plugged in. Check by booting into Ubuntu disk and choose Try UBuntu that is the Live cd. Run this code below in a terminal and it will tell your drive #"s
remember Windows uses letters C, D, E and so forth and Ubuntu uses sda, sdb, sdc and so forth. First partion would be sda1, second partition sda2, third sda3 and so on. When asks where you want boot it is sda not sda1 or sda2 always sda. If using sdb to load Ubuntu it would be sdb for grub (boot) and never sdb1 or sdb2. Get it. If you put it in sda of drive it will find the mbr(google that for info) that is where boot needs to be.
 In most pen drive unetbooten and Start up disk creator in Ubuntu it does it for you so you do not have to make a mistake. Install is in first partition which would be sdb1. Get it, first USB drive (sdb) and first partition on sdb (sdb1) Here is code in Live CD to see what your USB drive is. Open a terminal Applications to Accessories to Terminal. Copy and paste code always easiest.
```
sudo fdisk -l
```  (lower case L)
Have fun with Ubuntu. Do what you are comfortable with.

---

### Post by Georg99 on 2010-09-24
Hi,

thanks a lot for your help, especially to C.S.Cameron.
I partitioned the USB stick as you wrote and installed Ubuntu. Everything works fine.
Thanks again.

:smile:

George

---

### Post by beew on 2010-09-24
> **cj.surrusco said:**
> +1 for full install. It will be faster and easier than setting up persistence.

No, it won't be faster if you do a full install in a 8 G flash drive. The advantage of full install over a live usb with persistence is that you can do system updates (say you want to install graphic drivers) and you have more than 4 G to play with, but it will be a lot slower because the live usb runs in ram but not the full install.

---

