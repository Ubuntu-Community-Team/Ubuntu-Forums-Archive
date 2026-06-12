---
title: "Filesystem Mounting Error"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-01-13
When ever i Boot into my system i get the error that filesystem can not be mounted after three or four reboot it is going inside! pls help. I am using mount manager to auto mount my partitions at system start up.

---

### Post by nemilar on 2011-01-13
Looks like it could be a hardware problem.  Try firing up a rescue CD and running a diagnostic.  I know some of the more popular hard disk makers have liveCDs that you can download and boot from to run a diagnostic, or you could just try using Linux.

---

### Post by woodmaster on 2011-01-13
I'm on a mobile, can't read your screensot ut it may e a UUId issue like we had erk
[http://ubuntuforums.org/showthread.php?t=1399810]("http://ubuntuforums.org/showthread.php?t=1399810")

---

### Post by woodmaster on 2011-01-13
I'm on a mobile, can't read your screensot ut it may e a UUId issue like we had erk
[URL=""]

---

### Post by woodmaster on 2011-01-13
I'm on a mobile, can't read your screensot ut it may e a UUId issue like we had erk
[http://ubuntuforums.org/showthread.php?t=1399810]("http://ubuntuforums.org/showthread.php?t=1399810")

---

### Post by vanadium on 2011-01-13
It indeed might be a UUID issue considering you used mount manager. If you manage to get into the system, run following commands and post the output here. This will possibly allow to troubleshoot and solve the issue.
```

sudo fdisk -l
sudo blkid
cat /etc/fstab
mount
sudo mount -a

```

---

### Post by 1991sudarshan on 2011-01-15
> **nemilar said:**
> Looks like it could be a hardware problem.  Try firing up a rescue CD and running a diagnostic.  I know some of the more popular hard disk makers have liveCDs that you can download and boot from to run a diagnostic, or you could just try using Linux.

Could you pls explain me little more i.e how to run diagnostics!!

---

### Post by 1991sudarshan on 2011-01-18
> **vanadium said:**
> It indeed might be a UUID issue considering you used mount manager. If you manage to get into the system, run following commands and post the output here. This will possibly allow to troubleshoot and solve the issue.
```

sudo fdisk -l
sudo blkid
cat /etc/fstab
mount
sudo mount -a

```
 
i got this when i entered those commands


[HTML][HTML]kevin@kevin-desktop:~$ sudo fdisk -l
[sudo] password for kevin: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe426e426

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2256    18121288+   7  HPFS/NTFS
/dev/sda2            2257       21185   152047100    f  W95 Ext'd (LBA)
/dev/sda3           21187       30400    74011455    7  HPFS/NTFS
/dev/sda5            2257        5100    22844336+  83  Linux
/dev/sda6            5101       12750    61448593+   7  HPFS/NTFS
/dev/sda7           12751       18800    48596593+   7  HPFS/NTFS
/dev/sda8           18801       21185    19157481    7  HPFS/NTFS

Disk /dev/sdb: 1981 MB, 1981808640 bytes
61 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 3782 * 512 = 1936384 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     1934462    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(1023, 60, 62) logical=(1022, 60, 62)

kevin@kevin-desktop:~$ sudo blkid
/dev/sda1: UUID="98EC1FDDEC1FB50A" TYPE="ntfs" 
/dev/sda3: UUID="C4ECBF75ECBF5FFA" TYPE="ntfs" 
/dev/sda5: UUID="287fbd4d-409f-4919-ae02-003c5592f0fd" TYPE="ext4" 
/dev/sda6: LABEL="MINE" UUID="78A0AAFCA0AAC04C" TYPE="ntfs" 
/dev/sda7: UUID="118ABCE91B5647ED" TYPE="ntfs" 
/dev/sda8: UUID="A8F413FDF413CC86" TYPE="ntfs" 
/dev/sdb1: UUID="D422-6F6E" TYPE="vfat"

kevin@kevin-desktop:~$ cat /etc/fstab
UUID=98EC1FDDEC1FB50A /sda1 ntfs-3g defaults 0 0
UUID=287fbd4d-409f-4919-ae02-003c5592f0fd / ext4 defaults 0 0
UUID=C4ECBF75ECBF5FFA /sda3 ntfs-3g users 0 0
UUID=78A0AAFCA0AAC04C /sda6 ntfs-3g defaults 0 0
UUID=118ABCE91B5647ED /sda7 ntfs-3g defaults 0 0
UUID=A8F413FDF413CC86 /sda8 ntfs-3g defaults 0 0

kevin@kevin-desktop:~$ mount
/dev/sda5 on / type ext4 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda6 on /sda6 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /sda7 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8 on /sda8 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /sda3 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
[/HTML][/HTML]

---

### Post by vanadium on 2011-01-18
Your output looks fine and normal. You are having the problem with sda5, which is your root partition. To me, this does not seem to be caused by a configuration problem. It might be a hardware issue, at the level of your disk or hard disk controller. Perhaps you might be able to check the connections inside the system, but other than that, there is nothing I can suggest, though, other than having good backups of your data. At one day, the disk access might break completely.

---

### Post by matt_symes on 2011-01-18
Hi

Check the drives SMART status using the disk utility. This should show if your drive is failing.

You might try running fsck to check the drive.

Kind regards

---

