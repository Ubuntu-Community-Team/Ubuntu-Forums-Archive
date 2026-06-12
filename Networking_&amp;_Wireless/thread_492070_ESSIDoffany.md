---
title: "ESSID:off/any"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by RetepNamenots on 2007-07-04
I'm now having problems with ndiswrapper. [:(]

At the moment I get this when I scan with wlan0:

> iwlist wlan0 scan
wlan0 - Scan completed:
Cell 01 - Address: 00:14:7F:61:0B:CD
ESSID: "Gizmo"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.437GHz (Channel 6)
..
etc


So I know that it's using the wireless card and is actually picking up the network.

However, I can't set any variables on the wireless card itself. At the moment I have:

> iwconfig

wlan0 IEEE 802.11g ESSID:off/any
Mode:Managed Frequency:2.437GHz Access Point: Not-Associated
...
etc


but unfortunately I can't change any of these. If I try:

> iwconfig wlan0 essid Gizmo

then I just get:

> Error for wireless request "Set ESSID" (8B1A) :
SET failed on device wlan0 ; Operation not permitted.

If I try sudo iwconfig wlan0 essid Gizmo, I won't get a direct output, and no changes appear to be made.

Please help!

---

### Post by cloverenge on 2008-04-15
I have the same problem and I would love to see an answer. 
Nancy

---

### Post by Brakkever on 2008-04-19
I've the same problem and discovered that if I re-enter the WPA key in the Network Settings that it works again. At restart though it gets back. In some way the configuration is not stabil.

---

