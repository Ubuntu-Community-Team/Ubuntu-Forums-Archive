---
title: "Ubuntu on Flash no HD"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by PaulXUb on 2010-11-17
Hi,

I'm a new user to Ubuntu.  After a few hours of reading I was able to install Ubuntu on a flash drive and run it on a computer without a hard drive.  It is able to go online and use chat etc, however when I tried to save a small picture it somehow wouldn't save.  There is plenty of memory on the flash to store the picture.

Basically every time I restart the computer it resets.  Nothing I keep in the folders remain.  Is there any way I can fix it?

Thanks

---

### Post by Hippytaff on 2010-11-17
Hi and welcome

You usb install needs to be set up as a persitant usb
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

:-)

---

### Post by Rex Bouwense on 2010-11-17
Try:  [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
Beaten to the draw by Hippytaft.  Enjoy.

---

### Post by Hippytaff on 2010-11-17
> **Rex Bouwense said:**
> Try:  [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
Beaten to the draw by Hippytaft.  Enjoy.
 
same diagnosis....Different link - jobs a good one :-)

Edit -> same link :-s I need glasses

---

### Post by Rex Bouwense on 2010-11-17
I'm wearing my glasses and spelled your handle wrong.:)

---

### Post by Hippytaff on 2010-11-17
> **Rex Bouwense said:**
> I'm wearing my glasses and spelled your handle wrong.:)

I didn't notice - I definitely need glasses :-)

---

### Post by C.S.Cameron on 2010-11-17
Both usb-creator, (from the Live CD), and Universal from pendrivelinux.com have persistence options.
If you want more than 4GB of persistence space you can try this with a usb-creator or universal install:


Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

Following is what I did with an UNetbootin install:

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

### Post by PaulXUb on 2010-11-19
Thanks everyone.  It's working now.  However, is there any way to increase the storage to more than 4GB if I get a larger flash drive?

---

### Post by mastablasta on 2010-11-19
it's wouldn't recomend to run your system liek that on use as you will ruin USB preety fast as the have limited cycles of writing down things.
 
you could do a propper install on USB if that's what you were thinking. hwoever the problem of ruining USB quite fast (and any data on it) still remains.

---

### Post by C.S.Cameron on 2010-11-19
> **PaulXUb said:**
> Thanks everyone.  It's working now.  However, is there any way to increase the storage to more than 4GB if I get a larger flash drive?

See the post above yours.

---

### Post by C.S.Cameron on 2010-11-20
> **mastablasta said:**
> it's wouldn't recomend to run your system liek that on use as you will ruin USB preety fast as the have limited cycles of writing down things.
 
you could do a propper install on USB if that's what you were thinking. hwoever the problem of ruining USB quite fast (and any data on it) still remains.

Bull poop!

If you do the math you will see that at 10000 write minimum lifetime a flash drive will last years at 8 hour per day use.

I have only heard of one person supposedly bricking a flash drive running Ubuntu from it, except for a guy that intentionally wrote to a single cell continuously to try to brick one. 
If you have actually heard of someone bricking one, please post the source.

---

### Post by PaulXUb on 2010-11-20
> **C.S.Cameron said:**
> Bull poop!

If you do the math you will see that at 10000 write minimum lifetime a flash drive will last years at 8 hour per day use.

I have only heard of one person supposedly bricking a flash drive running Ubuntu from it, except for a guy that intentionally wrote to a single cell continuously to try to brick one. 
If you have actually heard of someone bricking one, please post the source.

Thanks for your replies.
The current flash drive I have sticks out pretty far and I'm afraid of damaging it when I move it around.  I was thinking about getting the La Cie Moskeyto. Do you know if it'll be capable to handling the task of running Ubuntu?

---

### Post by voteforpedro36 on 2010-11-20
There's no good reason it shouldn't, as long as it works as a USB drive.

---

### Post by PaulXUb on 2011-01-04
Ok, I've been running Ubuntu from this USB for a while now, and it works great.  However, every time I start the computer it give me the screen to "Try Ubuntu" or "Install Ubuntu."  

Is it possible to get rid of that screen? or
Is it possible for me to install Ubuntu into another USB drive so it's not in the USB mode, but in the installed mode?

---

### Post by C.S.Cameron on 2011-01-04
Following step by step for Full install of Ubuntu 10.10 to USB,
Adjust partition size to suit:

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

