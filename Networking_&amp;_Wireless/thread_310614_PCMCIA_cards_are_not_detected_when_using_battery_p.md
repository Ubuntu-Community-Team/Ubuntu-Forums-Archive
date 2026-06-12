---
title: "PCMCIA cards are not detected when using battery power"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by godrox on 2006-12-01
I installed Xubuntu on a Toshiba Tecra 8000 laptop with PII 266MHz, 128MB RAM and two PCMCIA slots. I use a Dlink 10/100 DFE-690TXD and Linksys WPC11 PCMCIA adapter.

As long as I boot with the AC adapter plugged in both cards are detected and work fine. When I boot on battery power, neither card works. When I boot on AC power, then switch to battery power, then remove and insert a PCMCIA card they also stop working. So obviously this problem is somehow related to working on battery power. 

I've checked the BIOS for any related settings (found none) as well as any BIOS updates (already running the latest version). The only solution I've found for this is to configure /etc/rc.d/rc.wireless.conf (and maybe /etc/pcmcia/wireless.opts ??), but I don't have either of those files on my system. I'm using linux-wlan-ng drivers since the ndiswrapper method would never detect my hardware.

Can anyone please offer some suggestions?

---

