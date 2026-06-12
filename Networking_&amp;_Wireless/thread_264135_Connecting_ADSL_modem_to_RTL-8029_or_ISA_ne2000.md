---
title: "Connecting ADSL modem to RTL-8029 or ISA ne2000"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by alice07 on 2006-09-24
I've just installed ubuntu 6.06 and haven't been able to get either of my network cards to connect to my ADSL modem.

The PCI card I use under Windows is detected as an RTL-8029(AS), but it doesn't get assigned an address by dhcp from the modem in linux. I've tried assigning a static address of 192.168.1.100 (the address it invariably gets in Windows), but it still can't communicate with the modem, which is 192.168.1.1. The Ethernet Active light on my modem doesn't come on when connected to this card.

If I connect the modem to my ISA ne2000 clone the Ethernet light on the modem comes on, but I can't get linux to detect this card at all. I've tried running modprobe ne, but got the following message:
FATAL: Error inserting ne (/lib/modules/2.6.15-26-386/kernel/drivers/net/ne.ko): No such device or address

I'd greatly appreciate any suggestions.

---

