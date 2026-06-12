---
title: "Running from a pen drive"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by corncob on 2010-10-27
I met somebody who is running Ubuntu from a USB pen drive, selecting it from the device menu he gets by pressing F12, ESC or something when booting.  When I looked closer I saw that the file system is like the one on an installation CD rather than what you'd find on a regular Ubuntu HD installation.  It's as if he's running it from a live CD but he says he can save files.  I'm hoping to get some comments from you guys and gals.  He's one of my students in this Ubuntu class I'm teaching and I feel I should have something to say about it but I don't know quite what.

---

### Post by ArgusVision on 2010-10-27
It's a Live USB with persistance. There's a couple of tutorials around here somewhere... Search live usb + persistance

---

### Post by migs73 on 2010-10-27
It is called a persistent install. see here

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

:)

---

### Post by ArgusVision on 2010-10-27
Take a look here.

[http://ubuntuforums.org/showthread.php?t=1594216&highlight=live+usb+persistance](http://ubuntuforums.org/showthread.php?t=1594216&highlight=live+usb+persistance)

---

### Post by ArgusVision on 2010-10-27
Ok... Migs link looks better... :-k

---

### Post by C.S.Cameron on 2010-10-27
Besides for a persistent, (disk image), install to flash drive, you can also do a Full install, using the same method as installing to an internal drive.

---

### Post by ArgusVision on 2010-10-27
One caveat to the full install method. Be sure on the last step to choose the usb as the drive to install grub to, or, (something I've done as a precaution) remove the HDD so there's no chance of writing anything to it vs. the flash drive.

Had an "experience" back when I first started with Ubuntu (2007), where I installed to a usb drive and made the PC unbootable without the usb. It made for an accidental security token... :? ... :P
Since then, I just take out the HDD.

---

### Post by Geoff918 on 2010-10-27
Take a look at [http://www.pendrivelinux.com](http://www.pendrivelinux.com)

You can set-up a full install. One shortcoming is that updates are nearly impossible (unless you have an extremely large USB drive). The drive will quickly run out of space if updates are applied.

And you're correct, it's close to a LiveCD version but there is the ability to use persistence (the ability to save files and changes to the OS environment). I'm pretty sure you can do the same with a LiveCD as long as you have other media on which to store your changes.

---

### Post by corncob on 2010-10-27
> **Geoff918 said:**
> Take a look at [http://www.pendrivelinux.com](http://www.pendrivelinux.com)

You can set-up a full install. One shortcoming is that updates are nearly impossible (unless you have an extremely large USB drive). The drive will quickly run out of space if updates are applied.

And you're correct, it's close to a LiveCD version but there is the ability to use persistence (the ability to save files and changes to the OS environment). I'm pretty sure you can do the same with a LiveCD as long as you have other media on which to store your changes.

Can you do this with a rewritable CD?  Are CD-RWs still around?  With CD-Rs at 25¢ ea I just get those and throw them away.  How about rewritable DVDs?  I haven't been looking for those in recent years either.

Thanks for the links.

---

### Post by C.S.Cameron on 2010-10-27
A Live CD is much slower than a Live USB.
Updating and upgrading a Full install flash drive works just fine for anything 4GB and larger.

Following is step by step for installing 10.10 to flash drive or external USB HDD:

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

### Post by corncob on 2010-10-28
Thank you, C.S.  I printed out the instructions and will give it to the student next class.

---

### Post by Ichido on 2010-10-28
I have just 2 hours ago, used UNetbootin to install 10.04 on my 2GB USB drive and it works great!
Files created are saved to the USB Drive.
When I boot my Dell 1525, I press "F12" for my "boot options" because my BIOS is set to boot #1-HD, #2-CD and #3-USB Drive.
PS. Insert USB Drive Before you boot.

---

