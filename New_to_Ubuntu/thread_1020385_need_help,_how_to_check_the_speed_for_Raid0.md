---
title: "need help, how to check the speed for Raid0"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Gigcsjcx on 2008-12-24
**[COLOR="Red"]simple Hardisk before setup the Raid0[/COLOR]**

linux@ubuntu:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
Timing cached reads: 1904 MB in 2.00 seconds = 952.09 MB/sec
Timing buffered disk reads: 226 MB in 3.00 seconds = 75.27 MB/sec
linux@ubuntu:~$

[COLOR="Red"]**after Setup the Raid0**[/COLOR]

/dev/md2:
Timing cached reads: 1916 MB in 2.00 seconds = 958.23 MB/sec
Timing buffered disk reads: 36 MB in 30.45 seconds = 1.18 MB/sec

**[COLOR="Red"]Only 1.18 MB/sec[/COLOR], Why? is it correct or anything wrong with my RAID0?**

---

### Post by Gigcsjcx on 2008-12-24
anyone gives me some idea?

---

### Post by Gigcsjcx on 2008-12-24
no reply!

---

### Post by cariboo on 2008-12-24
I think it depends on whether you are using hardware or software raid. I am using Raid1 on my server, and here are my results.

```
sudo hdparm -tT /dev/mapper/nvidia_ifdejefh1

/dev/mapper/nvidia_ifdejefh1:
 Timing cached reads:   994 MB in  2.00 seconds = 496.21 MB/sec
 Timing buffered disk reads:  212 MB in  3.02 seconds =  70.11 MB/sec
jim@willy:~$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   1004 MB in  2.00 seconds = 501.87 MB/sec
 Timing buffered disk reads:  216 MB in  3.00 seconds =  71.92 MB/sec
jim@willy:~$ sudo hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   1008 MB in  2.00 seconds = 503.21 MB/sec
 Timing buffered disk reads:  222 MB in  3.01 seconds =  73.77 MB/sec
```

Jim

---

### Post by Gigcsjcx on 2008-12-27
> **cariboo907 said:**
> I think it depends on whether you are using hardware or software raid. I am using Raid1 on my server, and here are my results.

```
sudo hdparm -tT /dev/mapper/nvidia_ifdejefh1

/dev/mapper/nvidia_ifdejefh1:
 Timing cached reads:   994 MB in  2.00 seconds = 496.21 MB/sec
 Timing buffered disk reads:  212 MB in  3.02 seconds =  70.11 MB/sec
jim@willy:~$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   1004 MB in  2.00 seconds = 501.87 MB/sec
 Timing buffered disk reads:  216 MB in  3.00 seconds =  71.92 MB/sec
jim@willy:~$ sudo hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   1008 MB in  2.00 seconds = 503.21 MB/sec
 Timing buffered disk reads:  222 MB in  3.01 seconds =  73.77 MB/sec
```

Jim

I reinstalled my sys with Ubuntu 8.10 and glad to find that my adaptec SCSI raid card is supported by it and then Raid0 setted up and installed smoothly.

---

