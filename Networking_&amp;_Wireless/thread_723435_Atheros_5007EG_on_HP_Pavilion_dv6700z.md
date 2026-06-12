---
title: "Atheros 5007EG on HP Pavilion dv6700z"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by muindaur on 2008-03-13
I recently got an HP Pavilion dv6700z with the AMD 64 chip and I've run into a problem with the wireless.

The wireless card is an Atheros 5007EG.

I'm running 7.10 64 with full updates.

I've tried to enable it with a few of the guides out there with no success but on the lspci step I do notice it lists the card with the status being disabled.

The only thing that I can think of is the switch needs to be enabled and there isn't an FN key that's labeled with the wireless tower. Only the switch on the front of the system. Is there any way to enable that switch of have it set up so I can hit FN+F2 and have the card enabled and not just sitting there doing nothing?

---

### Post by prshah on 2008-03-13
> **muindaur said:**
> I recently got an HP Pavilion dv6700z with the AMD 64 chip and I've run into a problem with the wireless.

The wireless card is an Atheros 5007EG.

I'm running 7.10 64 with full updates.

I've tried to enable it with a few of the guides out there with no success but on the lspci step I do notice it lists the card with the status being disabled.

The only thing that I can think of is the switch needs to be enabled and there isn't an FN key that's labeled with the wireless tower. Only the switch on the front of the system. Is there any way to enable that switch of have it set up so I can hit FN+F2 and have the card enabled and not just sitting there doing nothing?

Atheros is supported out-of-the-box, but it requires enabling restricted drivers; have you done so? Open: System -> Administration -> Restricted Driver Manager

As long as the switch in front is enabled, you dont need any Fn key combinations.

If this doesn't work, what exactly does ```
lspci | grep -i network
``` and ```
cat /proc/net/wireless
``` and ```
iwconfig ath0
``` (note ath0 and NOT eth0) give as output?

---

### Post by muindaur on 2008-03-13
The restricted drivers are enabled for the card.

If I run iwconfig I get no wireless device found and it only shows lo and eht1.

The most info is from sudo lspci -v

> 03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 137a
        Flags: fast devsel, IRQ 19
        Memory at f6000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1


I have tried the switch for wireless in both positions and the card doesn't appear.

Windows lists the card as 5007EG and the card does work since I was able to connect to wireless with the Vista Home Premium install that came with it before loading Linux.

---

### Post by gasparov on 2008-03-15
madwifi doesn't support that chip, it is supported with an experimental patch on i386 architecture.

---

### Post by kevdog on 2008-03-15
There is a patched version of madwifi that works with the chip however it only runs on 32bit Ubuntu installs.

---

