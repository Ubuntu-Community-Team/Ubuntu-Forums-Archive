---
title: "no Wifi and no  wired ethernet connection, compaq mini"
date: 2014-09-28
forum: Networking &amp; Wireless
---

### Post by edgar8 on 2014-09-28
hi guys.

Im a new ubuntu user and im having a litle problem with my Compaq mini.

first I try to ***connect ***via wi-fi and surprise, surprise wi-fi is not working, then I try a wired connection and bammm, it fails....

 I see [this ]("http://ubuntuforums.org/showthread.php?t=2138489")post but no help bc i can't put my laptop on line...

```
[COLOR=#000000][FONT=Ubuntu Mono]03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

[/FONT][/COLOR]thks guys :)

---

### Post by jeremy31 on 2014-09-28
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

This should help you get the files needed to get your wifi going using another PC to download the files

As of a few weeks ago the linux-firmware-nonfree no longer has the firmware you need for wifi

---

### Post by edgar8 on 2014-09-28
im trying to intall b43-fwcutter[COLOR=#333333][FONT=Ubuntu] but im stuck... im a newbie :([/FONT][/COLOR]

---

### Post by praseodym on 2014-09-28
Download this file and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

Installation:
```

sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe -rfv b43
sudo modprobe -v b43
```

---

### Post by edgar8 on 2014-09-28
sudo modprobe command not found :/

---

### Post by edgar8 on 2014-09-28
ups my bad :lolflag:

thank you very much :D

---

### Post by jeremy31 on 2014-09-28
Let us know what method worked and edit the topic on your original post to add [SOLVED]

---

