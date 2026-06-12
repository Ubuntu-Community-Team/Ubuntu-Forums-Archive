---
title: "Ubuntu 18.04 closing laptop lid stops wi-fi connection"
date: 2020-09-10
forum: Networking &amp; Wireless
---

### Post by nicholas764 on 2020-09-10
I have an issue with Ubuntu 18.04 and closing the lid of the laptop.


What I do to handle this issue:
 
1. I disable turn off display and suspend mode in Gnome Tweak Tool.
2. I set up - digit "2" in default-wifi-powersave-on.conf 


[connection] wifi.powersave = 2 , it means NM_SETTING_WIRELESS_POWERSAVE_DISABLE (2): disable powersave


This tricks dont work. Wi-fi connection still disconects when I close the laptop lid.

---

### Post by TheFu on 2020-09-11
Lid controls are in the systemd  /etc/systemd/logind.conf file.  The manpage for logind.conf explains the settings for each tweak. There are too many options and different settings to list them all here.  Access the manpage by running : **man logind.conf** in a terminal
or by running 
**xman &** and searching the list of available manpages for logind.conf.

These commands are installed on every Ubuntu system, by default.

---

### Post by nicholas764 on 2020-09-12
Thank you ! I know about this file and options, checked before post this thread. I found the answer. The low wi-fi signal was blocked by the lid of my computer. It's so easy.

---

