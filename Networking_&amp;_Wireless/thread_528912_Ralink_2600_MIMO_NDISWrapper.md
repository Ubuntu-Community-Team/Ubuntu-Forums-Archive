---
title: "Ralink 2600 MIMO NDISWrapper"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by mastergunner on 2007-08-18
Does anyone have this card and using NDISWrapper? I am a noob and I am connecting to the wireless by using dhclient command only. KDNetworkining doesnt see the card. Could someone help me out with this. I noticed on the NDIS website that only the 2500 is supported. HELP.

---

### Post by DFreeze on 2007-09-14
It's a bit late, but I've the exact same card. Haven't got it working yet, but I don't think you need NDISwrapper to get it to go, actually. Ralink is one of the few Open Source friendly wireless manufacturers out there, and there's a driver for this card available. 

But, as I said I'm also trying to get it going (Gutsy, NetworkManager, WPA) and had no luck so far. Search for RT2x00 (new open source driver, based on the driver from Ralink), RT2500 (Ralink driver).

When one of these drivers is on your system, the card will probably be recognised by KDNetworking. I'm sorry I can't give you any specific help, but I hope you can get started with this. Good luck!

---

