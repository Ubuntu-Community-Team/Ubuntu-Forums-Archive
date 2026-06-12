---
title: "Different partition sizes reported by df and parted"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by roncville on 2010-09-15
I'm not understanding why the sda4 size shows up drastically differently in the 'df' and 'parted' reports below (df=4.7GB, parted=210GB).  The system does in fact run out of disk space according to the df number.  It's been awhile since I installed this, so I don't recall what partition size I initially set.

Is there a simple explanation?  And yes - I did search this forum a couple of years back and didn't find an answer.

----- kernel level
rwo@miniITX:~$ uname -a
Linux miniITX 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 i686 GNU/Linux

----- df output
rwo@miniITX:~$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda4     ext3    4.7G  1.2G  3.3G  27% /
tmpfs        tmpfs    469M     0  469M   0% /lib/init/rw
varrun       tmpfs    469M  304K  469M   1% /var/run
varlock      tmpfs    469M     0  469M   0% /var/lock
udev         tmpfs    469M  148K  469M   1% /dev
tmpfs        tmpfs    469M     0  469M   0% /dev/shm
lrm          tmpfs    469M  2.4M  467M   1% /lib/modules/2.6.28-11-server/volatile
/dev/sda3     ext3     19G   14G  4.1G  77% /mnt/shareron2

----- parted output
rwo@miniITX:~$ sudo parted
[sudo] password for rwo: 
GNU Parted 1.8.8
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA WDC WD5000AACS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  10.0GB  10.0GB  primary  ext3         boot 
 2      10.0GB  20.0GB  10.0GB  primary  ext3              
 3      20.0GB  40.0GB  20.0GB  primary  ext3              
 4      40.0GB  250GB   210GB   primary  ext3

----- mount output
rwo@miniITX:~$ mount
/dev/sda4 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-server/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /mnt/shareron2 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by TeoBigusGeekus on 2010-09-15
/dev/sda is your whole hd and it is 500gb.
/dev/sda4 is the 4rth partition on that drive, sized to 4.7gb and used as your / (root) partition.

---

### Post by roncville on 2010-09-16
It turns out that a file system can be smaller than the partition in which it resides - that was news to me.  I don't know if this should be the case, or if it resulted from a bug in the installer or some utility I ran along the way.

Anyway, I booted with a Ubuntu live CD, ran gparted, and had it do a 'check' on my sda4 partition (the one with the size mismatch).  It complained that the file system was smaller than the partition, and offered to grow it to partition size.  I accepted the offer and now the file system is large like the partition.

Here's a posting from another forum, that put me on to the solution
   [http://linux.derkeiler.com/Mailing-Lists/Fedora/2009-04/msg01901.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2009-04/msg01901.html)

---

