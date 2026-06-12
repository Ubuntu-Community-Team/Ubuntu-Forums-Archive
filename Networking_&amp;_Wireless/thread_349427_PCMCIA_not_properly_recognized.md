---
title: "PCMCIA not properly recognized"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by AlexanderDeBernardi on 2007-01-30
Dear all,

during installation of xubuntu on my HP OmniBook 7100 the installation routine is unable to recognize my Xircom adapter card, which has ethernet, modem and ISDN capabilities depending on the adapter connected.

This card works perfect with SuSE 9.x, RedHat Desktop 9.x and RedHat server as well as with some releases of Knoppix.

The make of this card with lspcmcia is
Bridge=yenta_cardbus
Device 0=serial_cs

pccardctl status 
16-bit pc card

pccardctl info
CreditCard Ethernet 10/100 + Modem 56
CEM56

lspci
CardBus bridge TI PCI1250

Hope this gives enough information to advise me how to proceed.

kind regards,

Alexander De Bernardi

---

### Post by AlexanderDeBernardi on 2007-01-30
Dear all,

looks like xubuntu has issues recognizing this card during boot. :confused: 

After summarizing the input about xircom in this forum for me the following commands have successfully gained control of this card:

:idea: pccardctl eject
:idea: pccardctl insert

xubuntu then activated the ethernet drivers and I was in business again.

Thus the remaining issue is now:

how do I get xubuntu to do these steps during startup?

kind regards,

Alexander De Bernardi

---

