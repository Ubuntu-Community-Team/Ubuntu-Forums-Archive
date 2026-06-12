---
title: "Partitioner Problem installing Ununtu 9.1 over WinXP"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by jmattos on 2009-12-14
so im trying to install ubuntu 9.1 over windows xp on my shuttle pc (sn25p). It boots from the CD fine and I go through the installation wizard until the point where I get to the partitioner.

all the buttons are disabled (new partition table, add..., change..., Delete, Revert) and when I click forward it tells me I have no partitions defined.

Is this because I have windows xp installed on my main (and only) HD? Is it an NTFS thing?

Help!

---

### Post by lazbuddie on 2009-12-14
I have the same problem on 13 out of 73 Ibm T30 think pads. The best I have come up with is that it is a BIOS problem. I would like to know too.

---

### Post by Chesamo on 2009-12-14
Did you actually click on the drive (first item in the list)? You have to do that.

Also, it's Ubuntu 9.10 (as in, the nine-point-ten; or nine-point-one-zero if you *really* feel like being technically correct), not 9.1 (as in nine-point-one).

---

### Post by ukripper on 2009-12-14
> **jmattos said:**
> so im trying to install ubuntu 9.1 over windows xp on my shuttle pc (sn25p). It boots from the CD fine and I go through the installation wizard until the point where I get to the partitioner.

all the buttons are disabled (new partition table, add..., change..., Delete, Revert) and when I click forward it tells me I have no partitions defined.

Is this because I have windows xp installed on my main (and only) HD? Is it an NTFS thing?

Help!

Check your Cd for defects. When you boot with ubuntu 9.10 cd it gives option to check if CD has defects.

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
Did you try to partition using GParted first? Sometimes GParted will let you do things that the partition editor in the installer doesn't want to.

---

### Post by spydeyrch on 2009-12-14
If you really don't want your XP partition and want to write over it, I would recommend using Gparted first. If you can, [download gparted]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/"). Burn it to a cd (waste of a good cd if you ask me because there is a better way) and then boot it. Use Gparted to reformat your hdd to something like fat32 or some other older file system.  BE WARNED!!!!! IF YOU DO THIS TO YOUR ENTIRE HARD DRIVE, YOU WILL LOSE ANY AND ALL DATA YOU HAD STORED ON IT!!!!! You can also, just shrink or enlarge your XP partition, that way you don't lose all your data, that is if you want to keep some of it. Do it at your own risk though.
 
Once done, boot up your ubuntu 9.10 cd and then have at it!! Should work. :D
 
----------------
 
A better way to use gparted.
 
 [Download UnetBootin]("http://unetbootin.sourceforge.net/") and us a USB thumb drive (flash drive) to boot gparted. Unetbootin will take the .iso file of gparted and "burn" it to the usb flash drive, thereby making the usb flash drive bootable In my experience, it boots faster off of a usb flash drive than a cd. One thing really quickly though, your computer needs to be able to boot off of a usb drive. Check yoru BIOS for that option. Sometimes during POST, if you hit F12, it will give you a boot menu and you can choose the correct device to boot from. Your boot menu key might be different, refer back to your BIOS/users manul.
 
If you can boot off of a usb flash drive, then use gparted that way and ....... :o OHHH HEY!!! Now you can boot your ubuntu install off of a usb drive too!!! YAY!!! :popcorn:
 
The bootup into ubuntu live and the install will go much faster off of a usb flash drive than a cd, as I previously mentioned. Have at it! :P
 
-Spydey

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
Why would anyone d/l and burn an app that comes ready to use on the live CD that they're going to install from anyway?

---

### Post by spydeyrch on 2009-12-14
Well, I wasn't thinking about the fact that, yes, the live cd does have gparted. Sorry about that. I got on stuck on the mind frame of "gparted" and the first thing that came to my mind was to directly download it. Granted you could do it both ways, download it and also use the one provided on the live cd. :D
 
Let us know how it turns out. :popcorn:

---

