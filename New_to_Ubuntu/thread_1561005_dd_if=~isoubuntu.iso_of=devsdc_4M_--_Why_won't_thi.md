---
title: "dd if=~/iso/ubuntu.iso of=/dev/sdc 4M -- Why won't this boot?"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Isaacgallegos on 2010-08-25
dd if=~/iso/ubuntu-10.04.1-desktop-i386.iso of=/dev/sdc 4M

this works with opensuse and mandriva but ubuntu will not boot when cloned using dd. _Is there a special way I need to format my USB drive? _

Side note: I don't have a cd drive; my only computer is a netbook. I'm currently in a different linux distro which dosen't have any fancy automated usb makers, but dd should work.

---

### Post by dagdeniz on 2010-08-25
Not enough info in the help pages if dd is still supported. From [https://help.ubuntu.com/community/Installation/FromImgFiles:](https://help.ubuntu.com/community/Installation/FromImgFiles:) 

> Ubuntu is distributed over the Internet as two types of files: CD image files, called ISOs, and flash image files, called IMGs. [Warning: This applies just to Ubuntu 9.04. Ubuntu is NO LONGER distributed in IMG format, except for some machines [IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/sad.png[/IMG] ]. To install Ubuntu from flash media, you first need to write the downloaded IMG image to your flash device.  
and the method (after unmounting the drive): 
```
sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m
```
However, for the iso files, "dd" method is not mentioned at all: 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

The manual method described at the end of the page is not as easy as "dd if=xyz of=xyz"

Didn't the usb creator work for you?

---

### Post by jtarin on 2010-08-25
Using dd with the correct source & target (i.e. the path and filename of your LiveCD iso *and* the device name (only) of your USB stick) works with LiveCD. Just did it.

I have seen different USB sticks not work when trying to make bootable in the past (use a different stick & same process works fine) so don't rule out possible media problem.

---

### Post by Isaacgallegos on 2010-08-25
> **dagdeniz said:**
> Didn't the usb creator work for you?

I don't have ubuntu, yet. I have mandriva, but this is not a mandriva problem since it's specific to the Ubuntu iso. This method has worked with other distros and I'm sure I've done it with Ubuntu at least once. 


[QUOTE=jtarin] I have seen different USB sticks not work when trying to make bootable  in the past (use a different stick & same process works fine) so  don't rule out possible media problem.     [QUOTE]

I wonder if this has something to do with how a disk can be partitioned. I've recently been looking up "flagging" a partition as active, with little understanding of how to do it in the terminal.

---

### Post by oldfred on 2010-08-25
Windows needs an active (boot flag) partition. Some BIOS will not boot without a primary partition with the boot flag. grub/Ubuntu do not use the boot flag.

set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda

I formated USB to FAT32, installed grub2 to the USB, copied the ISO (standard copy) and then set a loopmount boot in grub.cfg to boot it. I have several ISO on one 4GB flash drive all booted from grub2.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

---

### Post by jtarin on 2010-08-25
Here's a [link]("http://www.pendrivelinux.com/usb-x-ubuntu-610/") for Linux and pendrives.....check the menu, not just the article that opens.

---

### Post by LiquidMeson on 2010-08-25
there's also unetbootin

---

### Post by Isaacgallegos on 2010-08-28
> **LiquidMeson said:**
> there's also unetbootin

fixed. thanks.

---

### Post by mikewhatever on 2010-08-28
There exists an unofficial .img image of 10.04 that should work when written with dd.
[http://kmandla.wordpress.com/2010/05/02/ubuntu-10-04-desktop-i386-bootable-usb-image/](http://kmandla.wordpress.com/2010/05/02/ubuntu-10-04-desktop-i386-bootable-usb-image/)
A word of caution - while I don't endorse using custom images, the author of this one is very clear about what's been done. He is also a mod here.

---

