---
title: "iwconfig questions"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by tocilog on 2007-05-11
heres my iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"STAAB49AB"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=19/100  Signal level=79/100  Noise level=33/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

for wlan0, is the ESSID supposed to be my router ESSID? if it is, its not the same.  I'm using Xubuntu Feisty.

---

### Post by bukwirm on 2007-05-11
Yes, that essid should match the essid of your router. If you need to know how to set options with iwconfig, you should read it's man page (type "man iwconfig" in a terminal).

---

### Post by tocilog on 2007-05-11
ok thanks. changed the essid to match my router's and the wireless works! FINALLY!

---

