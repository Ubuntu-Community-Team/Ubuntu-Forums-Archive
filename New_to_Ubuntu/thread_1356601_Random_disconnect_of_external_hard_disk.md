---
title: "Random disconnect of external hard disk"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by dagarshali on 2009-12-16
Hi, 
I recently upgraded to 64bit ubuntu karmic koala.. The external drive that I mount via USB, randomly unmounts and I get this input/output error. And when I connect the the harddisk, in the past, just one window opened showing the contents. Now, it opens like 3 or 4 windows.

Is there any way to fix this as it is very important that I have this external hard disk running of this system

Regards,
vishwa

---

### Post by ukripper on 2009-12-16
reconnect your drive and post output of these commands in terminal:
```
dmesg | tail
```

```
sudo mount
```

```
sudo fdisk -l
```

---

### Post by dagarshali on 2009-12-16
**dmesg |tail**
[69264.312780] scsi 16:0:0:0: Direct-Access     FANTOM   WD10EAVS-00D7B1  2.10 PQ: 0 ANSI: 4
[69264.313742] sd 16:0:0:0: Attached scsi generic sg2 type 0
[69264.314625] sd 16:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[69264.315509] sd 16:0:0:0: [sdb] Write Protect is off
[69264.315517] sd 16:0:0:0: [sdb] Mode Sense: 21 00 00 00
[69264.315522] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[69264.320492] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[69264.320507]  sdb: sdb1
[69264.336519] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[69264.336529] sd 16:0:0:0: [sdb] Attached SCSI disk

**sudo mount**
[sudo] password for dagarshali: 
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda3 on /media/DATA type ext4 (rw)
/dev/sda7 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dagarshali/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dagarshali)
/dev/sdb1 on /media/0FFD-432F type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
**sudo fdisk -l**

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e0eee9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19559   157099176    7  HPFS/NTFS
/dev/sda2           21941       33002    88855515    f  W95 Ext'd (LBA)
/dev/sda3           33003       38913    47480107+  83  Linux
/dev/sda5           21941       22462     4192933+  82  Linux swap / Solaris
/dev/sda6           22463       25073    20972826   83  Linux
/dev/sda7           25074       33002    63689661   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000098ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)

---

