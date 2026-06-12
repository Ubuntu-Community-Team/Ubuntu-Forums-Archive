---
title: "WNDA3100v2 installed, but will not authenticate"
date: 2014-08-14
forum: Networking &amp; Wireless
---

### Post by lawschooldan on 2014-08-14
Hello all,

I am running 14.04 on an older Dell machine. I just got finished installing the drivers for the notorious WNDA3100v2 and all appeared well, until I tried to connect to a secure network.

As a test, I removed my router's WPA&WPA2-Personal security and I could connect without issue.

Whenever I try to connect to a secure network, of course with the correct password, the system will not authenticate.

Any ideas?

---

### Post by lawschooldan on 2014-08-14
For all with the same issue. I solved by changing the "security mode" on my router from using AES/TKIP to TKIP. So I guess this was a crypto problem and not an authentication problem. Hope this helps somebody else, it was very frustrating for me.

---

### Post by lawschooldan on 2014-08-14
SOLVED. For all with similar problems: I fixed this by changing the crypto used by my router from AES/TKIP to TKIP. I guess there was some issue using the crypto method.

---

### Post by lawschooldan on 2014-08-14
SOLVED. For all with similar problems: I fixed this by changing the crypto used by my router from AES/TKIP to TKIP. I guess there was some issue using the crypto method.

---

### Post by weatherman2 on 2014-08-14
Glad you got it working, but keep in mind you limit yourself to 54Mbps connection speeds on an N wireless card when you use TKIP and not AES.  To get the fastest speeds with wireless security and 802.11n, you need to use WPA2 + AES.

---

