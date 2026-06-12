---
title: "connect android with jmtpfs"
date: 2019-11-26
forum: Networking &amp; Wireless
---

### Post by jduns on 2019-11-26
I need to get my android device as mass storage, so that I can use posixovl, so that I can add symlinks(-like) to my android device.
Now I am trying with jmtpfs:
1. I added in fstab this line
    ```
jmtpfs /media/duns/likebook fuse nodev,allow_other,rw,user,noauto,noatime,uid=1000,gid=1000    0    0
```
2. then I tried to mount my device, both with sudo:
    ```
sudo jmtpfs -o allow_other /media/duns/likebook
```
or without sudo
```
jmtpfs -o allow_other /media/duns/likebook
```

But I get this error message
```
Device 0 (VID=2207 and PID=0011) is a Various Viewpia DR/bq Kepler Debugging.
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP PANIC: failed to open session on second attempt
terminate called after throwing an instance of 'MtpErrorCantOpenDevice'
  what():  Can't open device
Aborted
```

---

### Post by ajgreeny on 2019-11-26
On my Android phone I have to go into the phone's settings -> Connected devices -> USB and there choose to use the phone as a mass storage device, at which point it is like any other USB flash drive. The computer setting does not seem to make any difference, it's all to do with phone settings.

This may, of course, be different with different phones, but it may help you as a start in your investigation

---

### Post by jduns on 2019-11-26
Thank you. In effect, with the smartphone it works, but with another device, Likebook (an e-ink ebook reader with Android 6) it doesn't.

EDIT
No, now it **works**! :D

---

### Post by jduns on 2019-11-26
I thought it was resolved, but two problems remain
1) **not always** the connection **works** (both for the smartphone and the android ereader), with the same messages as above;
2) the sync (with Krusader syncronization) **freezes**

---

### Post by jduns on 2019-11-26
For the first problem (1) I noticed that I have to **unplug** and (re)plug the device.
For the second (2) I supppose that the problem is the grafical app (Krusader, Dolphin) so now I'm trying with a rsync script. But so far I get an error with symlinks, even though I'm using posixovl. Tomorrow I will re-try.
Thank you

EDIT
Nothing to do: even with a script it **freezes** (after some files syncronized: it begins, but not ends).

EDIT
sync had lasted more than 8 hours: I interrupted it!

---

### Post by jduns on 2019-12-09
My workaround now is to use a sd-card (with posixovl to keep the symlinks between different PC connected with the likebook).

---

