---
title: "dhcp fails on boot only"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by dread22 on 2008-09-20
I've changed my /etc/network/interfaces file to look like this:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid MySSID
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk xxxx

in order to get a connection at start up rather than login. But when during login I get assigned 169.254.10.* and of course have no network. If I run '/etc/init.d/networking restart' all is back to normal and have full access with the correct ip being assigned.

It just fails on startup which is the exact reason i changed my settings.

---

### Post by pytheas22 on 2008-09-20
I don't know why it's failing, but as a work-around you could always [write a boot script]("http://strabes.wordpress.com/2006/10/16/how-to-create-a-startup-script-in-ubuntu-dapper/") to call '/etc/networking restart' at boot.  It would add a few seconds on to your boot time but should effectively get you a working IP address automatically.

---

### Post by dread22 on 2008-09-21
I tried that I placed links in the rc folders which killed networking at 98 and restarted at 99. Still the same thing happened.

---

### Post by pytheas22 on 2008-09-21
That's strange.  I guess the next-best thing, as far as I can think, is to use a Gnome Sessions startup-command to call '/etc/networking restart'.  Perhaps someone else would have a better idea, though.

---

### Post by dread22 on 2008-09-22
Placing it in the gnome sessions would not give me what I need, I'll still need to log in before the session script execute.

I was thinking maybe its something to do with the dhcp so tried using a static address but still same problem, had to restart networking.

I'll try writing a new script which kills and reboots manually on boot up rather than using the system kill and start scripts maybe that will make a difference like you suggested.

Thx for the help. Hopefully someone can come up with a more elegant solution.

---

### Post by Iowan on 2008-09-22
Check **man interfaces** for information on **pre-up**.

---

