---
title: "Wireless frequently drops on Ubuntu 18.4 (Intel Wireless 8265 / 8275)"
date: 2019-01-27
forum: Networking &amp; Wireless
---

### Post by karasu on 2019-01-27
My wireless connection frequently drops on Ubuntu 18.4 (Intel Wireless 8265 / 8275), forcing me to restart NetworkManager every few minutes. 

wireless-info.txt is attached

Thanks for any help!

---

### Post by praseodym on 2019-01-28
Crossposting, isn't it?

[https://forum.ubuntuusers.de/topic/haeufige-wlan-timeouts-auf-laptop/](https://forum.ubuntuusers.de/topic/haeufige-wlan-timeouts-auf-laptop/)

Please report back to either posting for helping others

---

### Post by karasu on 2019-01-28
Guilty as charged!

As you point out in the German thread, NetworkManager has issues handling a wireless band that uses WPA1 and WPA2 concurrently.  

Switching the router's security mode from auto to WPA2-PSK[AES] apparently fixed the issue. 

Thanks again for your help!

---

