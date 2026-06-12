---
title: "Computer locks up on wireless WEP connection"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by GriZzlEnLS on 2008-01-18
Hello it seems when I try and connect on my wireless network on 7.10 my laptop locks up. I have yet to figure out how to use WPA so I thought I would try WEP. As soon as I tried to connect my whole computer locks up. I am able to connect to wireless without WEP just fine. I dual boot with windows so I'm pretty sure its not the card. I am using an 8185L RealTek wireless card. Any help would be great thanks.

---

### Post by Hightide on 2008-01-18
Hi, as a starter, have a look at Kevdogs wireless :)tutorial

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

regards

---

### Post by GriZzlEnLS on 2008-01-18
Well tried using the walkthrough and now it gives me this error

anthony@anthony-laptop:~$ sudo wpa_supplicant -w -Drtl8180 -iwlan0 -c/etc/wpa_supplicant.conf -dd 
[sudo] password for anthony:
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'rtl8180' ctrl_interface 'N/A' bridge 'N/A'
Unsupported driver 'rtl8180'.

Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout

---

### Post by GriZzlEnLS on 2008-01-18
/bump can anyone help me with this one?

---

