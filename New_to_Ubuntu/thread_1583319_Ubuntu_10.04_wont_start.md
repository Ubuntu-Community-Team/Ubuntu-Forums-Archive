---
title: "Ubuntu 10.04 wont start"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by elDux on 2010-09-27
Hello

I'm posting this from a different computers because I recently upgraded to Ubuntu 10.04 on my Dell Inspiron 1501 laptop and now it doesn't work. everything was fine until last week when i turned it on and all i got was a black screen with a bunch words that i imagine are commands. I no nothing about computers so i have no idea what's going on. It never gets to the sign in screen or the desktop. I took a picture of the screen it shows me and attached it to this post, if that helps any.

If anyone could help that would be great.

Thanks

---

### Post by andrewthomas on 2010-09-27
Do you have an Ubuntu liveCD?

---

### Post by elDux on 2010-09-27
Yes, but of a previous version of Ubuntu, on a burned disc.

---

### Post by andrewthomas on 2010-09-27
That is fine, as long as it is at least 9.10.  Reinstall grub2 with these instructions.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by elDux on 2010-09-27
[COLOR=Red][COLOR=Black]Thanks, how do i know what I'm supposed to enter my value as. I don't know the correct drive/partition or even what that refers to. [/COLOR]
[B]

"Important:[/B][/COLOR] All instances of **[COLOR=DarkRed]sdX[/COLOR]** and **[COLOR=DarkRed]sdXY[/COLOR]** must be replaced with the correct drive/partition for your system. (sda, sdb, sda1, sda5, sdb5, etc). **[COLOR=DarkRed]X[/COLOR]** is the drive letter. **[COLOR=DarkRed]Y[/COLOR]** is the partition number. The first drive is "a" and the first partition is "1". Example: sd[I]a1"


[/I]

---

### Post by andrewthomas on 2010-09-27
post the output of 

```
sudo fdisk -l
```

---

### Post by elDux on 2010-09-28
This is what showed up when I typed in sudo fdisk -1

/bin/sh: sudo: not found

---

### Post by andrewthomas on 2010-09-28
that is an l not a 1 just copy and paste the command

---

### Post by elDux on 2010-09-29
This is what came up

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

---

### Post by andrewthomas on 2010-09-29
> **elDux said:**
> [COLOR=Red][COLOR=Black]Thanks, how do i know what I'm supposed to enter my value as. I don't know the correct drive/partition or even what that refers to. [/COLOR]
[B]

"Important:[/B][/COLOR] **All instances of [COLOR=DarkRed]sdX[/COLOR] and ****[COLOR=DarkRed]sdXY[/COLOR] must be replaced with the correct drive/partition** for your system. (sda, sdb, sda1, sda5, sdb5, etc). **[COLOR=DarkRed]X[/COLOR]** is the drive letter. **[COLOR=DarkRed]Y[/COLOR]** is the partition number. The first drive is "a" and the first partition is "1". Example: sd[I]a1"


[/I]
You would use sda and sda1.

---

### Post by elDux on 2010-09-29
Nice. I got it working. Thanks so much!

---

### Post by andrewthomas on 2010-09-29
Glad to be of help.

---

### Post by andrewthomas on 2010-09-29
When the problem is fixed, please mark the thread as [SOLVED] using the thread tools menu.

---

