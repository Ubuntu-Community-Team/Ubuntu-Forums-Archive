---
title: "Segmentation Fault when attempting to mount HD"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by FerretWithASpork on 2011-04-21
Hi all,

So my computer has 2 HDs in it. One of them has Win7 installed on it, the other was an old drive from an old comp, it had windows files on it because I was too lazy to format, and I just used it as extra space. The other day I finally decided to clean it out and deleted all the Windows files off it and removed the "bootable" flag from it.

Apparently it was doing more than I thought it was because after that I couldn't boot up at all. I formatted that drive and installed Ubuntu. Now I'm trying to mount the drive that was my main Win 7 drive but when I use "$ sudo mount /dev/sda1 /mnt" I get "Segmentation Fault" returned.

The strangest part, to me, is that in the Disk Manager Ubuntu recognizes it as being NTFS but for "Usage" it's not recognized as a File System, it's just blank. [[Picture]]("http://i.imgur.com/sBOLW.png")

Curiously I can mount the 8.4mb "New Volume" partition on the end of that drive.

Did I somehow corrupt the partition? Is there any way for me to mount this drive, or should I just format it and reinstall windows?

---

### Post by FerretWithASpork on 2011-04-21
Soo... I take it I should just reformat?

---

### Post by bhaverkamp on 2011-04-21
Looks like the boot partition was on the second disk. Need to see if there is anything recoverable on the first drive.

post the output of :
sudo fdisk -l
mount

---

### Post by FerretWithASpork on 2011-04-21
```

ferretwithaspork@JD-LinDesktop:~$ sudo fdisk -l
[sudo] password for ferretwithaspork: 

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b869b86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36480   293025568    7  HPFS/NTFS
/dev/sda2           36481       36482        8192    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x466b466b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156279809    5  Extended
/dev/sdb2           19457       19458        8192    7  HPFS/NTFS
/dev/sdb5           18959       19457     3999744   82  Linux swap / Solaris
/dev/sdb6               1       18958   152279040   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 2013 MB, 2013265920 bytes
129 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         949     1957872    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(956, 128, 32) logical=(948, 75, 32)

```

```
ferretwithaspork@JD-LinDesktop:~$ mount
/dev/sdb6 on / type ext4 (rw,errors=remount-ro,commit=0)
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
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ferretwithaspork/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ferretwithaspork)
/dev/sdc1 on /media/KPKV16 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```

/dev/sda1 is the partition I'm trying to access.

---

### Post by FerretWithASpork on 2011-04-21
bump

---

### Post by FerretWithASpork on 2011-04-22
uhh bump?

---

### Post by FerretWithASpork on 2011-04-22
sooo.... bump

---

### Post by ohadcn on 2011-04-22
have you tried to access the HD from a live-cd?
did you tried to configure the bios loading win7 drive?

---

### Post by FerretWithASpork on 2011-04-22
I did try from a live CD, It still won't mount, but it doesn't give a segmentation fault. There are no errors it just doesn't mount the drive.

As for the bios I don't know what to change in there. I changed the boot order for the hard-drive so it's booting from the main drive (the sda/1 one that I can't access) and that's where I had Ubuntu install GRUB too as well, but it still won't start Win7.

---

