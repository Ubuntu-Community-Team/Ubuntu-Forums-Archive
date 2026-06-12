---
title: "Bootable install on external drive?"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by mjtaryan on 2011-07-10
My Windws system allows for a manual boot from a drive other than the main (boot) drive (i.e. CD, SD card, usb, etc.). I'm wondering if I can install a bootable version of ubuntu on an external USB hard disk and, if so, where do I find instructions for doing so? NOTE: I created and booted from a DVD and have decided I want to have ubuntu available, but don't want to take up room on my primary drive.)

---

### Post by Palanthas on 2011-07-10
Howdy mjtaryan! First off, Welcome to Ubuntu!

For a quick answer, yes you can install Ubuntu on an external media. I boot off a USB stick from time to time on my Dell Inspiron 1545 and it works wonderfully, albeit a little slower then when I boot off the internal hard drive.


If I remember right (and sadly I am at the coffee shop at the moment so I can't test this) you should be able to start the computer with the external hard driver plugged in and the CD/DVD also in its drive. (you may need to set BIOS to boot the CD first before USB) The external hard drive should be one of your options to install Ubuntu onto. Just to be on the safe side though, you may want to pull your internal hard drive out just to keep from accidentally installing over your windows installation!

After the installation is finished you should now be able to start the computer with the external hard drive plugged in and Ubuntu will start automatically, assuming the BIOS is set to boot to USB before the internal hard drive. Then shut down the computer, unplug the external hard drive and restart the computer, you'll be back into windows.

Hope this helps! I will try to check to make sure this actually works when I get home unless you beat me to it. ;)

---

### Post by jtarin on 2011-07-10
> **mjtaryan said:**
> My Windws system allows for a manual boot from a drive other than the main (boot) drive (i.e. CD, SD card, usb, etc.). I'm wondering if I can install a bootable version of ubuntu on an external USB hard disk and, if so, where do I find instructions for doing so? NOTE: I created and booted from a DVD and have decided I want to have ubuntu available, but don't want to take up room on my primary drive.)This is usually not a problem if the drive is detected by the bios and Grub is installed to the / of the drive in question and if you only have Linux on it and you use a third-party bootmanager editor such as EasyBCD installed in Windows so the Windows bootmanager will chainload Grub. The problem arises when the drive is unplugged and then plugged back in it can re-identify it self differently. That is why I have set out the scenario as such, when it comes to placement of bootmanagers.There may be other takes on this.This has worked for me...and still does.

---

### Post by ajgreeny on 2011-07-10
Just make sure you choose to install the bootloader files, grub2, to the external drive, or you will be in trouble if you try to boot with the external drive not attached.  You will need to click on the **Device for bootloader installation** button which appears after you choose the manual partitioning during the "Something else" option that you will see at the "Preparing disks" or partitioning stage.  There you should choose /dev/sdx where the sdx is your external drive.  Do not put grub on to a partition,eg /dev/sdx1, put it on the root of the drive, /dev/sdx.
See screenshot for details of this.

---

### Post by C.S.Cameron on 2011-07-10
Following step by step for Full install of 11.04 to USB device, partition sizes given are for 8GB drive, adjust size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
Insert the Live CD or Live USB.
Start the computer, the CD / flash drive should boot, (you need to adjust BIOS to boot USB).
Select language
Select "Forward".
Select Download updates while installing and Select Install this third-party software.
(Notice that at least 4.4 GB drive space is required, 4GB bootable flash drive users must choose another distro for a full install).
Forward
If prompted unmount partitions.
Select "Something else"
Forward
Confirm "Device for boot loader installation:"is correct, (If you left your internal HDD plugged in make sure the USB drive root is selected - sdb not sdb1).
(Optional Windows data partition)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000
"Location = Beginning".
"Use as: = FAT32 file system"
And "Mount point = windows".
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap partition)
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
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and enable the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.

---

