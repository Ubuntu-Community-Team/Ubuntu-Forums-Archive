---
title: "External Herd Drive"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by fknyeah on 2009-02-10
How can I gain permissions on the files on my External HDD?
For some reason it won't let me edit any of my own files.

---

### Post by JK3mp on 2009-02-10
Can you copy them? Did you mount the device properly. Try mountinig it manually in the terminal.
```
mount -t vfat -o umask=000 /blah/blahdrivepath
```.

---

### Post by fknyeah on 2009-02-10
it mounts, but won't let me delete empty folders, edit metadata of music, etc.  It's like its read only.

---

### Post by taurus on 2009-02-10
Is it ntfs or fat32 filesystem?  Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by fknyeah on 2009-02-10
it is ntfs.

sam@honus-wagner:~$ sudo fdisk -l
[sudo] password for sam: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris


sam@honus-wagner:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G   68G   70G  50% /
tmpfs                 504M     0  504M   0% /lib/init/rw
varrun                504M  232K  504M   1% /var/run
varlock               504M     0  504M   0% /var/lock
udev                  504M  2.8M  502M   1% /dev
tmpfs                 504M  324K  504M   1% /dev/shm
lrm                   504M  2.0M  503M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             466G  232G  235G  50% /media/disk

---

### Post by Neural oD on 2009-02-10
just check the permission - maybe you'll have to run chmod on those files

---

### Post by fknyeah on 2009-02-10
it says the permissions of the disk could not be determined

---

### Post by taurus on 2009-02-10
Try

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```
Your external drive is now mounted to /media/sdb1.

---

### Post by fknyeah on 2009-02-10
sam@honus-wagner:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
Error reading bootsector: Input/output error
Failed to sync device /dev/sdb1: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

---

### Post by Neural oD on 2009-02-10
> **fknyeah said:**
> sam@honus-wagner:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
Error reading bootsector: Input/output error
Failed to sync device /dev/sdb1: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

Google testdisk - it might be that your boot sector on the ntfs partition is corrupt- testdisk will help u recover it!

---

### Post by taurus on 2009-02-10
> **Neural oD said:**
> Google testdisk - it might be that your boot sector on the ntfs partition is corrupt- testdisk will help u recover it!

Here's the TestDisk if you want to take a look at it.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by JK3mp on 2009-02-10
TestDisk is ur best bet. Let us know if it works.

---

### Post by fknyeah on 2009-02-10
I'm so confused about how to use it.  can you help?

---

### Post by nathan28 on 2009-02-10
I'm going through something similar with an NTFS drive, but am afraid to run anything on the disk prior to backing it up since i've fried an HFS+ external disk messing around before. There's some help here:

[http://ubuntuforums.org/showthread.php?t=1062545&highlight=iomega](http://ubuntuforums.org/showthread.php?t=1062545&highlight=iomega)

---

### Post by fknyeah on 2009-02-12
What ever testdisk did seems to have worked. if i have anymore problems i'll give a holler

Thanks for all the help!
SFK

---

