---
title: "Slow copy speeds"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by neurostu on 2009-09-30
does anybody know how I would go about diagnosing slow copy speeds? I have two sata drives and when I try to copy big files >500mb from one drive to another I get really slow copy speeds like 5mb/sec

---

### Post by cariboo on 2009-09-30
Use hdparm to check the transfer speeds of your hard drives. Open a terminal and type:

```
sudo hdparm -tT /dev/sdX
```

where X is your drive. THe results should look something like this:

```
/dev/sda:
 Timing cached reads:   1628 MB in  2.00 seconds = 813.96 MB/sec
 Timing buffered disk reads:  170 MB in  3.02 seconds =  56.24 MB/sec
```

The results above are for my 3 year old system. In my case PATA is faster then SATA.

```
/dev/sdb:
 Timing cached reads:   1616 MB in  2.00 seconds = 808.34 MB/sec
 Timing buffered disk reads:  232 MB in  3.01 seconds =  77.07 MB/sec
```

---

### Post by Sir Jasper on 2009-10-01
Hi,

Thanks[COLOR="Blue"] cariboo907[/COLOR], your  reply was interesting but as it seems to relate to read speeds is there also a built-in way to also test write speeds on internal and external drives (including flash drives)?

My regards

---

### Post by neurostu on 2009-10-01
Another clue is that the problem is intermitent. Sometimes I copy at full speed other times however I get the horridly slow speed.

---

### Post by XCan on 2009-10-02
Is there by any chance a dependence on the filesystems? Copying from/to NTFS isn't the fastest I suspect.

---

### Post by neurostu on 2009-10-03
Both filesystems are EXT3

---

### Post by neurostu on 2009-10-03
> **cariboo907 said:**
> Use hdparm to check the transfer speeds of your hard drives. Open a terminal and type:

```
sudo hdparm -tT /dev/sdX
```

where X is your drive. THe results should look something like this:

```
/dev/sda:
 Timing cached reads:   1628 MB in  2.00 seconds = 813.96 MB/sec
 Timing buffered disk reads:  170 MB in  3.02 seconds =  56.24 MB/sec
```

The results above are for my 3 year old system. In my case PATA is faster then SATA.

```
/dev/sdb:
 Timing cached reads:   1616 MB in  2.00 seconds = 808.34 MB/sec
 Timing buffered disk reads:  232 MB in  3.01 seconds =  77.07 MB/sec
```

I tried this and got fast speeds. Much faster than the 1.2 - 4 MB/sec that I get about 50% of the time.

---

### Post by Vaphell on 2009-10-03
i confirm having similar issues on my 8.04 box with 2 satas. I can't say i ever seen transfer faster than 10MB/s, average is more close to 5-7. ntfs/ext3 thing is negligible.
I read some threads and tried to pin the problem down, but no dice.
In syntetic benchmarks of hdparm i get 800MB/70MB for both drives.

you can read more about the low speed issue here
[http://ubuntuforums.org/showthread.php?t=1150108](http://ubuntuforums.org/showthread.php?t=1150108)

---

