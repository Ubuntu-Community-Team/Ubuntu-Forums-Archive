---
title: "[SOLVED] How do I connect Intrepid with a Conexant pci card modem?"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by bwallum on 2008-11-07
Hi

I've found some HowTos on dialup connectivity but they all seem old and rather confusing.

I'm in the UK using a modem reported as:-

CLASS=0780
NAME="Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem "
PCIDEV=14f1:2f00
SUBSYS=13e0:8d85
IRQ=5
HDA=
CodecDiagnosed=
slamrTest=
CodecClass=
IDENT=hsfmodem
SLMODEMD_DEVICE=
OPTS=
Driver=hsfmodem-drivers
DRIVER=hsfmodem_drivers

I have tried searching synaptic for 'hsfmodem' but no joy. When I look at the 'old' HowTos I'm not sure if they are referring to the file layout of Intrepid.

Where can I get the hsfmodem and where in the file system should it be placed?

Regards
Bob

---

### Post by bwallum on 2008-11-08
I didn't in the end. The conexant modem drivers are non free and the cost of one year's subscription to a driver is more than the cost of a modem that does work on a free linux driver.

My advice, for what it is worth, is to go broadband if you can. If you can't get a dial up modem that is linux friendly and that generally is not conexant from my experience. I used a Pctel pci card modem (pctel were taken over by conexant so this applies to pre takeover manufactured units)

The process is ugly getting a dial up to work, but do-able. First identify your modem, then download appropriate files, then compile your own driver. Not as bad as it sounds, allow yourself a couple of hours if it is the first time you have compiled anything, then follow this HowTo :-

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

