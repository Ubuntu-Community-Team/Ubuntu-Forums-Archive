---
title: "Security Cameras and Mobile APPs"
date: 2022-12-29
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2022-12-29
Security cameras such as the Amazon owned BLINK system are quite reasonable and cheap.

I bought a BLINK pan n tilt camera recently (on offer), actually not a bad device, works well with the app but I was hoping to be able to access it locally using VLC or similar.  I have used IP cameras on my network before, this BLINK camera has an IP address but scanning its IP on nmap using -p- (all 65 thousand ports I believe)  it reports the following:

TCP All 65535 scanned ports are closed
UDP Not shown: 65534 closed ports
PORT   STATE         SERVICE
68/udp open|filtered dhcpc

Appreciate videos go from my network to BLINK then back to me but how is this achieved without my camera being shown as a server of some description?  I do understand systems used are generally to assist setup and not necessitate opening ports on home routers.

Geoff

---

