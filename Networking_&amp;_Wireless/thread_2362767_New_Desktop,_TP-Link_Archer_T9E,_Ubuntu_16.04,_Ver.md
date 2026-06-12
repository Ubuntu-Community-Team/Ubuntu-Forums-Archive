---
title: "New Desktop, TP-Link Archer T9E, Ubuntu 16.04, Very spotty wifi"
date: 2017-06-01
forum: Networking &amp; Wireless
---

### Post by dvinci161 on 2017-06-01
Hello there, I have had some interesting wifi connection issues. I just got a new computer with Ubuntu 16.04 as the title indicates.

The wifi card worked immediately upon startup, however, displaying half strength with the wifi signal when the computers around have full. The speed is very slow, around 3~4 Mbps (laptop in the same place has ~25). 

Interestingly, a couple times when I left steam with a download, I returned to find it downloaded quickly and having somewhere reached a peak download speed of 3 MB/s. When I was looking at it however, it was around 50 KB/s. Another interesting note is that if I click the "connection information" under the wifi it sometimes says the speed is upwards of 100 Mbps even as I'll watch a youtube video struggle to load at 144p.

I have looked at some similar issues and attempted some things but none of them seemed to apply to my situation. I noticed there is a sticky for Broadcom drivers, and the driver it recommends for this card "is already the newest version" according to the terminal.
Here's my wireless info the from the script the stickied thread recommends running:
[http://paste.ubuntu.com/24740552/](http://paste.ubuntu.com/24740552/)

Thanks for any help.

---

### Post by praseodym on 2017-06-02
Change the encryption mode in your router to WPA2-AES (CCMP), not mixed mode WPA/WPA2

---

