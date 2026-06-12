---
title: "Wake-on-LAN, two NICs, PCI 2.2, MK40VN"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by mbappe on 2008-04-12
I've been unable to get wake-on-lan working with my Encore ENLGA-1320 gigabit NIC and Shuttle MK40VN running Gutsy.  Both PCI card and motherboard advertise support for WOL and PCI 2.2.  And I can't find a WOL header on either (It shouldn't be necessary with PCI 2.2, right?).

I have been able to get WOL working using the built-in VIA network interface but it is only 100 Mbit.

I'd prefer to disable the built-in network interface and use the gigabit NIC exclusively, if possible.  Can anyone help me figure out the magic?

If that is not possible, then my second choice would be to use the built-in network interface for WOL, but use the gigabit PCI NIC for everything else.  Is it possible to configure my system to do that?

---

