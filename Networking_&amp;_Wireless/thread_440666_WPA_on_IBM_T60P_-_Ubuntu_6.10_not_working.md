---
title: "WPA on IBM T60P - Ubuntu 6.10 not working"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by Yoguess on 2007-05-11
Hi,
I've tried googling and searching here but no luck.

I found the instruction for ndiswrapper and driver install here:
[http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter](http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter)

Followed the WPA instructions here:
[http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa](http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa)

it still dont work, so I did the debug commands at the end:
sudo dhclient -r wlan0 && ifconfig wlan0 down && killall wpa_supplicant
sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd
"yoguess@yoguess-laptop:~$ sudo dhclient -r wlan0 && ifconfig wlan0 down && killall wpa_supplicant
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:7e:41:05:3e
Sending on   LPF/wlan0/00:19:7e:41:05:3e
Sending on   Socket/fallback
SIOCSIFFLAGS: Permission denied
yoguess@yoguess-laptop:~$ sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd
bash: /usr/sbin/wpa_supplicant: No such file or directory"

no such file or directory - I'm  a newbie and so i'm stuck
help please

---

### Post by Yoguess on 2007-05-12
anyone?

---

