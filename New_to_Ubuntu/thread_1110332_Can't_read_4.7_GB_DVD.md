---
title: "Can't read 4.7 GB DVD"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by all-beans on 2009-03-29
Hi,

I created several ISO image files with the following command:

```
mkisofs -r -o ~/iso_images/disk1.iso /mnt/data/2009-03-22_17-17/venus000.tar.gz /mnt/data/2009-03-22_17-17/venus001.tar.gz /mnt/data/2009-03-22_17-17/venus002.tar.gz /mnt/data/2009-03-22_17-17/venus003.tar.gz
```

And burnt DVDs of these image files with the following command:

```
growisofs -dvd-compat -Z /dev/dvd=disk1.iso -speed=8
```

The above worked fine since I can read these DVDs with no problems on XP

I cannot read these DVDs with Ubuntu 8.10 desktop. I get the following error when trying to copy the file from one of these DVDs:

```
user@machine:~/backuptest$ cp /cdrom/*.* .
cp: reading `/cdrom/venus001.tar.gz': Input/output error
cp: reading `/cdrom/venus002.tar.gz': Input/output error
cp: reading `/cdrom/venus003.tar.gz': Input/output error
user@machine:~/backuptest$
```

I ```
ls -al
``` the destination folder and get:
```
user@machine:~/backuptest$ ls -al
total 1049560
drwxr-xr-x  2 user user       4096 2009-03-29 15:48 .
drwxr-xr-x 59 user user       4096 2009-03-29 14:31 ..
-r--r--r--  1 user user 1073688576 2009-03-29 15:48 venus000.tar.gz
-r--r--r--  1 user user          0 2009-03-29 15:48 venus001.tar.gz
-r--r--r--  1 user user          0 2009-03-29 15:48 venus002.tar.gz
-r--r--r--  1 user user          0 2009-03-29 15:48 venus003.tar.gz
user@machine:~/backuptest$
```

As you can see the first filed almost entirely copied. Each file should be 1174999040. Here's the tail of dmesg:

```
[11162.607417] UDF-fs: No VRS found
[11162.614550] ISO 9660 Extensions: RRIP_1991A
[11420.297996] attempt to access beyond end of device
[11420.298007] sr0: rw=0, want=2097152, limit=2097151
[11420.298011] __ratelimit: 84 callbacks suppressed
[11420.298014] Buffer I/O error on device sr0, logical block 524287
[11420.300253] attempt to access beyond end of device
[11420.300261] sr0: rw=0, want=2097156, limit=2097151
```

Also note I am running VMWARE server 1.08 with a XP guest on this machine. The XP guest is using the same DVD ROM as Intrepid and reads the full DVD no problems. The above XP machine is an older HP Pavillion, so that's 2 XP machines that can read the DVDs. I thought to point this out since I have read other postings blame this on bad DVDs, bad readers, bad burning or burners. Not so. it's got to be the Ubuntu 8.10 software that reads DVDs. (driver/kernel etc...) As a matter of fact DVDs using the same ISO images burnt with NERO on XP won't read on Ubuntu 8.10. 

I can only conclude that the problem is with Intrepid. 

Anyone any ideas?

---

