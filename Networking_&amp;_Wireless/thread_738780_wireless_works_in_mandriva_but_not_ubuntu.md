---
title: "wireless works in mandriva but not ubuntu"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by morphodone on 2008-03-29
I have an Acer Aspire 5570z laptop.

The built in wireless card works without any configuration with Mandriva 2008.
Mandriva detects the card as an Atheros AR5006EG.

Ubuntu detects the card as 
 Ethernet controller: Atheros Communications, Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0428
        Flags: fast devsel, IRQ 17
        Memory at 88100000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

Can I force the card to run as an AR5006EG as in Mandriva?

---

### Post by Naguz on 2008-05-15
I know this is quite a bump, but does anyone know hoe this works in mandriva? If they've managed to do it, hopefully the same solution could be used in ubuntu, were there is no stable, working solution for users with this chipset and 64bit as of yet.

The cards are the same btw. The Atheros AR5007EG Uses the Atheros AR2425 chipset.

---

### Post by AdamWill on 2008-05-16
The driver used is the 'madwifi' driver, I can tell you that at least. I don't know if / how well this driver is integrated into Ubuntu. Perhaps it's not installed by default, and you just have to install it? Try searching for packages with 'madwifi' in the name, I guess.

---

