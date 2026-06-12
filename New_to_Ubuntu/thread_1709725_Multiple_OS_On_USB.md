---
title: "Multiple OS On USB"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by Hyrda on 2011-03-18
I will admit this is my first time doing anything related to Linux, so  you may need to excuse the fact that I know absolutely nothing.

I  have been looking to place multiple Linux distributions on my USB. The  USB itself is a SanDisk Cruzer Blade 16 GB, so I am not sure as to  whether it is even possible with this or not.

After reading  around, some have said about partitioning my USB. My real issue is that,  I do not know which software or method I should use to do that for  Windows Vista (Yes, I know, it is a terrible OS). 

I have also seen  various pieces of software I could use to place the Linux distributions  on my USB, like UNetbooting or Universal USB Installer from  pendrivelinux.com, although, out of these software I do not know if any  of them can work for Ubuntu, Fedora and Debian.

I guess I am more or less asking for a step by step guide to this, if it is not too much trouble.

---

### Post by Pougnet on 2011-03-18
Try following this guide here [http://www.linuxquestions.org/questions/linux-software-2/boot-live-cd-or-dvd-with-grub-309670/](http://www.linuxquestions.org/questions/linux-software-2/boot-live-cd-or-dvd-with-grub-309670/)

---

### Post by jmszr on 2011-03-18
Hydra,

This might be what you're looking for: [http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Hope that helps.

Edit: You might want to check this out (it's for Windows): [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by I2k4 on 2011-03-18
These are Ubuntus's own very good instructions for using the PenDrive - the one extra thing needed to retain settings and preferences between boots is to set aside USB space for "Persistence" (you'll see the option on the dialog at "Show Me How" Step 2, item 8.)

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I suggest using at least 2GB for Ubuntu, whichever version, and 2GB for Persistence.  I also suggest shopping versions using this method until you find one you like and that runs well on your computer.  Since you haven't finalized your choice of Linux OS, you might want to simplify life and save some hours of aggro by getting one USB for each OS you want to run, then worry about consolidating your choices onto a single drive when you're further down the road.  A 4GB USB drive is $10, and it's only an hour's work to install and configure Ubuntu or Lubuntu or anything else when you want to try a different flavor.

When you want to boot from USB you set your computer's BIOS to boot priority for that drive.   I have no idea whether you can set up a further choice of different OS on the USB drive when your BIOS recognizes it.  Good luck.

---

### Post by oldfred on 2011-03-18
With 16GB you can do a full install of one system and still have lots of room for many ISOs to also boot.

Full install:
It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.


Then you can create a iso folder and install many ISO files and boot them like jmszr's link.

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

I did a full install to my 16GB flash with 8GB for the system and 8GB for a data partition. No swap & I do not plan on saving a lot of data in /home as it does not have room. Regular houseclean required if you use it a lot. I also have several ISO in my 4GB flash and use itfor all installs and have available several rescue ISO, gparted, and versions of Ubuntu. All booted with grub2 as above link.

---

### Post by beew on 2011-03-18
If you are in Ubuntu the easiest way to make a multiboot usb would be to use the utility multisystem
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)


@I2k4

I think OP wants to make a multiboot usb, not a live usb just for Ubuntu.

---

### Post by I2k4 on 2011-03-18
Beew:  Interesting link, but came up in French. I know what the user wants to do, but was suggesting that it might turn out to be more trouble than it's worth in time and effort.  It's a personal judgement call.

---

### Post by beew on 2011-03-18
> **I2k4 said:**
> Beew:  Interesting link, but came up in French. I know what the user wants to do, but was suggesting that it might turn out to be more trouble than it's worth in time and effort.  It's a personal judgement call.

The website is in French, but you can translate the page (I see a Google translation bar on top of the page or you can use a firefox addon like quick translate) The actual program I downloaded and installed has English interface (I think it may depend on where you are)

Multisystem has an easy to use GUI, no time and effort required beyond making a few clicks and waiting for it to do its thing. :)

---

