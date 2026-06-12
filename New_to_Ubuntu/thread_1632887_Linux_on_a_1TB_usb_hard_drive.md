---
title: "Linux on a 1TB usb hard drive"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by joshthechamp14 on 2010-11-28
Hey
I was just wondering if I could _**install**_ Mythbuntu on my 1TB USB Hard Drive???
Is this possible??

---

### Post by akand074 on 2010-11-28
Yes it is possible. The hard drive's max read/write speed will be lower than an internal or eSata hard drive though. I have a friend that carries Ubuntu around with him in an 8GB USB drive for when it can come in handy.

---

### Post by C.S.Cameron on 2010-11-28
Following step by step is for installing 10.10 on a 16GB USB drive, you can adjust partition size to suit or use gparted to adjust at a later date. You might also prefer making the first partition NTFS rather than FAT32:

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
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
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

### Post by thatguruguy on 2010-11-28
I always put the alpha versions of ubuntu on external hard-drives for testing rather than my main hard-drive, so I don't mess up my system.  It's as simple as telling the installer to use the external drive rather than your system's internal hard-drive.

---

### Post by beew on 2010-11-28
@C.S.Cameron

I have a question. I have a few installations on external drives and flash drives. But I didn't remove the hard drive from the computers on which these are created, just too much trouble.  The problem is that the OSes of the host computers show up in the boot screen whenever I use one of these. It is not a problem if I just have one Linux installed in an external drive but now I am thinking of multiboot, It would be confusing if there are OS entries on the boot screen that don't really point to anything in the drive. Is there a way to get rid of that?

Thanks.

---

### Post by beew on 2010-11-28
> **akand074 said:**
> Yes it is possible. The hard drive's max read/write speed will be lower than an internal or eSata hard drive though. I have a friend that carries Ubuntu around with him in an 8GB USB drive for when it can come in handy.


Yes, an installation on a 8G usb can be slow, but you can make it faster and more reponsive by lowering the value of vm.swappiness to force it to use ram.

---

### Post by joshthechamp14 on 2010-11-29
> **C.S.Cameron said:**
> Following step by step is for installing 10.10 on a 16GB USB drive, you can adjust partition size to suit or use gparted to adjust at a later date. You might also prefer making the first partition NTFS rather than FAT32:

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
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
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



Thanks so much...u rock

---

### Post by C.S.Cameron on 2010-11-29
> **beew said:**
> @C.S.Cameron

I have a question. I have a few installations on external drives and flash drives. But I didn't remove the hard drive from the computers on which these are created, just too much trouble.  The problem is that the OSes of the host computers show up in the boot screen whenever I use one of these. It is not a problem if I just have one Linux installed in an external drive but now I am thinking of multiboot, It would be confusing if there are OS entries on the boot screen that don't really point to anything in the drive. Is there a way to get rid of that?

Thanks.

You can manually edit your grub.cfg file, remove or ### the menuentry for that drive.
It will reappear after updates on that computer though. grub will show whatever drives with o/s are installed on the computer.

---

### Post by wilee-nilee on 2010-11-29
> **beew said:**
> @C.S.Cameron

I have a question. I have a few installations on external drives and flash drives. But I didn't remove the hard drive from the computers on which these are created, just too much trouble.  The problem is that the OSes of the host computers show up in the boot screen whenever I use one of these. It is not a problem if I just have one Linux installed in an external drive but now I am thinking of multiboot, It would be confusing if there are OS entries on the boot screen that don't really point to anything in the drive. Is there a way to get rid of that?

Thanks.

os prober in grub2 is the distro finder you can remove it with synaptic if you want just one OS to show. The one installed on that HD.

---

