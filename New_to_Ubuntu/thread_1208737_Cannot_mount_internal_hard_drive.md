---
title: "Cannot mount internal hard drive"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by cruise.tammy on 2009-07-09
Hello-

I'm a beginner to ubuntu (9.04) and am trying to force mount my internal HD because I can't boot from Windows XP. I'm trying to recover my data. Please help, and many thanks in advance.
This is the information:

ubuntu@ubuntu:~$ sudo /bin/bash
root@ubuntu:~# mkdir /media/disk
mkdir: cannot create directory `/media/disk': File exists
root@ubuntu:~# mount -t ntfs-3g /dev/sda1 /media/disk -o force
Failed to read last sector (234436481): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@ubuntu:~# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x76ba76ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10337    78147688+   7  HPFS/NTFS
root@ubuntu:~#

---

### Post by LewRockwell on 2009-07-09
first of all, stop hacking on it and let's see what we can do

.

---

### Post by LewRockwell on 2009-07-09
give us a rundown of your equipment and such while you're waiting

.

---

### Post by cruise.tammy on 2009-07-09
Ok thanks LewRockwell, I look forward to your suggestions.

---

### Post by cruise.tammy on 2009-07-09
I have an e-machines T-2892 desktop.
When I try to boot Windows XP Home, the e-machines logo appears then it goes to a black screen with a blinking cursor at the top left corner.

---

### Post by LewRockwell on 2009-07-09
ok, first thing you want to do is get one of these and learn how to use it to work MAGIC

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

then, if supergrub can't find your windows bootloader and get you in...

you'll get Parted Magic and use Testdisk and/or Photorec to recover, if necessary...

[http://www.partedmagic.com/](http://www.partedmagic.com/)

...no back-up?

.

---

### Post by cruise.tammy on 2009-07-09
Thanks LewRockwell. I'll try your solutions and let you know the results.
Sorry, my external hard drive crashed a few days ago, so I had no back-up.

---

### Post by IHeequ5i on 2009-07-09
When did your XP partition stop working? Had you changed anything on it? 

Have you tried bringing XP up in Safe Mode (press the F8 key while the e-Machines logo is displayed). You should get a menu of options and one will be Safe Mode. This is a very generic Windows option with minimal driver support, but if it works you will be able to recover your data.

Were you running a dual boot system with Ubuntu and XP, or did you install Ubuntu on a secondary drive?  Just trying to understand exactly what you did.

---

### Post by LewRockwell on 2009-07-09
it should also be noted that supergrubdisk does MUCH more than meets the eye at first glance...

sure, for some folks the automatic stuff works, but for others a little more interaction is required...

same for parted magic, as it is a liveCD with internet connectivity, firefox, gparted, clonezilla, secure erase, and other utilities as well

.

---

### Post by LewRockwell on 2009-07-09
> **cruise.tammy said:**
> Thanks LewRockwell. I'll try your solutions and let you know the results.
Sorry, my external hard drive crashed a few days ago, so I had no back-up.

actually you might surprise yourself and rescue that drive as well

.

---

### Post by cruise.tammy on 2009-07-09
> **Doomspark said:**
> When did your XP partition stop working? Had you changed anything on it? 

Have you tried bringing XP up in Safe Mode (press the F8 key while the e-Machines logo is displayed). You should get a menu of options and one will be Safe Mode. This is a very generic Windows option with minimal driver support, but if it works you will be able to recover your data.

Were you running a dual boot system with Ubuntu and XP, or did you install Ubuntu on a secondary drive?  Just trying to understand exactly what you did.

Hello Doomspark- I was deleting some start-up icons and shut down my computer. When I tried restarting, it wouldn't boot and went to the black screen with "blinking cursor." I think I deleted a .ini file by mistake. I tried using safe mode but it did not work. I was not running a dual system, just XP Home. I only have a 120 GB HD, no secondary drive. I downloaded Ubuntu as an iso file burned it to CD and am using it to try and recover my data.

---

