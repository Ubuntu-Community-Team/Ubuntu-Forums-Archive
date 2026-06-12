---
title: "Creating a network Startup script"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by McGod on 2008-04-26
I finally got my WPA2 to work!!!:D:D

But on-startup I have to go into terminal and type:

sudo /home/brandon/rtl8187b-modified/wlan0up
sudo wpa_supplicant -Bw -Dipw -iwlan0 -c/etc/wpa_supplicant.conf


How would I put that into a script that I can make run on boot.

---

### Post by psylance on 2008-04-26
put the command in /etc/rc.local

---

