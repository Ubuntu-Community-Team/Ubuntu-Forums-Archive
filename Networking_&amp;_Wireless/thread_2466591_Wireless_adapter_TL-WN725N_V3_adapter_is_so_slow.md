---
title: "Wireless adapter TL-WN725N V3 adapter is so slow"
date: 2021-08-31
forum: Networking &amp; Wireless
---

### Post by codefire52 on 2021-08-31
Hello, recently I bought a new pc with TP Link TL-WN725N V3 in it as the wifi adapter. I installed the driver from github.com/lwfinger/rtl8188eu. The device managed to connect but the problem is, the signal strength is too low so it took a long time to load "simple" site like google.com & yes its far slower than my laptop even though my PC and laptop are connected in same network & the same place. Can anyone figure out what's the problem is? I'm using kubuntu 20.04

---

### Post by morrownr on 2021-09-04
I am not familiar with that adapter, that chipset or the driver you used but since nobody else is jumping in, I'll throw what I know out...

It could be a low signal strength issue or a congestion problem or both (or other things for that matter). If it was me, I would install a WiFi Analyzer app on my phone to see what the congestion is like on the channel in use. Maybe a different channel is less congested and you can change the channel in your router. If the router is set to 40 MHz or 40/20 mixed channel width, I would change it to 20 fixed.

If you are interested in information about wifi adapters that are well supported with in-kernel drivers (plug and play) go to this site:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

---

