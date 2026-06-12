---
title: "cannot mount external hd after upgrading to 11.04"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by floydian sod on 2011-06-18
i just formatted and installed ubuntu 11.04 to my laptop and cannot access my ext4 filesystem 1tb wd hard drive. used to work perfectly on karmic koala, now when i look it up on disk utility, it looks empty and not formatted. everything i own is on that hard drive, and i simply can not format it.

here are mount, lsusb and fdisk -l outputs from terminal:

mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
none on /sys type sysfs (rw,noexec,nosuid,nodev) 
fusectl on /sys/fs/fuse/connections type fusectl (rw) 
none on /sys/kernel/debug type debugfs (rw) 
none on /sys/kernel/security type securityfs (rw) 
none on /dev type devtmpfs (rw,mode=0755) 
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
none on /dev/shm type tmpfs (rw,nosuid,nodev) 
none on /var/run type tmpfs (rw,nosuid,mode=0755) 
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev) 
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 
gvfs-fuse-daemon on /home/sodo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sodo) 

lsusb 
Bus 005 Device 002: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 005: ID 07a6:8515 ADMtek, Inc. AN8515 Ethernet 
Bus 001 Device 004: ID 1058:1021 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

sudo fdisk -l 

Disk /dev/sda: 78.5 GB, 78518522880 bytes 
255 heads, 63 sectors/track, 9546 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x86b7a0a0 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1            4255        4741     3903796    5  Extended 
/dev/sda2               1        4254    34170223+  83  Linux 
/dev/sda3   *        4742        9545    38588130    7  HPFS/NTFS 
/dev/sda5            4256        4741     3903795   82  Linux swap / Solaris 

Partition table entries are not in disk order 

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes 
255 heads, 63 sectors/track, 121600 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x00000000 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb4          165075      288932   994885933    0  Empty 
Partition 4 does not end on cylinder boundary.

ps: i forgot to unplug the usb when formatting, but used advanced options and formatted only linux partition.

---

### Post by wildmanne39 on 2011-06-18
Hi, but you show in the first part of your message that your external drive is ext4, so you might have3 formated it, do you get a permission denied? you should check in disk utility and see if it is mounted then you should be able to see what is going on with it.

---

### Post by jtarin on 2011-06-18
> it looks empty and not formatted. everything i own is on that hard drive, and _**i simply can not format it**_.If everything you own is on that drive I would advise not to format it until you can back up the data to another location.
Sometimes simply unplugging the drive and plugging back in works wonders.
Will you be leaving this drive plugged in all the time or only temporary from time to time?

---

### Post by floydian sod on 2011-06-20
> **wildmanne39 said:**
> Hi, but you show in the first part of your message that your external drive is ext4, so you might have3 formated it, do you get a permission denied? you should check in disk utility and see if it is mounted then you should be able to see what is going on with it.

attached the ss, that's what the disk utility says.

---

### Post by floydian sod on 2011-06-20
> **jtarin said:**
> If everything you own is on that drive I would advise not to format it until you can back up the data to another location.
Sometimes simply unplugging the drive and plugging back in works wonders.
Will you be leaving this drive plugged in all the time or only temporary from time to time?

i use the drive plugged in at all times, and have tried unplugging and replugging several times. did not work, unfortunately.

---

### Post by jtarin on 2011-06-20
Issue the command ```
df
``` in a terminal and post results.

---

### Post by floydian sod on 2011-06-20
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             33633412   4746876  27178028  15% /
none                    505396       676    504720   1% /dev
none                    512008       316    511692   1% /dev/shm
none                    512008        88    511920   1% /var/run
none                    512008         0    512008   0% /var/lock
/dev/sda3             38588128  37805880    782248  98% /media/vindovs partisyonu


no sign of the external hard drive.

---

