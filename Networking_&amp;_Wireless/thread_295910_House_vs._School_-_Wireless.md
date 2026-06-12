---
title: "House vs. School - Wireless"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by khoda on 2006-11-08
I use my T60 Laptop at my home and at my school. I have wireless in both places. At home I have to use wpa_supplicant because we use encryption. At school, I don't. 

Every time I get to school I have to kill wpa_supplicant and spend 5-10 minutes reconfiguring my settings to get wireless working (sometimes I can't...). 

I have a ThinkPad a/b/g wireless card, using madwifi drivers (Atheros).

Anyone know a quick way to do this? Maybe a handy program or script?

---

### Post by wieman01 on 2006-11-09
Either Wifi-Radar or NetworkManager are good (graphical) tools. I would opt for Wifi-Radar... You find both in the repositories.

---

### Post by khoda on 2006-11-16
whats a wpa key?

---

### Post by snay on 2006-11-16
Usually the WPA key is the hexideximal equivilant of the wireless APs password. Try putting the password in normally first, as most things will accept it that way, but you may have to convert it to hex if not.

---

### Post by DavidTangye on 2006-11-16
> **snay said:**
> Usually the WPA key is the hexideximal equivilant of the wireless APs password.That's not very accurate. This is a bit better.
There are two types of wireless password schemes: WEP and WPA. Furthermore WPA comes in type/version 1 or 2. I used WPA type 1. Its supported by my router. WPA-PSK (Wi-Fi Protected Access Pre-Shared Key ). My router also supports WEP, but its an earlier encryption scheme and is supposedly less secure, so I figured I might as well use as good as I can.

The key is defined in the router, and also must be in the machines that want to access it. If the router is set for WEP, WPA-PSK, or WPA-abc then set the same in your PC. I used wpa-supplicant to convert the key to a hex encrypted? equivalent and stored that in the /etc/network/interfaces config file. I do not use a wpa-supplicant config file.

An intro to WEP and WPA: [http://kbserver.netgear.com/kb_web_files/n101190.asp](http://kbserver.netgear.com/kb_web_files/n101190.asp)

I found that the best info on this topic, that got me up and going, was in these forum threads:
- [http://www.ubuntuforums.org/showthre...highlight=8B2A](http://www.ubuntuforums.org/showthre...highlight=8B2A)
- [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

