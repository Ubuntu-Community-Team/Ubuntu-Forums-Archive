---
title: "WPA2 and Feisty???"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by NobleSavage on 2007-04-21
Does WPA2 "Just Work" with Feisty?   I think I read that WPA worked, but I'm wondering about WPA2.

---

### Post by NobleSavage on 2007-04-21
Bump!  Anyone know?

---

### Post by winter7 on 2007-04-21
Well, I can tell you it doesn't work for my ralink 2561t based at all. I get WEP but I can't even connect to anything, even unsecured.  On a linksys witha broadcom 4306 I have the option for WPA2, however I can't connect to anything either (secured or otherwise). So from my experience no wireless works.

Try it out from a live cd... who knows. you may be one of the lucky ones.

---

### Post by DC@DR on 2007-04-22
I got it worked flawlessly with WPA, but not WPA2, damn it, it seems it couldn't detect WPA2-enabled wireless network, any idea to resolve it? :-(

---

### Post by spd106 on 2007-04-22
Network Manager might have trouble detecting which type of encryption to use if you have broadcast disabled on the AP.

I have WPA-PSK with CCMP/AES here, works fine.

---

### Post by H.E. Pennypacker on 2007-04-26
This has been widely reported.  There has been an issue with WPA2 and Feisty.  Launchpad has a few entries, but nothing wide enough for a problem this big.  I'll have to report a bug if I can't find a solution.

---

### Post by wirelessmonkey on 2007-04-27
The difference between wpa and wpa2 is very small, virtually nothing visible in client deployment.  PMK generation is handled as per the RFC.....  Weird.

---

