---
title: "D-Link DWA-642 help"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by FAJALOU on 2008-10-05
Hi, I am using a D-Link DWA-642 wireless pci notebook card to get onto the internet.  Unfortunately, it uses Atheros AR5416 chipset, which is not currently fully supported by Madwifi, and ath5k is still in dev, so I thought I would share what I have done to get it to work.  This can be found here: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=935573](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=935573)

However, even the above how-to I have found to be a tad bit buggy (ie sometimes I cannot connect to my secured network, but then I will restart and will connect perfectly fine to it.)  This is what confuses me:  I created the the above how-to, and everything goes as should.  However, using Madwifi by itself in linux-restricted-modules doesn't work:  I have to use ndiswrapper and that trunk for it to work.  My question is can anyone think of anything that could be the reason for the card to sometimes does not connect to my encrypted (WPA) network, but connects to an unsecured network, and then when I reboot, it will connect to the encrypted network no problem?  Below is the pertinent part of sudo lshw:

```
 *-network
          description: Wireless interface
          product: AR5416 802.11abgn Wireless PCI Adapter
          vendor: Atheros Communications Inc.
          physical id: 0
          bus info: pci@0000:03:00.0
          logical name: wlan0
          version: 01
          serial: 00:1b:11:64:f1:28
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,08/28/2006,6.0.1.75 ip=192.168.1.105 latency=128 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

And sudo lspci -v
```
03:00.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)
	Subsystem: D-Link System Inc Unknown device 3a6a
	Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 128, IRQ 10
	Memory at 38000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] #80 [0000]


```

Maybe there is a way to use iwconfig to have it always connect to my network?  I don't know, all I know is that sometimes it won't connect to my wifi network, and then on reboot it does connect.  Any thoughts or suggestions would be helpful.  thanks.


EDIT:  Was just looking through sudo lspci -v and found that my vga card (ati raedon mobility 7500) is running on the same irq as the wireless card (IRQ 10), could this be a source of the error, and if so, how can I change one of the IRQ's to a different number?

---

