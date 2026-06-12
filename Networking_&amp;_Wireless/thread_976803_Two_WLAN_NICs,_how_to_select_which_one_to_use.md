---
title: "Two WLAN NICs, how to select which one to use?"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by maxxfi on 2008-11-09
Hello,

I recently got a laptop Dell D400, where I have installed Ubuntu 8.10
The laptop has already internally a 802.11b miniPCI Intel Pro Wireless 2100 (that is working properly with a fresh installed Ubuntu 8.10), 
but as my home AP has 802.11g capabilities and I have a spare PCMCIA Planet WL-3560 available, I would like the laptop to use that one instead.
Thanks to Atheros chipset, also the Planet NIC is fully working.

The problem is, how do I tell NetworkManager to access by home WLAN *only* using the WL-3560, as Ubuntu seems to try to connect to the home ESSID using both NICs?

[As a workaround, I can disable the Intel card via a special Fn key sequence, but that's not the optimal solution as at the same time it disables also the builtin Bluetooth interface.]

---

