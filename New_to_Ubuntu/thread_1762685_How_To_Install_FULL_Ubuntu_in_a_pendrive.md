---
title: "How To Install FULL Ubuntu in a pendrive?"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by rez182 on 2011-05-19
how can i install the full ubuntu to a pendrive as if it were the HDD? is it possible to do it directly from ubuntu running in a HDD? BTW im not talkin about LiveUSB.

Thank.

---

### Post by oldfred on 2011-05-19
It is really just like any install to a second drive. Some suggest disconnecting internal drive to prevent grub overwriting sda as that is where it defaults to. If you use manual install and tell grub to install to the drive that is the USB flash drive then you will be ok. With a flash drive you do want to make some settings to reduce writes. Writes are very slow. Flash install is slow both due to flash and USB port, but if configured to minimize writes, it is functional.  If you are planning on using on more  than one computer do not install any proprietary video drivers.

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

You can boot an ISO on your hard drive to use to install.
This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by beew on 2011-05-19
First create a live CD or a live usb (can use unetbootin) for installing. 

Boot into the live CD or live usb.

Attach the usb into which you want to install (note the drive label, so for example, if you use a live usb for installing the drive to install into would probably be /dev/sdc, sda would be your internal drive, sdb would be the live usb for installing)

Then just install Ubuntu like you would normally except you must make sure the target of installation is indeed the usb you intended to install into (say sdc in our example)

Choose manual partition, that way you can choose where to install grub (it should be installed in the usb, so it would be sdc in our example, be careful here for if you install grub into the internal drive your computer will be not bootable afterwards, it can be fixed easily but you want to avoid the trouble in the first place)

You need at least a / partition (mount point /) and a swap partition (linux swap) . You can add an optional /home partition if you want though I am not sure if there is a point for a usb install. The / partition and the /home partition should be formatted as ext4.

Then just install.

usb install can be quite slow, if you want both portability and performance I suggest it is a lot better to install into an external hard drive instead.

---

### Post by rez182 on 2011-05-19
will disabling the HDD from BIOS prevent causing any problem to the HDD GRUB while installing ubuntu in a USB drive?

having a portable ubuntu will be great plus i want to test my 11.04 with the graphic driver i have. i messend up badly in my previous tries. lost all my data (win7, ubuntu 10.10) long sad story. so i wanna try all the new fixs in a pendrive.

BTW i wanna is it possible to install ubuntu in a USB drive with the installation files in the same USB drive?

---

### Post by oldfred on 2011-05-19
You might be able to install from same flash drive if you have the installer in one partition and then install to other partitions. Not sure if it works or not as I have not tried that. I have installed from one flash to another but on boot sdg became sdf and UUID search stopped so I had to edit grub menu entry to get it to work.

---

### Post by rez182 on 2011-05-19
will disabling my HDD from BIOS prevent any change of the Grub in the HDD?

---

### Post by pritam_par on 2011-08-19
To install Ubuntu on pendrive only you need to plug in the pendrive when you are booting from the Ubuntu CD, and at the time of selecting the hard disk partition select the pendrive partition and follow the other steps as usual.
_________________________________
[URL="http://opensource-sidh.blogspot.com/"]My BloG on Open Source 
[/URL]

---

### Post by katakaio on 2011-08-19
An entirely different approach that accomplishes the same thing is to use Portable Ubuntu. If you simply want to plug your USB into a Windows machine and boot up Ubuntu, this works fantastically well. (Great for internet cafes, btw.) It starts out less than 512 MB the last time I checked - you can read the Lifehacker article [here]("http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows"). I've used it often and I can't complain, so if you want Ubuntu on a stick for a Windows environment, this is a really great solution.

---

