---
title: "USB Drive - Read Only"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by dunbrokin on 2010-04-23
I have a USB drive to which I ocassionally transfer important files. When I tried to do so today it tole me that the drive was read only!!

I have tried changing the permissions as root...but it will not allow me to do so!!

How can this be?

What do I need to do to tame this beast!

---

### Post by TriBlox6432 on 2010-04-23
Do you have copies of everything that's on that flash drive somewhere else?

I've had this happen once, and I just popped it into my Windows machine and re formatted it and it worked great!

---

### Post by mikewhatever on 2010-04-23
Can you be more specific about 'changing permissions as root' and about 'it will not allow'. Also post the output of the following command:

```
cat /proc/mounts
```

Edit: I think formatting the drive right away is a little extrema.

---

### Post by 2hot6ft2 on 2010-04-23
Is it a flash drive or an external hard drive?

If it's a flash drive then like has already been said formatting it will usually solve the problem. First thing I do with a new flash drive is reformat it. I had your problem with one once and learned my lesson.

If it's an external hard drive what file system is it formatted to?
If it's NTFS try setting the permissions with
System > Administration > NTFS Configuration Tool
It has worked for me so far and is easier than editing the fstab.

---

### Post by dunbrokin on 2010-04-24
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev tmpfs rw,relatime,mode=755 0 0
/dev/disk/by-uuid/5e8cc14f-6d7f-46c4-91ea-4f6d508f3c01 / ext4 rw,relatime,errors=remount-ro,barrier=1,data=ordered 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
/dev/sda1 /boot ext4 rw,relatime,barrier=1,data=ordered 0 0
/dev/sda7 /usr ext4 rw,relatime,barrier=1,data=ordered 0 0
/dev/sda8 /var ext4 rw,relatime,barrier=1,data=ordered 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
/dev/sda9 /home ext4 rw,relatime,barrier=1,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/pj/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
/dev/sdb1 /media/USB\040DISK vfat ro,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro 0 


I don't see any NTFS Configuration Tool under System>Administration.

The drive is a USB pen drive.

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive
Bus 002 Device 004: ID 04f2:a138 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0a05:0001  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:63fe Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by mikewhatever on 2010-04-24
Looks like this is your drive:
/dev/sdb1 /media/USB\040DISK vfat ro,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0 022,dmask=0077,codepage=cp437,iocharset=iso8859-1,
shortname=mixed,utf8,flush,errors=remount-ro 0

The file system seems to be vfat (probably fat32), and it is mounted with permissions for the first created user. Are you the only user on that computer? What's the output of **id** command?

---

### Post by dunbrokin on 2010-04-24
uid=1000(pj) gid=1000(pj) groups=4(adm),20(dialout),21(fax),24(cdrom),26(tape),29(audio),30(dip),44(video),46(plugdev),104(fuse),106(lpadmin),112(netdev),121(admin),123(sambashare),1000(pj)

The other user is mm.

---

### Post by mikewhatever on 2010-04-24
Very interesting. From what you posted so far, the drive should not be a read only file system. Have you tried re-plugging it?
What are the outputs of the following two?

mkdir /media/USB\040DISK/test

ls -l /media/USB\040DISK

---

### Post by dunbrokin on 2010-04-24
pj@pj:~$ mkdir /media/USB\040DISK/test
mkdir: cannot create directory `/media/USB040DISK/test': No such file or directory
pj@pj:~$ ls -l /media/USB\040DISK
ls: cannot access /media/USB040DISK: No such file or directory

Replugged it numerous times...even turned the PC on and off again...still the same.

---

### Post by mikewhatever on 2010-04-24
Wait a minute, I must have been blind or something, but the drive is mounted as read only (ro). 

/dev/sdb1 /media/USB\040DISK vfat **ro**,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0 022,dmask=0077,codepage=cp437,iocharset=iso8859-1,
shortname=mixed,utf8,flush,errors=remount-ro 0

Try this:

devkit-disks --unmount /dev/sdb1

```

