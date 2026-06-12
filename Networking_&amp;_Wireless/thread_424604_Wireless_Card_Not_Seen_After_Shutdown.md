---
title: "Wireless Card Not Seen After Shutdown"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by fathefner on 2007-04-26
how do u turn on ur wireless card in ubuntu it was working yesterday then it was shutdown and now it doesnt see my card? And im not sure what to do it there a terminal command i used  iwconfig
and it told me 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"toho"  Nickname:"toho"
          Mode:Auto  Channel:255  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:55/100  Signal level:37/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

---

### Post by kane77 on 2007-04-27
have you tried:
```
sudo ifup wlan0
```?

---

