---
title: "Installing Ubunto 8.10 on a 2nd hd"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by FireLizard on 2008-12-23
Hi,  

    I am new to all this and I want to ease into Linux.  I currently have an HP PC with Vista (ugg) on a SATA HD and an extra PATA HD with a corrupt version of Windows 2000, from my old computer.  I would like to wipe the Windows 2000 and install Ubuntu 8.10 on the second HD as a secondary OS so I can explore it while still using Windows.  However, most of what I'm finding online by way of directions is about partitioning one hd, not dual booting from two different hds.  Do I need to mess with the partitioning when I'm installing to a completely different HD? Should I just remove the Vista HD during the install? Also, what file system should I reformat the Win2000 HD to?  I'd like to be able to share files between the two OS if that is possible.

    Any help and suggestions would be much appreciated.  I can't do anything yet as I don't even have the Ubuntu install disk, or the needed pata to sata converter fot the 2nd hd yet - they should be in the mail but I don't expect them until after Christmas.  I also only have intermittent Internet access (through friends) until I get a vista compatible wireless card – in the mail, I picked one that is supposed to be Linux and vista compatible.

    Thanks

---

### Post by Duck2006 on 2008-12-23
If you are going to use the hole drive, then when your doing the install tell it to use the hole drive and it will do it all for you.

This may help with installing ubuntu. Just use the ubuntu install part.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by mikewhatever on 2008-12-23
Hi and welcome,

the tutorials you saw on partitioning and installing apply to any HDD you choose to install Ubuntu on. It doesn't matter if one or several other HDDs are connected.
[Istallation Guide]("http://psychocats.net/ubuntu/dualboot")
[Plan Partitions]("http://psychocats.net/ubuntu/partitioning")

The only 'complicated' decision to make in your case, is where to install GRUB, Ubuntu's boot loader.
Disconnecting the Vista HDD is a good idea to make sure you don't wipe out your data by accident.

---

### Post by mshipman on 2008-12-23
I have a similar setup to the one you are proposing:

1. 300GB SATA hard drive with Vista.
2. 250GB SATA hard drive with Ubuntu.

You can either install from the live CD, and Ubuntu will take over the bootloader on your first hard disk by default (don't worry, there will still be a chainloader entry for windows), or you can install GRUB to the MBR of the second hard drive and flip the boot order back and forth in the BIOS (This is what I've done because I reinstall one/both operating systems often).

---

### Post by mapes12 on 2008-12-23
Boot you machine using the Ubu Live CD or a [Gparted]("http://gparted.sourceforge.net/") Live CD. I prefer the latter.

Run Gparted (if you used the second option from the above it will already be running).

When in the Gparted GUI select **Device** then select your second HDD. Format it as Ext3 filesystem. This will wipe your current W2K installation and prepare the drive for Ubu.

Reboot the machine this time with the Ubu installation CD. Follow the installation instructions until you get to **Partitioning**. Select **Manual** then select the partition you just created on your second HDD (it will most probably be called sdb1) to install Ubu onto. You may have to do the same for your /home and Swap areas (can't remember but the installer will guide you).

After the install is complete your machine will reboot. Grub will then ask you which OS to start. It will know Ubu is on the second HDD from the configuration the installer has set.

That should be it. For other help checkout the link in my signature file.

I would not do this > Disconnecting the Vista HDD is a good idea to make sure you don't wipe out your data by accident.because if you do then Grub will have no idea that it needs to create a dual boot configuration and one or the other OS will not be accessible.

Although you have decided to have ubu on a second drive this does not mean that your Vista OS is "safe" from anything bad happening. Linux does not see drives as windoze does. It only see's file directories and devices (drives to you and me) are just a means of storing data.

Before you start any of this **Backup your Vista stuff!**

---

### Post by caljohnsmith on 2008-12-23
One of the main things to be aware of when you install Ubuntu to its own drive is where Grub goes; even if you install Ubuntu to a different drive than your internal drive, Grub by default will be installed to the MBR (Master Boot Record) of your internal drive so that it can take over the dual-booting process. I would recommend though installing Grub to the MBR of the Ubuntu drive, and that way you can keep your drives independent of each other. To boot Ubuntu you would just need to change your BIOS to boot the Ubuntu drive. If you accept the default and let Grub get installed to the MBR of your internal drive, then if you disconnect the Ubuntu drive or if anything happens to the Ubuntu drive, you won't be able to boot your Windows internal drive. To install Grub to the MBR of the Ubuntu drive, just click the "advanced" button near the end of the installation process and have Grub installed to /dev/sdb or whichever is the drive you are installing Ubuntu to. That's all there is to it. Let us know how it goes or if you run into problems. :)

