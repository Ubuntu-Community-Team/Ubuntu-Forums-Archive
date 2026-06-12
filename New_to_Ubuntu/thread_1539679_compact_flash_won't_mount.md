---
title: "compact flash won't mount"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by trikster_x on 2010-07-26
I have a 4 GB compactflash card connected to my computer using a USB card reader.  When I try to open the directory it shows it mounted under, nothing happens.  When I run fdisk and gparted, the device doesn't show up.  When I try to safely remove drive I get the errors:

> Error detaching: helper exited with exit code 1: sense buffer empty
Error SYNCHRONIZE CACHE for /dev/sdb: Success
sense buffer empty
Error STOP UNIT for /dev/sdb: No such file or directory


This is what I get when I run mount:

```
amanda@triksterx-laptop:~$ sudo mount dev/sdb1 /home/amanda/cflashcard
mount: special device dev/sdb1 does not exist
```

The card mounts and is readable in windows, but I don't want to have to reboot just to put pictures on my computer.  Any help with this problem will be greatly appreciated.

Using ubuntu 9.10

---

### Post by sandyd on 2010-07-26
> **trikster_x said:**
> I have a 4 GB compactflash card connected to my computer using a USB card reader.  When I try to open the directory it shows it mounted under, nothing happens.  When I run fdisk and gparted, the device doesn't show up.  When I try to safely remove drive I get the errors:



This is what I get when I run mount:

```
amanda@triksterx-laptop:~$ sudo mount dev/sdb1 /home/amanda/cflashcard
mount: special device dev/sdb1 does not exist
```

The card mounts and is readable in windows, but I don't want to have to reboot just to put pictures on my computer.  Any help with this problem will be greatly appreciated.

Using ubuntu 9.10

your missing a slash in front of the dev

---

### Post by trikster_x on 2010-07-26
Figured it out.  There was a piece of debris in the reader preventing the card from pushing in all the way.  Sorry for wasting anyone's time.

---

