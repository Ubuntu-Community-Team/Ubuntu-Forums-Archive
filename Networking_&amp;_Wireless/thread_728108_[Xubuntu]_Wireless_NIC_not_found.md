---
title: "[Xubuntu] Wireless NIC not found"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by Plantmiester on 2008-03-18
I've been trying to get my Wireless card to work for some time now, but to no avail.

It is an Atheros AR5007EG (according to my windows device info).

Using ndiswrapper had no luck, as the card itself can't be detected to be wrapped.  I used LinuxAnt driver loader, which again couldn't see the card.  I just recently tried the special install of MadWiFi, which, while the install went on without a hitch, I'm still unable to even detect the cards existance.

This is as much as I can get.

*Update with some corrections/info*

I just lspci'd to check for my card.  Here is the readout I got specifically for the wireless NIC.

> 03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Unknown device 1a3b:1026
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>


I'm not sure about the access denied part, but I have the sneaking suspision that it is causing some trouble.

---

