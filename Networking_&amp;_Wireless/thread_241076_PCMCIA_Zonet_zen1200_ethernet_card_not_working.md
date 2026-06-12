---
title: "PCMCIA Zonet zen1200 ethernet card not working"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by mfuqua on 2006-08-21
Hello all.  I just purchased a Zonet zen1200 pcmcia ethernet card, and I can't seem to get the darn thing working.  I've trying it out on a Thinkpad R51 that has a functional ethernet card already, but I plan on using it on and old vaio that doesnt have an ethernet card, but that I currently don't have access too (as it is in France and I'm in the US).  Running ifconfig on eth2, I get:

eth2      Link encap:Ethernet  HWaddr 00:50:22:9B:14:22
          inet addr:169.254.251.81  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::250:22ff:fe9b:1422/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:876492 (855.9 KiB)  TX bytes:5670 (5.5 KiB)
          Interrupt:11 Base address:0xe000

So it is seeing the card, but not getting a signal I guess. From what I understand, the card is supposed to work with great success with just plug-and-play ease, but obviously something is up, and being a noob, I'm not quite sure what.  Any help would be appreciated. Thanks :)

---

