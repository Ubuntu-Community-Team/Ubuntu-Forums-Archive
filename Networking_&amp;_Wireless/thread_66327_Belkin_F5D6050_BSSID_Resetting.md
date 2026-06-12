---
title: "Belkin F5D6050 BSSID Resetting"
date: 2005-09-16
forum: Networking &amp; Wireless
---

### Post by bobgreen5s on 2005-09-16
I have successfully gotten my Belkin Wireless USB adapter using the 
at76c503a  / atmel drivers. My only problems for the adapter is that the wireless adapter doesn't automatically start up when ubuntu loads and the adapter stops working every few minutes. The solution to both of these problems is to deactivate and activate wlan0 in the gnome network dialog. I would prefer a better solution because it is annoying to deactivate and activate the wireless adapter every few minutes. When I did "tail -f /var/log/syslog" I found out that when the adapter stopped working the message, ```
Sep 16 18:21:01 localhost kernel: /usr/src/modules/at76c503a/at76c503.c: wlan0: lost beacon bssid 00:12:17:ac:ba:cb
```, then I have to deactivate and activate the adapter to get it to be working again.


Any help would be appreciated.

---

### Post by bobgreen5s on 2005-09-17
Any ideas?

---

