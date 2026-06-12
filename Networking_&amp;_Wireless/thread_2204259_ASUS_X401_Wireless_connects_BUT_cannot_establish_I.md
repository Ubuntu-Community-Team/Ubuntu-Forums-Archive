---
title: "ASUS X401 Wireless connects BUT cannot establish Internet"
date: 2014-02-07
forum: Networking &amp; Wireless
---

### Post by kieran3 on 2014-02-07
I think it has something to do with my router. I have tried many of the fixes I've read on here to no avail.  If this helps, I tried connecting to a neighbors unsecured WIFI and it had no problem. I am running an old linksys router with WEP.

---

### Post by kieran3 on 2014-02-07
here is my iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"kieranssid"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:13:10:A9:68:A3   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36   Missed beacon:0


```

---

### Post by kieran3 on 2014-02-09
Solved. I don't remember which thread was the final tip off to me, I've read so many.  The drivers for my ASUS don't like WEP encryption.  Changed the router settings to WPA2 and problem solved!!

---