### Post by wildmanne39 on 2011-06-20
> **floydian sod said:**
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             33633412   4746876  27178028  15% /
none                    505396       676    504720   1% /dev
none                    512008       316    511692   1% /dev/shm
none                    512008        88    511920   1% /var/run
none                    512008         0    512008   0% /var/lock
/dev/sda3             38588128  37805880    782248  98% /media/vindovs partisyonu


no sign of the external hard drive.

Hi, according to disk utility your usb drive is empty, and does not have a partition on it. You can possibly still recover the data if you do not write anything to that disk before attempting to recover the data. Maybe jtarin will be back and take another look soon and tell you more.

---

### Post by floydian sod on 2011-06-20
> **wildmanne39 said:**
> Hi, according to disk utility your usb , and drive is empty, and does not have a partition on it.

and therefore i can't save the data?
(please don't tell me i can't!)

---

### Post by jtarin on 2011-06-20
The only thing I can suggest at this time is to look at the [documentation ]("https://help.ubuntu.com/community/DataRecovery")and proceed accordingly. The possibility exist for you to save some data.
One other not mentioned there is [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") which many use and swear by.....try first.
[Additional info and methods on above apps.]("http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/")
A problem I see you possibly having recovering is the fact that your trying to recover a 1TB disk......it's going to be difficult to image that and have someplace to back it up to.

---

### Post by floydian sod on 2011-06-20
> **jtarin said:**
> The only thing I can suggest at this time is to look at the [documentation ]("https://help.ubuntu.com/community/DataRecovery")and proceed accordingly. The possibility exist for you to save some data.
One other not mentioned there is [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") which many use and swear by.....try first.
[Additional info and methods on above apps.]("http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/")
A problem I see you possibly having recovering is the fact that your trying to recover a 1TB disk......it's going to be difficult to image that and have someplace to back it up to.

no kidding (=

guess i'll manage somehow. thanks for all the help and info. 
i'll do it as soon as i can get my hands on another 1tb or above hd.

---

### Post by nlneilson on 2011-06-22
I have a similar problem.
USB flash drives with executable apps cannot be executed.
Apparently, since Ubuntu 10.04 by default they are "noexec".

How is "exec" flag set??

With 9.10 there was no problem.
With 11.04 the executable apps will not run from a USB flash drive and will probably have the same problem with an SD card, external hdd, CD-DVD etc.

The apps run OK when copied to the hdd and even a USB drive at a terminal with:
java -Xmx512m -Dsun.java2d.noddraw=true -Djava.library.path=. -jar NLNww.jar

The .bash file that contains this the Permission->Allow executing ... cannot be set because of no execute bit on FAT the Permission must be set for the drive.

I have been unable to find how this is done.

Most of my dev work is done in M$ so my use of Ubuntu is limited.

Any help on this would be appreciated.

Neil

---

### Post by jtarin on 2011-06-22
> **nlneilson said:**
> I have a similar problem.
USB flash drives with executable apps cannot be executed.
Apparently, since Ubuntu 10.04 by default they are "noexec".

Give an example of an executable apps.

---

### Post by nlneilson on 2011-06-22
[http://nlneilson.com/apps/NLN.zip](http://nlneilson.com/apps/NLN.zip)
[http://www.nlneilson.com/nlnww.html](http://www.nlneilson.com/nlnww.html)

The C/C++ app works OK.

The Java app does not except from a terminal.

The NLNww.bash file cannot be given Permission as executable.

A similar app when 9.10 was installed worked OK.

edit: In the NLNe app you can just copy and and past in Point1 your location and place a comma between the lat and lon 43° 7' 41", 131° 54' 3" and push Enter. Then Calc->Points->GoTo Point 1

Thanks

Neil

---

### Post by nlneilson on 2011-07-05
A bug report has been filed with Ubuntu and confirmed.

Quote:
[Bug 805298] Re: apps on removable media (FAT formatted) cannot be given execute premission

** Changed in: udisks (Ubuntu)
Status: New => Confirmed
____________

---

