---
title: "Aircrack suite"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by Gailen on 2008-08-31
Well, I'm experiencing quite a fiw issues with AIRCRACK Wireless Auditoring suite and its derivates.

But the main one is that I can't block a channel using AIRMON. I mean, by default, when starting a wireless interface by 
```
sudo airmon-ng start wifi0
```
The one created scans continuously all the channels available (with airodump).
But when I try to do the same but fixed to only one channel by
```
sudo airmon-ng start wifi0 1
``` (for example), it still continues scanning all the channels, so whein I tray to do the Fragmentation attack, it fails telling me that the AP is in another channel.
Or when it succeeds, the reception is quite slow.

I do not know but once I managed to fix the channel and everything went much faster, I got the ARP-REQUEST and started getting teh CAPTURE, but not succeed in getting the WEP pass as I got not enough packages (100.000 for a 128byt key). (It was due to a misunderstanding with the instructions)
P.D. - I am probing it with my own WiFi AP

Thank you very much

I'm using an Atheros AR5007EG with the latest MADWIFIs.

---

