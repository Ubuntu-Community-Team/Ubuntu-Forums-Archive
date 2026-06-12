---
title: "must run wifiradar to connect to wifi???"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by nadp on 2006-11-29
its a strange thing, but sometimes the internet just loses connectivity, i open firefox and it says "looking for http://www.abc.com" until i run wifiradar, wait a few seconds, then it runs normally =S
this happens several times a day...
any suggestions??

---

### Post by Joe_CoT on 2006-11-29
This is probably because wifiradar is reconnecting the connection. You would be able to do the same by doing:
```
sudo ifdown wlan0
sudo ifup wlan0
```

Many people (myself included) experience wifi dropouts in edgy.

---

### Post by nadp on 2006-11-30
umm, by wlan0, do u mean the wireless card? cz i have it as eth0??
(i tried the command above, it didnt give me any result, so i tried eth0 and it gave me something -I am currently on windows, i will give the exact result wen i login from ubuntu)

---

