---
title: "My wireless card doesn't recognize my network"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by pepotis on 2008-03-31
Hi!
I have a Netgear WG311v3 card installed by ndiswrapper in a Fluxbuntu (Ubuntu with Fluxbox desktop). Everything is ok, but the card doesn't detect my network!!
The starngest stuff is that it can recongize so many AP's which are much farther than my Wifi Router (that is just next to the computer)...
I can connect with the same device to the same network from Windows XP, and I have tried so many drivers with ndiswrapper. I have checked my router configuration and everything is ok (dhcp activated, no SSII hidden....
This is becoming so disapointing.... Please help me

Thanks:

pepotis

---

### Post by pepotis on 2008-03-31
Anybody?

---

### Post by mr.loco on 2008-03-31
Hmm, try "feeding" iwconfig all the data yourself.

```
sudo iwconfig <interface name> essid <SSID>
```

---

### Post by pepotis on 2008-03-31
I tried that before... Doesn't work...

---

### Post by mr.loco on 2008-03-31
Maybe your NIC is set to a different channel than your router.

---

### Post by pepotis on 2008-03-31
How can check it?? How many channels are there??
Thank you very much for your help

---

