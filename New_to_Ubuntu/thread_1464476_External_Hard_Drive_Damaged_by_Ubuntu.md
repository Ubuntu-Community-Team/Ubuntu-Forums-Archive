---
title: "External Hard Drive Damaged by Ubuntu?"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by dave2001 on 2010-04-28
I have an issue with my external hard drive. I'm running xubuntu 8.04 on my thinkpad a20m laptop, and I have a 250GB WD external hard drive. After some work, I've managed to get things configured correctly so the drive mounts and unmounts properly. However, the "eject" function, either at command line or from context menu, does not function correctly. The file system is unmounted, but the drive is not powered down in any sense, the heads do not "park," and the drive icon reappears immediately on my desktop. Is it possible that this will damage the drive? I have seen reference to this kind of issue on launchpad, but no good solution. I am new to ubuntu, knowing only some basic commands, so if there is any diagnostic info I can provide, please let me know.

---

### Post by mikewhatever on 2010-04-28
Well, you forgot to link to the launchpad references, which makes it hard to comment. Other then that, why and by what should a spinning drive get damaged? After all, that's what it's built to do. Generally speaking, the drive should go to sleep after some time of inactivity, regardless of whether mounted or not. You can also use *hdparm -S* to put in standby manually (heads parked), or *hdparm -Y* to put it to sleep.

```
sudo hdparm -S 1 /dev/sdX
sudo hdparm -Y /dev/sdX
```

---

### Post by dave2001 on 2010-04-28
[QUOTE=mikewhatever] "Other then that, why and by what should a spinning drive get damaged"

This was part of my question, can disconnecting a drive while it is spinning, and the heads unparked, damage it or reduce it's lifespan? It seems like the "eject" function would not exist if yanking out the usb cable any 'ol time was fine.

Thanks for the command suggestions, I'll give 'em a try.

---

### Post by tica vun on 2010-04-28
Disconnecting a storage device (be it an external HDD, optical drive or flash memory) may revert any changes you've made to the files on it, or even cause data loss, but there's no way it can damage a hard drive.

---

### Post by dave2001 on 2010-04-28
I tried both hdparm commands, got error with each. Here's my terminal output

ubuntastic@Thinkpad-A20m:~$ sudo hdparm -S 1 /dev/sdb

/dev/sdb:
 setting standby to 1 (5 seconds)
SG_IO: bad/missing ATA_16 sense data::  f0 00 05 00 00 00 00 10 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD(setidle1) failed: Input/output error

---

### Post by dave2001 on 2010-04-28
Ok, good to know. Thanks Tica Vun. BTW, love your sig, gave me a chuckle.

---

### Post by ubunterooster on 2010-04-28
That (eject) does not cut power as I know. That makes it good for, say, charging a ipod

---

