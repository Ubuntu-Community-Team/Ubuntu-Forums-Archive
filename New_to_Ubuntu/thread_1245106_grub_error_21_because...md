---
title: "grub error 21 because.."
date: 2009-08-20
forum: New to Ubuntu
---

### Post by epidemiks on 2009-08-20
..the harddrive it was on is dead: ext-fs dissapeared, followed by the ntfs file system on the other partition of the disk. 

if that's catastrophic hardware failure wasn't hard enough to swallow, so now i can't boot into my xp install. and all the restore grub howto's aren't working as grub can't find stage1..

how can I just get rid of grub 100% so xp will boot?

(i do plan on reinstalling 8.10 as soon as humanly possible on the new 1TB drive, btw :))



this might help:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd214d214

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   160,055,594   119,089,845   f W95 Ext d (LBA)
/dev/sda5          40,965,813   160,055,594   119,089,782   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="786CA42F6CA3E65A" TYPE="ntfs" 
/dev/sda5: UUID="5C182B87182B5F70" LABEL="Audio Data" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /media/Audio Data type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /mnt/root type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

```

---

### Post by alexlafreniere on 2009-08-20
Boot into your XP install disc and repair your installation. This will overwrite your master boot record and reinstall the XP bootloader (or lack thereof). Is the Linux install on a completely different drive as the XP install? If that's the case just pull the Linux drive, your system will default to the XP install at boot.

---

### Post by epidemiks on 2009-08-21
> **alexlafreniere said:**
> Boot into your XP install disc and repair your installation. This will overwrite your master boot record and reinstall the XP bootloader (or lack thereof). Is the Linux install on a completely different drive as the XP install? If that's the case just pull the Linux drive, your system will default to the XP install at boot.

the linux drive is gone, as in pulled out already.. I've put grub on the xp disc or something similarly stupid

I'll track down my xp disc and try the repair, it's been so long since i've had to do anything xp related, i've almost forgotten how :lolflag:

thanks!

---

### Post by gn2 on 2009-08-21
You can use a SuperGrub CD to reinstate the Windows bootloader.

[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

---

