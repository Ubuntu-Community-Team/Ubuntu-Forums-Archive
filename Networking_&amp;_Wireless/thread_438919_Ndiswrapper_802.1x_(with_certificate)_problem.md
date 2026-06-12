---
title: "Ndiswrapper 802.1x (with certificate) problem"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by raul_ on 2007-05-10
I think this is the last post i'll make about wireless.

I have a D-link DWAL-G122 B1. I installed ndiswrapper, and used the windows drivers. Everything is working, but my college uses 802.1x connection, that requires a certificate file.  I followed the instructions carefully, but the first command (after the configuration, that is just copy/paste) ```
 iwconfig wlan0 essid e-U enc open
```

says ```
Error for wireless request "Set Encode (8B2A):
SET failed on device wlan0; Invalid argument. 
```

and i guess that's what stopping my laptop from being authenticated in the next step (wpa_supplicant -D wext -c  /etc/wpa_supplicant.conf -i wlan0 -dd, or something like that)

What can I do? the "official" ralink drivers don't work either.the closest i got was with ndiswrapper

---

