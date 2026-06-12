---
title: "Unable to mount My Drive"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by Unewbeginner on 2011-01-30
Hi everyone, I dropped my drive when I was copying my data. After that when I plug my hard drive again, I got the message below:
```

Unable to mount My Drive

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
```

I run the command below:

```
sudo fdisk -l
```

and got the message below:

```
Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003f448

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121598   976728064    7  HPFS/NTFS
```


Any Chance I could get it fixed in Ubuntu? Or it was physically damaged?

Thanks!

---

### Post by Unewbeginner on 2011-01-30
Some new message below:

```
Error mounting: mount exited with exit code 18: Failed to write lock '/dev/sdb1': Resource temporarily unavailable
Error opening '/dev/sdb1': Resource temporarily unavailable
Failed to mount '/dev/sdb1': Resource temporarily unavailable
```

I tried to run the command below:

```
sudo ntfsfix /dev/sdb1
```

and got this message: 

```

Mounting volume... Error opening partition device: Resource temporarily unavailable.
Failed to startup volume: Resource temporarily unavailable.
FAILED
Attempting to correct errors... Error opening partition device: Resource temporarily unavailable.
FAILED
Failed to startup volume: Resource temporarily unavailable.
Volume is corrupt. You should run chkdsk.

```



If anyone could help me fixed the drive, I really appreciate it!

---

### Post by Rab22 on 2011-01-30
I'm not very familiar with this error, but we can try a couple things.

What do you get for output from the following commands
```
mount
```
```
cat /etc/mtab
```

EDIT: adding one more command
```
 lsof | grep sdb1 
```

---

### Post by Unewbeginner on 2011-01-30
mount: 

```
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
/dev/sda7 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/client/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=client)
```

cat /etc/mtab

```
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda7 /home ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/client/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=client 0 0
```

 lsof | grep sdb1

no result.

---

### Post by Unewbeginner on 2011-01-30
some new info....

```
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

---

### Post by Rab22 on 2011-01-30
I would have imagined you'd have found something in one of those commands had the device been locked somewhere. 

That last error message doesn't look good at all. Do you have a windows computer around? I would follow the instructions listed above to try and recover anything I could. Outside of that, I'm not really sure.

Have you tried Google'n that new error message? Maybe someone else has ran into that error?

Sorry!

---

### Post by SneakySh0rty on 2011-02-03
I have the same problem and error msgs. I did not drop mine though. I know the hard drive was failing so i started to back up files. One day i tried to back up some more files and i got the boot volume Blue Screen of Death. 

I purchased a 1tb hdd and installed unbuntu 10.10. and majority of things are working fine in this OS (still learning some things)  I want to save 8 years worth of photos on my messed up hd. Ubuntu discovers the other hard drive and i got the first error. when entered  sudo ntfsfix /dev/sdb2 i got a different output:

christian@XPS:~$ sudo fdisk -l

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4       32098+  de  Dell Utility
/dev/sdb2   *           5       14589   117154012+   7  HPFS/NTFS

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00079d39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120837   970616832   83  Linux
/dev/sda2          120837      121602     6142977    5  Extended
/dev/sda5          120837      121602     6142976   82  Linux swap / Solaris
christian@XPS:~$ sudo ntfsfix /dev/sdb2
Mounting volume... pread: Input/output error
Failed to calculate number of free MFTs: Input/output error.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
pread: Input/output error
Failed to calculate number of free MFTs: Input/output error.
Remount failed: Input/output error.

thoughts?

OS on the messed up hdd is Windows XP Pro Sp2. I dont have any recovery disks for it either
-separate question, would any dell windows xp pro sp1 (or 3) recovery disk work? Or do i specifically have to get a sp2 disk? 

Computer(trying to bring back from the dead)
Dell XPS Gen 2

---

