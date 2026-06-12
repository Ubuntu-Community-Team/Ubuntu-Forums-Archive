---
title: "WiFi dropping on group rekeying?"
date: 2016-07-31
forum: Networking &amp; Wireless
---

### Post by Y4kuzi on 2016-07-31
Hello,

for as long as I can remember I've been having this issue that causes my WiFi to drop (spec details in pastebin link below).
To  keep it short, it mostly happens when I'm afk (sleep, out, etc.) and  then when I come back, the WiFi icon shows it's still connected, but it  does not reply to any ping commands.
I have to manually restart the network-manager (sometimes multiple times...) to fix it.

In the syslog file I keep seeing this line pop up:
```
Jul  31 08:33:42 hp-ubuntu wpa_supplicant[1035]: wlo1: WPA: Group rekeying  completed with 00:23:69:2e:53:57 [GTK=CCMP]
```
I'm not sure what that means, but it keeps showing up right before the connection is lost, so it might be relevant.

Here is the output of the wireless-info script:
[http://pastebin.com/KD7KsZdD](http://pastebin.com/KD7KsZdD)

---

### Post by Y4kuzi on 2016-08-15
Nobody? It just happened again:
Aug 15 17:05:59 hp-ubuntu wpa_supplicant[2800]: wlo1: WPA: Group rekeying completed with 00:23:69:2e:53:57 [GTK=CCMP]

---

