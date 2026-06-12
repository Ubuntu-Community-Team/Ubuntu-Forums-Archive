---
title: "Ubuntu 8.10 crashes while tarring filesystem"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by mistypotato on 2010-10-08
Is it abnormal for ubuntu to crash (hard crash, screen lockup with distortion) during a cron job file system backup via TAR ?

There is PLENTY of free space on the drive  13GB used, 57GB free

It crashes every time I run the file system TAR cron job after about 20%

---

### Post by da burger on 2010-10-08
Have you tried running the tar command from the command line without using cron? Is it successful? Does it give any errors?
Angus

---

### Post by silverglade00 on 2010-10-08
Also, are you trying to tar up the folder where you are saving the tar file?

---

### Post by mistypotato on 2010-10-08
> **da burger said:**
> Have you tried running the tar command from the command line without using cron? Is it successful? Does it give any errors?
Angus

I'll try that.

thx

---

### Post by mistypotato on 2010-10-08
> **silverglade00 said:**
> Also, are you trying to tar up the folder where you are saving the tar file?

No, I'm creating the TAR file on a USB drive

---

### Post by da burger on 2010-10-09
Wait are you trying to tar /? If you are make sure you exclude the folder where the usb drive is mounted. Else the tar will try and tar itself!

---

### Post by mistypotato on 2010-10-13
Well,

I made sure it's NOT backing up the destination folder and it still crashes.

This time it crashed while backing up a file located on the desktop.


When it crashes...the screen display ALWAYS gets distorted...which I feel is a clue.

---

