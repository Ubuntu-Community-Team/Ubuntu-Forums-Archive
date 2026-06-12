---
title: "Belkin 54g F5D7010 can see netowrk, won't connect"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by potatan on 2008-05-20
Hi,

I've just finished setting up a friend's old laptop (Dell Inspiron 1000) with Ubuntu 8.04

All went well, except for the wireless config.  The laptop has a PCMCIA Belkin 54g wireless card, model F5D7010.  I have configured it using the Windows drivers mentioned elsewhere - Wireless Network Drivers applet currently shows
```
 bcmwl5a
 Hardware Present: Yes
```

iwconfig gives:
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:81/100  Signal level:-44 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

and if I click on the network icon in the panel, I can see my Wireless Network.

However, when I try and connect, I supply the WPA key and it tries to connect but with no success.

The key is correct, I use it on three other machines on this network, and the SSID of the wlan network is correct too.

Any ideas where to start looking to troubleshoot?  I'm thinking maybe the card doesn't support WPA?  It's possibly around 4 years old.

Many thanks in advance.

---

### Post by potatan on 2008-05-21
bump

---

