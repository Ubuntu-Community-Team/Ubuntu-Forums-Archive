---
title: "Netgear WG511  v1 and p54pci driver on 8.10"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by scotartt on 2008-05-22
After I upgraded to 8.10, on a DELL Inspiron 8500 with a Netgear WG511 'made in taiwan' (i.e. version 1) wireless PCMCIA card, that previously worked fine, it stopped working completely.

I discovered, almost accidentally that 'sudo modprobe prism54' worked a huge treat and the card came up and used the old configuration and connected to my wireless network just fine.

However it would not survive a reboot.

I subsequently found the prism54 driver was now blacklisted in 8.10's /etc/modprobe.d/blacklist file. Acting on a comment placed in that file I tested both the p54pci driver and the prism54 driver and I have discovered that for me, the p54pci driver DOES NOT WORK AT ALL, and the prism54 driver works great. Correcting the blacklist entry meant that the wireless card now survives a reboot and comes up trumps every time.

While I don't have a problem anymore, I'm just typing this here so that A) anyone with a similar problem searching for it can find a potential solution; B) whoever maintains the wireless networking doco and particularly the list of hardware incompatibilities and the fixes and HOWTOs can access this informatio; and last C) so the maintainers of the p54pci driver can also squizz this information.

Regards,

---

