---
title: "ineo i-na206 external hard drive"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by DWL52 on 2009-10-16
Hello all,
I just won a ineo i-na206 320 gig external hard drive at a computer show :). It plugs into a usb port, and the lights come on but the disk that came with it has executable files on it, obviously for a Windoze OS. I know I'm probably going to need to format it, which is no problem, but how do I get Ubuntu to recognize it? Any and dall help is greatly appreciated.

Dave

---

### Post by Rocket2DMn on 2009-10-16
If the drive is already formatted, you can use the existing filesystem, which is probably NTFS.  If you want to format it and start from scratch, I suggest using [GParted]("apt://gparted").  GParted is available on the Ubuntu LiveCD, or you can download it from the repositories by clicking that link or running:
```
sudo apt-get install gparted
```
Some brief directions on using GParted are here - [https://help.ubuntu.com/community/HowtoPartition/ReformattingPartition](https://help.ubuntu.com/community/HowtoPartition/ReformattingPartition)
If you plan on sharing data with Windows, you should use NTFS, but if it's only going to be used in linux, ext3 or ext4 are better options.

---

### Post by DWL52 on 2009-10-16
Got Gparted and installed. Pardon my ignorance, but I'm a newbie. I know to mount the drive I have to have it listed in /etc/fstab, but I don't know what drive designation it is, so I don't know what to put in there. Also, there are two lights that come on when I plug this drive into the usb port; one green and one red. The red one flashes, which I interpret to mean as something is wrong. I don't remember the comand to shhow me what drives the system recognizes. Any help? Thanks.

---

### Post by Rocket2DMn on 2009-10-16
Sure, first, you shouldn't have a fstab entry for external drives unless it's absolutely needed.  It is best to let automount figure out what the drive type is and mount it for you.  I don't know what the lights on your drive mean, but why don't you post the output of the following for me with your drive plugged in:
```
sudo fdisk -l
cat /etc/fstab
mount
blkid
```

Also note that the drive needs to be unmounted if you want to reformat/repartition it.

---

### Post by DWL52 on 2009-10-16
OK, got the drive working and it is recognized when I reboot, but will not let me read or write to it unless I log in as root. I think this has to do with going in as root and changing the permissions to myself, which I'm pretty sure I know how to do. What I would like to do now is to get it to automount when I start the computer, or is that inherent with changing the permissions?

---

### Post by Rocket2DMn on 2009-10-16
Have you removed the fstab entry?  It's probably configured there to not allow you to write to access it, which is one reason to not have a fstab entry for external disks - it is better to let automount take care of it.  If you post the commands above, I can get a better idea of what is going on.
Did you reformat the drive with GParted, or are you still using the original filesystem the drive came with?

---

### Post by DWL52 on 2009-10-16
The results for sudo fdisk -lsudo fdisk -l are:[FONT=Verdana]

[/FONT]Disk /dev/sda: 500.1 GB, 500107862016 bytes[FONT=Verdana]
[/FONT]255 heads, 63 sectors/track, 60801 cylinders[FONT=Verdana]
[/FONT]Units = cylinders of 16065 * 512 = 8225280 bytes[FONT=Verdana]
[/FONT]Disk identifier: 0x617fe23a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 61.4 GB, 61471162368 bytes
255 heads, 63 sectors/track, 7473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x434bbe61
dave@dave-desktop:~$ sudo fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7163    57536766   83  Linux
/dev/sdb2            7164        7473     2490075    5  Extended
/dev/sdb5            7164        7473     2490043+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x695fa75d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x617fe23a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 61.4 GB, 61471162368 bytes
255 heads, 63 sectors/track, 7473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x434bbe61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7163    57536766   83  Linux
/dev/sdb2            7164        7473     2490075    5  Extended
/dev/sdb5            7164        7473     2490043+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x695fa75d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38914   312568832    7  HPFS/NTFS
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc          proc         defaults                    0  0  
# Entry for /dev/sdb1 :
UUID=91b7dc2a-7c12-4a66-9fcb-6f5cc8d2e1fc  /              ext3         relatime,errors=remount-ro  0  1  
# Entry for /dev/sdb5 :
UUID=2f68117e-26bb-440c-8755-b66c8a3e2150  none           swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
# Entry for /dev/sda1 :
/dev/sda1                                  /media/sda     ext3         defaults                    0  2  
#entry for /dev/sdc1 :
/dev/sdc1        /media/sdc    ntfs    defaults    0 2

The results for cat /etc/fstab are:
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc          proc         defaults                    0  0  
# Entry for /dev/sdb1 :
UUID=91b7dc2a-7c12-4a66-9fcb-6f5cc8d2e1fc  /              ext3         relatime,errors=remount-ro  0  1  
# Entry for /dev/sdb5 :
UUID=2f68117e-26bb-440c-8755-b66c8a3e2150  none           swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
# Entry for /dev/sda1 :
/dev/sda1                                  /media/sda     ext3         defaults                    0  2  
#entry for /dev/sdc1 :
/dev/sdc1        /media/sdc    ntfs    defaults    0 2

The results for mount are:
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)/dev/sda1: LABEL="WD500G" UUID="28785647-0029-4ce0-84d7-926d0f47c03f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="2f68117e-26bb-440c-8755-b66c8a3e2150" 
/dev/sdb1: UUID="91b7dc2a-7c12-4a66-9fcb-6f5cc8d2e1fc" TYPE="ext3" 

varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /media/sda type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)

and the rersults for blkid are:
/dev/sda1: LABEL="WD500G" UUID="28785647-0029-4ce0-84d7-926d0f47c03f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="2f68117e-26bb-440c-8755-b66c8a3e2150" 
/dev/sdb1: UUID="91b7dc2a-7c12-4a66-9fcb-6f5cc8d2e1fc" TYPE="ext3"

---

### Post by DWL52 on 2009-10-16
Also, I've decided to stay with the NTFS file system for this external drive.

---

### Post by DWL52 on 2009-10-16
> **Rocket2DMn said:**
> Have you removed the fstab entry?  It's probably configured there to not allow you to write to access it, which is one reason to not have a fstab entry for external disks - it is better to let automount take care of it.  If you post the commands above, I can get a better idea of what is going on.
Did you reformat the drive with GParted, or are you still using the original filesystem the drive came with?


I removed the fstab entry and rebooted as you said, and everything works like a charm. Thanks for all the help. Consider this one solved.

---

