---
title: "Burn ISO to External Hard Drive?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Ron Carson on 2011-04-30
Using Unetbootin, I'm able to burn the 11.04 ISO to my external hard drive. My computer is set to boot from the drive and it does access it during boot, but I get an error.

I've never tried booting from an external hard drive. When I looked at the hard drive with Gparted, it says there's no mount point.  In order to boot from this drive (WHICH HAS LOTS OF PERSONAL AND BACKUP FILES), must I partition it first?

---

### Post by dniMretsaM on 2011-04-30
I do not know if it would be necessary, but I think it would be best to help prevent corruption of any of your important data.

---

### Post by Dondermans on 2011-04-30
> **Ron Carson said:**
> Using Unetbootin, I'm able to burn the 11.04 ISO to my external hard drive. My computer is set to boot from the drive and it does access it during boot, but I get an error.

I've never tried booting from an external hard drive. When I looked at the hard drive with Gparted, it says there's no mount point.  In order to boot from this drive (WHICH HAS LOTS OF PERSONAL AND BACKUP FILES), must I partition it first?
Why would you want to do that?

---

### Post by Ron Carson on 2011-04-30
> **Dondermans said:**
> Why would you want to do that?
Do what?  Partition it?  If it's not needed, then I won't. 

I just want to burn the ISO to the USB hard drive and boot from it?  I'm obviously missing something!!!

---

### Post by Dondermans on 2011-04-30
I am sorry for the confusion. I'll rephrase: I wondered why you would want to burn an .iso to a drive which contains your personal *and* backup files. 

At the very least I would move the backup files elsewhere to make sure they are not on the same disk as your operating system.

---

### Post by oldfred on 2011-04-30
Most of the default programs to burn ISO or make USB assume they are small devices and erase everything.

But you can loop mount boot an ISO file from a hard drive or flash drive. It is a bit more advanced and the scripts that automate it also assume you want to reformat. But if you manually install grub2 as a boot loader, copy the ISO as a ISO to the drive in /boot/iso and edit grub.cfg to loopmount the ISO it is possible.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by Ron Carson on 2011-04-30
The Unetbootin seems to have burned the ISO to my USB drive but the OS didn't seem to recognize it during boot. 

Obviously, I'm missing something

---

### Post by Quackers on 2011-04-30
I'm sorry if this sounds a bit basic, but we need to check that you understand it. If you burn an iso file to a disk it doesn't install the system in that iso file to the drive. It only burns the iso image.

---

### Post by Ron Carson on 2011-04-30
Actually Unetbootin burns it to the hard drive just as if it was CD.  It SHOULD run from the hard drive identically as a CD

---

### Post by Quackers on 2011-04-30
> **Ron Carson said:**
> Actually Unetbootin burns it to the hard drive just as if it was CD.  It SHOULD run from the hard drive identically as a CD

Indeed, but not as an installed system.
Burning an iso image to a disc which has an installed system or backups is an unusual thing to do. There are risks.

---

### Post by Ron Carson on 2011-04-30
> **Quackers said:**
> Indeed, but not as an installed system.
Burning an iso image to a disc which has an installed system or backups is an unusual thing to do. There are risks.

There is no system on the external drive, so no worry there.  What risks are specifically associate with burning an ISO to a hard drive already having files?

---

### Post by Quackers on 2011-04-30
The program which burns the image to the drive can sometimes insist on using the whole partition. Formatting it before it uses it. I hope that hasn't happened here.

---

### Post by Ron Carson on 2011-05-01
The program did NOT reformat the hard drive. So, I'm still left with my original question of do I need to partition the external hard drive to use it for booting?

---

### Post by beew on 2011-05-01
Why not do a full installation in the external harddrive? It is much better than a live usb with persistence in that it is a real install just like installing into an internal disk (so you can do system level upgrades, install new kernel and do anything you can do in an internal installation), but you can boot from different machines just like a live usb.

I wouldn't even try doing what you do even if it can be done.  Also Unetbootin doesn't support persistence and I wouldn't even make a live usb with it unless it is only for the purpose of installing Ubuntu.

To install into an external drive, first create a live cd or live usb for installing (unetbootin would be fine), then boot into the live usb. Connect the external drive to the machine and choose installing Ubuntu, choose manual partition so that you can specify your partition layout, be careful that you install Ubuntu in the correct drive (so the external drive may be sdc, as sda is the internal drive, sdb maybe the live usb you are installing from) The partition layout would be a / partition (about 15G would be enough) and a /home partition to store data and settings, both formatted as ext4 and then a swap partition. Make sure you put the bootloader in the correct drive (sdc say) and then just proceed normally.

---

### Post by dFlyer on 2011-05-01
I can't answer your question. I would suggest you backup any data you don't want to loose regardless of what you do.

---

