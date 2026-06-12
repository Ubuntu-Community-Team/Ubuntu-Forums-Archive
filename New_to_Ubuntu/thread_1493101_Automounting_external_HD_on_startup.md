---
title: "Automounting external HD on startup"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by morosgoványi on 2010-05-25
I have an external drive (NTFS) that I use for media/documents/etc and I'd like to have to it automount on startup. It shows up in Nautilus, but it's a bit of a hassle to open something like Rhythmbox and attempt to play something only to have to go back and mount the drive. From what I understand, I'd have to edit the fstab file but I'm not sure how I should go about adding this.

---

### Post by mbzn on 2010-05-25
This is my fstab entry:

/dev/sdc1 /media/music ntfs-3g defaults,locale=en_ZA.UTF-8 0 0

The part that goes "locale=en_ZA" is my computers default language and i think you'll have to change. 

Yuo could also read through this:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by morosgoványi on 2010-05-25
Ok, I added this line to my fstab file.

```
/dev/sdb1 /media/Expansion ntfs-3g defaults 0 0
```

It works when no other usb device is connected. It seems my mp3 player takes the /dev/sdb slot if it's connected while booting the computer. How do you know what devices take what slots? In another words, how do I mount my expansion drive so that no other device will interfere with it on start up?

---

### Post by morosgoványi on 2010-05-25
Ok, I found something that solves my problem. Instead of using /dev/sdb in fstab, the device should be named by its UUID which is found by running blkid /dev/***. In other words, enter UUID="numbers and letters" into the fstab file instead of /dev/sda.

---

### Post by SRST Technologies on 2010-05-25
A better way of doing this which will not involve mucking with fstab by hand is to install the following packages:

ntfs-3g ntfsprogs ntfs-config

Then you'll have a handy utility in your menu that will let you define how the drive gets mounted, where, and if it's read write.  It'll also cause it to automount on insertion and even let you unmount it before yanking the plug which can cause data corruption.

---

