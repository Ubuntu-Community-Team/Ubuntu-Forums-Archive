---
title: "Wireless Network Managing Program"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by canarsie on 2006-09-06
Is there a good program I can use that detects networks in the area (even if I don't know the SSID)?

---

### Post by Almighty on 2006-09-07
WiFi Radar or Network Manager should do it. Both are available in synaptic.

---

### Post by WalmartSniperLX on 2006-09-07
> **Almighty said:**
> WiFi Radar or Network Manager should do it. Both are available in synaptic.

Yup those two are great. Im using Network Manager right now.

---

### Post by canarsie on 2006-09-08
Alright, I got Network Manager, but it doesn't show up in Alacarte Menu Editor and I can't seem to get the executable to run.  When I try to run it nothing happens.

---

### Post by spd106 on 2006-09-08
Network Manager works through an applet. It should be near the old network icon and the clock. Click on it to access the network scan. If it doesn't find your card then you need to open the /etc/network/interfaces file and comment out (ie put a #) on each line of the interface config. Then log out and log in again. 
See [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager).

If Network Manager doesn't work well for you then consider wifi-radar. I find it works much better and allows static ip.

---

### Post by canarsie on 2006-09-11
Thanks, it's all working now.

---