---

### Post by Duck2006 on 2008-12-23
> **mshipman said:**
> I have a similar setup to the one you are proposing:

1. 300GB SATA hard drive with Vista.
2. 250GB SATA hard drive with Ubuntu.

You can either install from the live CD, and Ubuntu will take over the bootloader on your first hard disk by default (don't worry, there will still be a chainloader entry for windows), or you can install GRUB to the MBR of the second hard drive and flip the boot order back and forth in the BIOS (This is what I've done because I reinstall one/both operating systems often).

Or you can use EasyBCD to boot the system.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by FireLizard on 2008-12-23
Thanks for all the replies and links, everyone.

So far, putting the Grub on the Ubuntu drive is sounding like a good option because I don't really want to mess with my vista install at all - I don't have re-install disks, and because I'd like to be able to remove Ubuntu if I want with out messing up vista's boot.  Do you see problems with this?

I have a question for maples12:  is the "Ubu Live CD" the same as the desktop cd you can get from [http://www.ubuntu.com/getubuntu?](http://www.ubuntu.com/getubuntu?)

I'll let you all know how it goes when I get all the stuff and start installing.  Thanks again.

---

### Post by Duck2006 on 2008-12-23
> **FireLizard said:**
> Thanks for all the replies and links, everyone.

So far, putting the Grub on the Ubuntu drive is sounding like a good option because I don't really want to mess with my vista install at all - I don't have re-install disks, and because I'd like to be able to remove Ubuntu if I want with out messing up vista's boot.  Do you see problems with this?

I have a question for maples12:  is the "Ubu Live CD" the same as the desktop cd you can get from [http://www.ubuntu.com/getubuntu?](http://www.ubuntu.com/getubuntu?)

I'll let you all know how it goes when I get all the stuff and start installing.  Thanks again.

Yes

---

### Post by mapes12 on 2008-12-23
> **FireLizard said:**
> Thanks for all the replies and links, everyone.

So far, putting the Grub on the Ubuntu drive is sounding like a good option because I don't really want to mess with my vista install at all - I don't have re-install disks, and because I'd like to be able to remove Ubuntu if I want with out messing up vista's boot.  Do you see problems with this?

I have a question for maples12:  is the "Ubu Live CD" the same as the desktop cd you can get from [http://www.ubuntu.com/getubuntu?](http://www.ubuntu.com/getubuntu?)

I'll let you all know how it goes when I get all the stuff and start installing.  Thanks again.

I'm not convinced this would work. My understanding is that you can only have one MBR on a working system. GNU GRUB (GRand Unified Bootloader) is a program that installs a boot loader **to** the MBR, which exists at the beginning sectors of a disk. It allows you to place specific instructions **in** the MBR that loads a GRUB menu or command environment, allowing you to start the operating system of your choice, pass special instructions to kernels when they boot, or discover system parameters (such as available RAM) before booting. 

Having said the above I've never tried it. The concept of changing boot drives in the BIOS to change OS's is interesting. I would be interested to learn how it goes.

---

### Post by mapes12 on 2008-12-23
> **FireLizard said:**
> Thanks for all the replies and links, everyone.

So far, putting the Grub on the Ubuntu drive is sounding like a good option because I don't really want to mess with my vista install at all - I don't have re-install disks, and because I'd like to be able to remove Ubuntu if I want with out messing up vista's boot.  Do you see problems with this?

I have a question for maples12:  is the "Ubu Live CD" the same as the desktop cd you can get from [http://www.ubuntu.com/getubuntu?](http://www.ubuntu.com/getubuntu?)

I'll let you all know how it goes when I get all the stuff and start installing.  Thanks again.

YEP! If the Live CD fails try the text based [URL="http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"]alternate installer CD
[/URL]

---

