---
title: "Recommended Wireless card I found that work out the box"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by waynepr72 on 2006-11-29
Hi there,

This may help anyone out there who is wondering which wireless card to purchase that will give them no problems in Linux then I would recommend ones from TP-Link.  I purchased a couple of PCMCIA cards for my laptops and a couple of the PCI cards.  They were plug into the laptop and PC and Linux picked them straight out the box no problems at all. I did try a Linksys card first and had no joy as I found out they sometimes use a chipset not currently supported.

The models where from :  TP-Link
PCMCIA card 108 mbs : TL-WN610G
PCI card 54 mbs :  TL-WN550G

I have Drapper and Edgy running on different machines and all worked fine on both. Not heard of this company before but there cards appear to work painlessly in Linux!

Regards,

Wayne

---

### Post by FrodoB on 2006-11-29
The PCMCIA card looks to be an Atheros device, what is the PCI card? Publishing the outputs of lspci would be nice I think.

---

### Post by waynepr72 on 2006-12-04
Here are the details as requested, this is from the Wireless TP-Link PCMCIA card in my laptop.  I hope this information helps.  I am happy how these are working, just need to get WPA working on my wireless network in Linux, currently have WEP working successfully.


0000:06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Atheros Communications, Inc.: Unknown device 1051
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 26000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

Regards, 

Wayne

---

