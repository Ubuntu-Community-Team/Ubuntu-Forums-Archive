---
title: "Live USB"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Messyhair42 on 2010-10-22
I'm wanting to use my Maverick USB stick as both a portable OS and use its /home folder as flash memory. if i open it from my desktop i get a bunch of folders that are related to using it as an install disk and none of the normal filesystem folders, and if i boot to it i don't have permissions to access the files on my desktop HD. Looking for solutions.

---

### Post by ArgusVision on 2010-10-22
Easiest thing that  worked for me, was take out the hard drive of your PC. (Towers are the easiest.) Run your live cd. Plug in the usb, and install normally to the usb just like you would a hard drive. As far as using the /home as a storage device, you might be better creating a FAT32 or NTFS partition so you can transfer files to other OS'es. (I know it may seem unimaginable, but it happens.) 
 A couple of things I experienced...
 - Data transfer rates are slower. It's not to bad on most things but disk intensive apps will slow down significantly and/or freeze from time to time.
- You're going to want a large flash drive. At least 8 GB, I'd recommend 16 GB or larger depending on what you're trying to do. Mobile office with a few docs, no big deal. Mobile personal computing, don't skimp.
- Not all drivers work on all hardware. (Big surprise right?) For exaple if you install it while on a PC that has an nVidia card, just stick with the generic drivers. If you install the nVidia specific drivers, it will basicly expect all hardware from then on to use those and will balk everytime you use something that doesn't. So just use the generic video.It may put a damper on Compiz/3D effects but you'll be able to operate. Proprietary wireless drivers are more problematic. Many wireless cards simply don't have a generic counterpart, and won't work without the specific driver.

Please don't think of me as a pessimist. I think it's a great idea, and I keep two different distros on usb in my back pack, but I just want you to be aware of what I've run into.

---

### Post by beew on 2010-10-22
> Data transfer rates are slower. It's not to bad on most things but disk intensive apps will slow down significantly and/or freeze from time to time.True. That's why I prefer to do full install on an external hdd than a usb flash drive. I have an installation in a 8G flash drive and one in a 4G hdd (from a dead laptop), the 4G one is a lot faster and in fact you won't even notice it is running externally whereas the 8G flash freezes often.


> Not all drivers work on all hardware. (Big surprise right?) For exaple if you install it while on a PC that has an nVidia card, just stick with the generic drivers. If you install the nVidia specific drivers, it will basicly expect all hardware from then on to use those and will balk everytime you use something that doesn't. So just use the generic video.It may put a damper on Compiz/3D effects but you'll be able to operate. Proprietary wireless drivers are more problematic. Many wireless cards simply don't have a generic counterpart, and won't work without the specific driver.

Or you can uninstall the nvidia driver when you remove the external drive. I have one machine that uses a nvidia card and I install the driver when I plug the 4 G external in it, and before I unplug I always remove the nvidia driver so I can use compiz in other machines as well.It would be painful if you use a flash drive because it could take a long time and your system may even freeze. But with an external hdd it is not so bad even though it is a hassel.

I can be wrong, but I think this issue only exists for graphic cards. For other drivers, like wireless, Ubuntu would use the correct drivers when you plug the installation into a computer even if you have proprietary drivers installed when using other machines . I have some broadcom driver package installed in  a live usb flash drive with persistence so I can use it in a machine with a broadcom wirless card. When I put it into a different PC that doesn't use broadcom for wireless it still works, Ubuntu automatically picks the correct wireless driver. A live usb flash drive with persistence is a lot faster than full install in  the same usb flash drive(At least for Ubuntu, that is, my Fedora live usb is very sluggish) even though there are things you can't do like upgrading kernel , also you cannot have more than 4 g of persistence.

---

### Post by C.S.Cameron on 2010-10-22
> **Messyhair42 said:**
> I'm wanting to use my Maverick USB stick as both a portable OS and use its /home folder as flash memory. if i open it from my desktop i get a bunch of folders that are related to using it as an install disk and none of the normal filesystem folders, and if i boot to it i don't have permissions to access the files on my desktop HD. Looking for solutions.

You should be able to access your desktop HDD from the flashdrive as root, gksu nautilus.

If you are using a persistent, (disk image), flash drive all persistent files are stored in a file named casper-rw.
This file is in the root of the flash drive.

Using a Linux machine you can mount this file as shown here:
[http://ubuntuforums.org/showthread.php?t=1028564](http://ubuntuforums.org/showthread.php?t=1028564)

It may be easiest to just make a folder in the root of the device for transferring files. This will be FAT32.

When booting from the device this folder can be found in filesystem/cdrom.

Following is a step by step for doing a Full install to USB and leaving a FAT32 partition so Windows can access the drive:

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

