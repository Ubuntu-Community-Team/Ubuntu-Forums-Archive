---
title: "Problems creating dual-boot partition with gparted"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by jimhoff on 2009-09-23
I've been using Ubuntu for the past few months and have ran into my first problem that I can't figure out with a google search.

I'm trying to create a partition on the harddrive to run xp programs (netflix, itunes).

However, when I try to resize the /dev/sda1, the option is greyed out. I can't really figure out how to ungrey it, or why I wouldn't be able to resize it. I am not running gparted from the live CD as most directions say to do, but that is because I do not have a live CD and thought it might not be necessary.

The other partitions I have are /dev/sda2 and /dev/sda5 which seems to be a subgroup of the sda2.

Your help is much appreciated, I look forward to being able to update my ipod touch.

---

### Post by wojox on 2009-09-23
Sure, You'll have to download and burn a live cd. You can't format the drive while it's mounted. Boot from cd drive and run gparted. When you get to the options page select try Ubuntu without installing.

---

### Post by jimhoff on 2009-09-23
So i'll have to download the entire livecd? My problem is that I have a dial up connection so the livecd could take a very long time to download. Is there a way to have just gparted or something smaller than the livecd to boot from? 

Thanks for the speedy response!

---

### Post by wojox on 2009-09-23
Sure here's a link for just gparted:

[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

---

### Post by jimhoff on 2009-09-23
What would I do once I download one of those files?  How could I get it to run off of a flash drive usb?

---

### Post by LewRockwell on 2009-09-23
use Synaptic to get unetbootin

super!

.

---

### Post by jimhoff on 2009-09-23
Thanks Lew, love your website.

---

### Post by oldfred on 2009-09-23
Make sure when you create the new partition that it is a primary partition. Windows only really works in a primary partition.

Some info on dual booting:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

If you are running 9.04 you can create a USB Disk from the administration menu. You can then run gparted from that and reinstall Grub after windows overwrites it.
Some answers to issues with trying to boot from USB on older computers:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by jimhoff on 2009-09-23
I've got windows XP installed on the partition, but now I am having problems getting it to boot ubuntu. I made a backup of the GRUB boot loader, but I can't figure out how to get a terminal thingy in order to run the commands to restore it. Is there another thing I could download whilst in XP and put onto a flash stick and get to the point where I can restore the GRUB menu? Thnx

---

### Post by oldfred on 2009-09-24
Just about any live disk will work. If you did not download the gparted one you can download any live disk. Most small ones are about 100mb.

The smallest download is probably supergrub which will allow you to choose to fix the boot from its menu. It has small CD (about 4.4mb), floppy and USB versions. 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Darkwing-Duck on 2009-09-29
Here is another way to restore grub with the LiveCD. 

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

hope this helps you out.

---

