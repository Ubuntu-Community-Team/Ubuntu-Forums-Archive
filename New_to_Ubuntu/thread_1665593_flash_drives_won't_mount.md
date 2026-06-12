---
title: "flash drives won't mount"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by david.buddha on 2011-01-12
I installed ubuntu on my Acer Aspire One net book, and now it will not mount any type of flash drive or sd card so i can save files on them.  the usb ports will work for a mouse and keyboard but nothing else.   What can I do?  Please help.

---

### Post by Natty Narwhal on 2011-01-12
[FONT=Verdana][SIZE=2]I'm having the same problem too! I downloaded Ubuntu 10.10 to my Micro SD card because I don't have a USB flash stick. Then I had to go into the BIOS settings and move HDD SD to the top of the boot list. That worked. But now (and ever since I installed Ubuntu) It will read my SD card and USB (to my Smartphone) but it won't let me look at the files stored or let me transfer pictures and data from device to computer or vise versa.[/SIZE][/FONT]

---

### Post by david.buddha on 2011-01-12
I have used the same flash drive to install ubuntu 10.10 on three computers  two worked perfectly and the Acer won't mount flash drive, read mp3 players i have tryed several.  will not read my android either.:confused:

---

### Post by garvinrick4 on 2011-01-12
You have set configuration editor. Apps/Nautilus/Preferences to check boxes to auto-mount and or auto-open, if that is the problem.
Or run:
```
 sudo fdisk -l
``` (lower case L)

Now make a directory for example.
```
sudo mkdir /media/flash
```Then mount:
```
sudo mount /dev/sdb1 /media/flash
```above using you own sda# from fdisk -l output of media.

---

### Post by EODSteven on 2013-02-19
You have to be Administrator in 12.10 and it works fine!

---

### Post by wildmanne39 on 2013-02-19
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

