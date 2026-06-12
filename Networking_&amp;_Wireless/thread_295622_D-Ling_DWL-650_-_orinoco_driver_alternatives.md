---
title: "D-Ling DWL-650 - orinoco driver alternatives?"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by SirKillalot on 2006-11-08
Hello folks,
I recently got a notebook with a DEL-650 PCMCIA card. The default driver used by ubuntu is the oricono_cs driver. Actually the wireless is working but I get strange errors in dmesg after connecting the card like:
ADDRCONF(NETDEV_UP): eth1: link is not ready

I use Wifi-Radar to connect to other WLans. But it seems that iwlist doesnt support oricono scan functions with my wifi card.
There are more minor issues like that, which I would like to fix.

Is there any usable alternative for my DWL-650 PCMCIA card out there? I think it uses a Prism-2 or Prism-2.5 chipset. I would be happy if you could also include some setup instructions for me.

Thank you!

---

### Post by tturrisi on 2006-11-08
~$SUDO iwlist eth1 scan
should do it if eth1 is your device name.

---

