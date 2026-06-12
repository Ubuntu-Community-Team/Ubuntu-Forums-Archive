---
title: "updates"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by spiky001 on 2009-10-01
hi hav installed 9.04 all ok but i hav trouble downloading updates (154 megs) i hav os on a 40 gig paryion so how is this possible:(

---

### Post by LewRockwell on 2009-10-01
check to see that your installation created a large enough partition size

update: as per posts below...yep, you're partitioning didn't go quite correctly...

.

---

### Post by nhasian on 2009-10-01
please give us the output of these terminal commands:
```

sudo fdisk -l
```
```

df -h
```

when replying, please make sure to use the CODE tags for the terminal output to make it easier to read.  

for example, mine says:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              20G  5.3G   14G  29% /
udev                 1005M  316K 1005M   1% /dev
none                 1005M  1.9M 1003M   1% /dev/shm
none                 1005M  332K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sdb1             111G   29G   76G  28% /data
/dev/sda3              80G   23G   53G  31% /home

```

thanks!

---

### Post by spiky001 on 2009-10-01
hi got those details

  	 	 	 	 	 	  Disk /dev/sda: 100.0 GB, 100030242816 bytes 
 255 heads, 63 sectors/track, 12161 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0x414d8374 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1        5099    40957686    7  HPFS/NTFS 
 /dev/sda2            5100       12160    56717482+   f  W95 Ext'd (LBA) 
 /dev/sda5            5100        9872    38339091    7  HPFS/NTFS 
 /dev/sda6           10199       12160    15759733+   7  HPFS/NTFS 
 /dev/sda7            9873       10176     2441848+  83  Linux 
 /dev/sda8           10177       10198      176683+  82  Linux swap / Solaris 
  
 Partition table entries are not in disk order 
 

   	 	 	 	 	 	  Filesystem            Size  Used Avail Use% Mounted on 
 /dev/sda7             2.3G  2.2G   43M  99% / 
 tmpfs                 751M     0  751M   0% /lib/init/rw 
 varrun                751M   92K  750M   1% /var/run 
 varlock               751M     0  751M   0% /var/lock 
 udev                  751M  152K  750M   1% /dev 
 tmpfs                 751M  488K  750M   1% /dev/shm 
 lrm                   751M  2.4M  748M   1% /lib/modules/2.6.28-11-generic/volatile 



hope u can help me

---

### Post by spiky001 on 2009-10-01
can any 1 help with the above problem plz

---

### Post by snowpine on 2009-10-01
Your Ubuntu partition (/dev/sda7) is only 2.3gb, which is much too small. This is a bug in the installer, so it's not your fault. :) What you need to do is reboot with the Ubuntu Live CD, and use the Gparted partition editor to shrink one of the adjacent partitions and grow your Ubuntu partition (/dev/sda7). I recommend 10gb minimum if you can spare it. Good luck!

---

### Post by LewRockwell on 2009-10-01
> **spiky001 said:**
> can any 1 help with the above problem plz

yes, read this:

[http://ubuntuforums.org/showthread.php?t=1275296](http://ubuntuforums.org/showthread.php?t=1275296)

.

---

