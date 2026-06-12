---
title: "Cannot pair sony wh-1000xm4 headphones"
date: 2020-12-30
forum: Networking &amp; Wireless
---

### Post by tizki on 2020-12-30
Hi,
I'm trying to pair my sony headphones, but it doesn't work.
I tried it on 2 different computers:
laptop with ubuntu  20.10  (5.4.0-58-generic) 
desktop with ubuntu 18.04 (4.15.128-generic) + bluetooth dongle

On both I can see the headphones:

```
[bluetooth]# devices
Device CF:8C:B4:0A:F7:2E LE_WH-1000XM4
```

but when trying to pair it fails:

```
[bluetooth]# pair CF:8C:B4:0A:F7:2E
Attempting to pair with CF:8C:B4:0A:F7:2E
Failed to pair: org.bluez.Error.ConnectionAttemptFailed
```  

I couldn't find anything in dmesg or syslog.

To make sure it's not a bluetooth or a problem with the headphones I tested:
The headphones with my android phone - works
My laptop and desktop with other bluetooth audio devices (JBL speaker and bluephonic headphones) - both work'


any idea how to solve this issue?

---

