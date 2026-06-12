---
title: "[SOLVED] Problems with wireless WEP 64 bit connection, Intel 4965AGN"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by Wikzo on 2008-03-11
Hello,

I am using a Zepto Znote 3215W laptop with a Intel Pro/Wireless 4965AGN 300Mbit wireless card on Ubuntu 7.10.

I am trying to connect to my schools wireless network, but I can't find it. The computer admin on my school has added my MAC address into his database, and I got the name (SSID) and password for the connection, which is a WEP 64/128 bit HEX.

I have tried to find the connection in the default Network Manager and WiFi Radar, but without luck.

At my home I can connect to many wireless connections without any encryption. But at my school, I can't even see the connection!

Please, can anyone help me?

---

### Post by unutbu on 2008-03-11
Did you try 
```

iwlist wlan0 scanning

```

Replace wlan0 with your wireless interface of course.

This thread also gives a lot of good information:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by Wikzo on 2008-03-12
I got it to work using Wicd which has more options. Thank you.

---

