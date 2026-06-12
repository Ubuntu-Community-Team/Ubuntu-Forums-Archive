---
title: "USB flash drive is &quot;not a block device&quot;"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by PuddingKnife on 2010-11-18
So, I have a netbook that is unable to connect to the internet, via wireless or ethernet connection. 

I am trying to mount my USB drive to /cdrom so that Synaptic can view it as a software source, in order to install the firmware I need for the wireless card. Its not going well..

I dont know what other information to give you, so just ask :)

---

### Post by pizza-is-good on 2010-11-18
Well, I'm not sure you can mount a USB to /cdrom. USB devices usually mount to /media. But, keep reading...

Is your USB /dev/sdb ?

You can find out by typing ```
sudo fdisk -l
``` in your terminal. I will list all devices in /dev. You can tell which is which by the size. The USB has to be pugged in.
[COLOR=Red]
Assuming it is /dev/sdb (change it to whatever it is), right click it on your desktop, select unmount, open a terminal, and type:

```
sudo mount -v /dev/sdb /cdrom
```The 'v' is to see if it gives you any errors. Again, change sdb to whatever your USB is.[/COLOR] [COLOR=Red]

If this doesn't work, I'm not sure it is possible.... But ask questions.[/COLOR] [COLOR=Red]

Good luck![/COLOR] 

~pizza

[COLOR=Red]Edit: It apparently does not work, as the command *mount* does not support FAT32. Supported file types according to man-page are ```
adfs,  affs,  autofs,  cifs,  coda,  coherent,  cramfs, debugfs, devpts, efs, ext, ext2, ext3, ext4, hfs, hfsplus, hpfs,
              iso9660, jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc,  qnx4,
              ramfs,  reiserfs,  romfs,  squashfs,  smbfs, sysv, tmpfs, ubifs,
              udf, ufs, umsdos, usbfs, vfat, xenix,  xfs,  xiafs
```Anyone have any suggestions?
[/COLOR]
[B]2nd Edit:

OK, maybe it does work. I didn't get the variables on the command right.
Try:
```
sudo mount -v -t vfat /dev/sdb1 /cdrom
```
This actually mounted my flash drive to /cdrom, BUT, synaptic was not able to read it. Maybe because my usb didn't have software sources.... At least it knew the drive was on /cdrom.

Good luck again...
[/B]

---

### Post by mcduck on 2010-11-19
> **PuddingKnife said:**
> So, I have a netbook that is unable to connect to the internet, via wireless or ethernet connection. 

I am trying to mount my USB drive to /cdrom so that Synaptic can view it as a software source, in order to install the firmware I need for the wireless card. Its not going well..

I dont know what other information to give you, so just ask :)

Why not just mount the USB drive in the normal way, and install the firmware directly from there?

If it's a .deb package you already have, you don't need Synaptic to install it. (and if it's *no*t a .deb package, Synaptic wont help you anyway).

You should be able to simply click the package to install it, or of course running "sudo dpkg -i *nameofthepackage*" works as well.

edit: I almost forgot, USB flash drive *is* a block device, so whatever command you tried to run when you got the error must have been wrong. Most likely you had some error in the device name.

---

### Post by PuddingKnife on 2010-11-19
I have Maverick installed on my USB drive. It is a 2gig flash drive. I need to install the broadcom drivers from the flash drive to the netbook, since it has no way of connecting to the internet. 

I tried 
```
sudo mount -v -t vfat /dev/sdb /cdrom
```

I get
> mount: /dev/sdb already mounted or /cdrom busy

sBut of course the netbook doesn't have a cdrom drive, So Im not sure what to do about that..

Is there an easier way to install the broadcom drivers from the USB without mounting it as /cdrom? As I understand it, it needs to be mounted as /cdrom in order for Synaptic to recognize it.

---

### Post by PuddingKnife on 2010-11-20
bump

---

### Post by cmcanulty on 2010-11-20
use this
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by mcduck on 2010-11-22
> **PuddingKnife said:**
> Is there an easier way to install the broadcom drivers from the USB without mounting it as /cdrom? As I understand it, it needs to be mounted as /cdrom in order for Synaptic to recognize it.
Yes, Just let it mount like a USB drive would normally do, browse into the device, find the package you want to install and click it.

However, you said that you have Maverick *installed* on that USB drive. Do you really mean it's an installed, working system on the USB drive? In that case it's not going to help you, you want the installer CD (which contains packages), not an installed system (which contains installed software, not the packages any more.)

---

### Post by fallencx on 2011-01-06
I think he means he has the installer CD installed into that usb. If not, that's my issue. Just a suggestion, but in plain english, I need a code that I can input in terminal that will read my USB flash as the CDrom drive so that synaptic can read it like that and I can install ndisgtk and ndiswrapper.

---

### Post by fallencx on 2011-01-06
I think I found what we're looking for.
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/98324](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/98324)

---