devkit-disks --mount-options rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0 022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro 0 --mount /dev/sdb1
```

This long command will try remounting the file system as rw keeping the rest of the options the same.

---

### Post by dunbrokin on 2010-04-24
Mount failed: Mount option relatime is not allowed

Changed relatime to realtime...and got the same answer i.e. not allowed.

---

### Post by mikewhatever on 2010-04-24
How about getting rid of that options:

```
devkit-disks --mount-options rw,nosuid,nodev,uid=1000,gid=1000,fmask=0 022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro 0 --mount /dev/sdb1
```

If that doesn't work too, try checking the file system. This may be wrong, but wouldn't hurt in any way, and besides, the options **errors=remount-ro** suggests the file system may be remounted as read only in case of errors. It's important to unmount the file system before checking:

devkit-disks --unmount /dev/sdb1

sudo fsck.vfat -yv /dev/sdb1

When done, try re-plugging.

---

### Post by dunbrokin on 2010-04-24
pj@pj:~$ devkit-disks --mount-options rw,nosuid,nodev,uid=1000,gid=1000,fmask=0 022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro 0 --mount /dev/sdb1
Mounted /org/freedesktop/DeviceKit/Disks/devices/sdb1 at /media/USB DISK
pj@pj:~$ devkit-disks --unmount /dev/sdb1
pj@pj:~$ fsck.vfat -yv /dev/sdb1
dosfsck 3.0.3 (18 May 2009)
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
open /dev/sdb1:Permission denied

---

### Post by mikewhatever on 2010-04-24
> **dunbrokin said:**
> pj@pj:~$ devkit-disks --mount-options rw,nosuid,nodev,uid=1000,gid=1000,fmask=0 022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro 0 --mount /dev/sdb1
Mounted /org/freedesktop/DeviceKit/Disks/devices/sdb1 at /media/USB DISK
pj@pj:~$ devkit-disks --unmount /dev/sdb1
pj@pj:~$ fsck.vfat -yv /dev/sdb1
dosfsck 3.0.3 (18 May 2009)
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
open /dev/sdb1:Permission denied

Well, the first command seem to have worked, as for fsck.vfat, I forgot to mention that it needs to be run with sudo, otherwise you get 'permission denied' error.

devkit-disks --unmount /dev/sdb1

sudo fsck.vfat -yv /dev/sdb1

---

### Post by dunbrokin on 2010-04-24
That seemed to work...thank you.....but why had it happened in the first place and how can I ensure it does not happen again?

---

### Post by mikewhatever on 2010-04-24
No idea. One possible explanation may this -> errors=remount-ro. In other words, the file system may have had errors and got remounted as read only. We can try further investigation by looking at the logs, for example:

less /var/log/dmesg | grep -i sd

---

### Post by dunbrokin on 2010-04-24
[    0.000000] ACPI: RSDP 000fb9f0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT dd051e00 00074 (v01 DELL    M09     27D80C12 ASL  00000061)
[    0.000000] ACPI: DSDT dd052400 064DB (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: SSDT dd050331 0066C (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.164216] ACPI: EC: Look up EC in DSDT
[    0.653673] ACPI: SSDT dd05099d 00281 (v01  PmRef   BspIst 00003000 INTL 20050624)
[    0.654096] ACPI: SSDT dd050df5 005C6 (v01  PmRef   BspCst 00003001 INTL 20050624)
[    0.654842] ACPI: SSDT dd050c1e 001D7 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.655132] ACPI: SSDT dd0513bb 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    1.576342] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.576370] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.576406] sd 0:0:0:0: [sda] Write Protect is off
[    1.576408] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.576426] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.576512]  sda: sda1 sda2 < sda5 sda6
[    1.623951]  sda7 sda8 sda9 >
[    1.651998] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.475525] EXT4-fs (sda6): barriers enabled
[    4.490757] kjournald2 starting: pid 447, dev sda6:8, commit interval 5 seconds
[    4.490921] EXT4-fs (sda6): delayed allocation enabled
[    4.492132] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    5.621177] Adding 9936160k swap on /dev/sda5.  Priority:-1 extents:1 across:9936160k 
[    7.228133] EXT4-fs (sda6): internal journal on sda6:8
[    7.649334] sdhci: Secure Digital Host Controller Interface driver
[    7.649337] sdhci: Copyright(c) Pierre Ossman
[    7.668792] sdhci-pci 0000:02:01.1: SDHCI controller found [1180:0822] (rev 22)
[    7.668816] sdhci-pci 0000:02:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    7.671863] mmc0: SDHCI controller on PCI [0000:02:01.1] using DMA
[    8.675987] EXT4-fs (sda1): barriers enabled
[    8.687320] kjournald2 starting: pid 911, dev sda1:8, commit interval 5 seconds
[    8.722623] EXT4-fs (sda1): internal journal on sda1:8
[    8.722626] EXT4-fs (sda1): delayed allocation enabled
[    8.723289] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    9.381707] EXT4-fs (sda7): barriers enabled
[    9.386871] kjournald2 starting: pid 963, dev sda7:8, commit interval 5 seconds
[    9.387472] EXT4-fs (sda7): internal journal on sda7:8
[    9.387477] EXT4-fs (sda7): delayed allocation enabled
[    9.388075] EXT4-fs (sda7): mounted filesystem with ordered data mode
[    9.821981] EXT4-fs (sda8): barriers enabled
[    9.849583] kjournald2 starting: pid 983, dev sda8:8, commit interval 5 seconds
[    9.857249] EXT4-fs (sda8): internal journal on sda8:8
[    9.857252] EXT4-fs (sda8): delayed allocation enabled
[    9.858385] EXT4-fs (sda8): mounted filesystem with ordered data mode
[   10.555117] EXT4-fs (sda9): barriers enabled
[   10.567324] kjournald2 starting: pid 1012, dev sda9:8, commit interval 5 seconds
[   10.575127] EXT4-fs (sda9): internal journal on sda9:8
[   10.575131] EXT4-fs (sda9): delayed allocation enabled
[   10.584171] EXT4-fs (sda9): mounted filesystem with ordered data mode
[   11.484984] type=1505 audit(1272076020.879:20): operation="profile_replace" pid=1079 name=/usr/sbin/cupsd

---

### Post by mikewhatever on 2010-04-25
Nothing about sdb is in that log, oh well, you must have rebooted since. ;)

---

### Post by dunbrokin on 2010-04-25
OK, thank you very much for your help...it is much appreciated.

---

### Post by rpstex on 2011-02-06
I'm using 10.10 latest packages, no pmount, usbmount installed, and I have been having problems getting 2 different usb hard drives and a sdcard in my htc vision (all 3 are fat32) to mount r/w.
Everytime I plug them in, i can only read from them in nautilus, no write
sudo modprobe usb_storage did nothing
i have nothing in my /etc/fstab about any usb devices,

and I just figured out a temporary fix
after i plug in my phone and (from the phone's screen)  Turn on USB Storage
i open terminal and sudo umount /dev/sdc1
if i have a nautilus window open of the disk, it flashes blank for a split second and all of sudden is read write.

if i sudo umount /media/VISION 
it works the exact same if i sudo umount /dev/sdc1

i wish i understood why this happens more clearly so that i could make my devices mount correctly the first time
  
this is the output of 'cat /proc/mounts' while usb drive is mounted read only (before I umount /dev/sdc1) :
/dev/sdc1 /media/VISION vfat rw,sync,nosuid,nodev,relatime,fmask=0002,dmask=0002,allow_utime=0020,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0

and this is the output of 'cat /proc/mounts' while usb drive has read/write (after i umount and then open /media/VISION in nautilus):
/dev/sdc1 /media/VISION vfat rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro 0 0

---

