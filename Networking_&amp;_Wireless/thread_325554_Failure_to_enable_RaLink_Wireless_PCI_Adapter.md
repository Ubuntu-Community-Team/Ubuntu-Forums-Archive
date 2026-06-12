---
title: "Failure to enable RaLink Wireless PCI Adapter"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by sgartner on 2006-12-25
Hi, I am running 6.10 and have fully updated the system via the package manager.

Everything is running fine with the exception of the wireless network interface.

I have a RaLink Wireless PCI Adapter which is shown in the Connections tab of the Network Settings panel, I configure the properties for this interface to connect to my wireless network (with the enable this connection option checked). However in the Connections tab of the Network Settings panel the wireless  connection appears not to be enabled, the checkbox is unchecked.

If I check this box, the system crashes within about 1 second with a total screen freeze, requiring me to reset the box.

I have an Ethernet card in the box also and this Network interface is working fine.

I have a 128-bit WEP Encryption password on the wireless network with MAC filtering disabled.

I am able to connect to the wireless network with other computers and have previously used this box and network card on the same wireless network under WIN XP.

Any suggestions about what might be the problem and/or methods to address the issue would be sincerely appreciated.

Thanks heaps. steve

---

### Post by Floppyjoe on 2006-12-26
What driver are you using?

---

### Post by sgartner on 2006-12-26
I have not explicitly installed any drivers for the wireless network card. I am not even 100% sure of the card manufacturer.

I was able to determine that the wireless card has the Ralink chipset by running the lspci command.

It is an older 11B (might be 24 months old) card.

Should I replace it with more recent hardware that has linux support and is anyone able to recommend a suitable card?

Thanks. steve

---

### Post by sgartner on 2006-12-27
I have done some further reading on the issue and have discovered numerous other posting associated with wireless card chipset, the rt2400. I did a search on the forums with 'rt2400' and got some results, which mostly say that 6.10 has an issue with the rt2400 driver.

I have updated the driver via the package manger, yet the issue persists – i.e. the system crashes when I try and enable the wireless network in the network manager.

Will keep plugging away and post ant results to the forums.

---

