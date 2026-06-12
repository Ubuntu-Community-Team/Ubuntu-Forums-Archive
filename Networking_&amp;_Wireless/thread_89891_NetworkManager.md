---
title: "NetworkManager"
date: 2005-11-13
forum: Networking &amp; Wireless
---

### Post by BeachBum on 2005-11-13
Hello everyone,

I just found out about NetworkManager, used apt to fetch the app, and am having a difficult time getting it to work with my IPW2200 wireless connection in KDE.  Ethernet plugged in, it works fine,.  No ethernet and the app sees my AP, however the app keeps asking for my 128bit encryption key.  I put it in exactly as its found in /etc/network/interfaces (which works using ifup/down commands), however it keeps asking for my key, and never connects.  In the interfaces file, its entered in the format:

XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX

and this works.  Putting in the key without hyphens doesn't work either.  

Any suggestions?

Thanks!

---

### Post by mgor on 2005-11-14
hm, not sure if it will work, but NetworkManager might want the key in HEX.
try entering it with a leading '0x' (zero x) and then the wep key without the hyphens.

---

