---
title: "Ubuntu can't even see wireless card in lspci"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by mattbelcher on 2007-04-27
I'm running Ubuntu 7.04 for the first time on a Shuttle XPC. lspci doesn't see my wireless card at all, but it showed up fine in my previous distribution, which was gentoo. It is an Atheros chipset and I previously used the madwifi driver. I'm sure the card is plugged in properly (the light on it blinks periodically).

The host bridge is a VIA VT8375 [KM266/KL266], PCI bridge is VIA VT8633 [Apollo Pro266 AGP].

Any ideas?

---

### Post by chili555 on 2007-04-28
It happens sometimes. I have an ancient laptop with an equally ancient no-name Prism II card that works perfectly with WEP and Network Manager in Feisty, but refuses to identify herself in lspci. How about:```
sudo lshw -C network
```Moreover, I'd suggest installing the Madwifi drivers and going ahead to configure and connect.

---

### Post by mattbelcher on 2007-04-28
Thanks for your help. My card doesn't show up in lshw either, just the ethernet. I'll try your suggestion and just install the madwifi drvers and see how it goes.

---

