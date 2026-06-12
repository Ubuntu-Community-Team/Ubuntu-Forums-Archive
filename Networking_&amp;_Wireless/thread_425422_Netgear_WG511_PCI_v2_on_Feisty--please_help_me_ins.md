---
title: "Netgear WG511 PCI v2 on Feisty--please help me install driver"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by shuttleworthwannabe on 2007-04-27
I have done a search on this forum, and there is a detailed instructions on FAQ for this for drapper; I have not followed it to the tee, but checked synaptic for ndiswrapper, and installed that. But my WG511 is still dead.

Here is the output from $lspci -vv


02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
        Subsystem: Netgear WG511 v2 54MBit/ Wireless PC-Card
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step

It seems to be registering, but the LED is not coming on. Do I have to do anything else; like install a driver? where to get driver and how to install this.

Thanks in advance,

SWB

---

### Post by shuttleworthwannabe on 2007-04-28
Anybody?

Update:  I have downloaded the Windows driver xxx.exe; how do I point ndiswrapper to pick up the xxx.inf within this xxx.exe file?

---

