---
title: "Need Help With USB wifi"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by Mike.42 on 2008-06-13
Ok, so I gave up on the D-Link WDA-1320 dispite this page [http://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink]("http://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink")
So, I decided to try a eHome (dlink spinoff) usb wifi card (a E103). I used ndiswrapper with the drivers from the cd. Under the driver name, it says that the hardware is present. But then under network manager there is no wireless options. I also downloaded  Kwifimanager but it also does not work.

---

### Post by SeePU on 2008-06-14
> **Mike.42 said:**
> Ok, so I gave up on the D-Link WDA-1320 dispite this page [http://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink]("http://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink")
So, I decided to try a eHome (dlink spinoff) usb wifi card (a E103). I used ndiswrapper with the drivers from the cd. Under the driver name, it says that the hardware is present. But then under network manager there is no wireless options. I also downloaded  Kwifimanager but it also does not work.
Are you using a usb adapter or pci card?  There's a big difference.  D-Link's usb adapters can be totally different hardware (i.e. different chipset) than their pci network cards.  

The D-link WDA-1320 is PCI and uses madwifi drivers.  That device probably uses the Atheros chipset.  I believe the support is supposed to be good but I read of a lot of complications/issues and complicated configurations.  I can't help with that one.  If you want that one to work, you need to google it or search for that adapter in the forums.

I recommend adapters with either the zydas or ralink chipsets.  In Hardy 8.04, those devices should have drivers already in the kernel (in other words, supported).  I don't know anything about configuring PCI-based cards as I have experience with usb wireless adapters only.  Not that much, either.  

But, on the linux wireless pages, distros with the most recent kernels should play nice with ralink-based and zydas-based usb wireless adapters.

---

