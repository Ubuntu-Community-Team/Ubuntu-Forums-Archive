---
title: "explanation of my hard drive"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by abble455 on 2010-08-01
I recently installed 10.04 on my lenovo thinkpad sl400 choosing to wipe the hard drive of windows and not install ubuntu on a partition.  So, I'm not having a problem but I'm wondering what these "other" partitions are (see below)?

I typed
```
sudo fdisk -l
```

and got

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00015019

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris
```

Can someone explain to me what this output means, specifically what /dev/sda2 & /dev/sda5 are?  Thanks in advance!

BTW - yes i'm a complete newb.

---

### Post by llamabr on 2010-08-01
The best answer is: they're supposed to be there, and don't mess with them.  Further, until you know what they're there for, you don't really need to know what they're there for.  

You can also post the output of:

```
df -h
```

if you want, and we can tell you exactly where those partitions are mounted.  But in the mean time, I wouldn't worry overmuch.

---

### Post by snowpine on 2010-08-01
/dev/sda1 is your Linux install
/dev/sda2 is an extended partition that holds /dev/sda5
/dev/sda5 is a logical swap partition (similar to virtual memory in windows)

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by abble455 on 2010-08-01
Thanks for the explanations

here's the output from 
```
df -h
```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             141G   50G   84G  38% /
none                  1.5G  340K  1.5G   1% /dev
none                  1.5G  880K  1.5G   1% /dev/shm
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
```

---

