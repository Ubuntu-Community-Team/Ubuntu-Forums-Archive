---
title: "AWLH3026T with ndiswrapper"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by Melcar on 2008-02-05
I have an Airlink AWLH3026T that's giving me a headache.  The card "works" out of the box with full encryption (it uses the rt61pci module).  Unfortunately, the card is slow as hell with the default module and I'm trying to get ndiswrapper installed.  Now, I have installed ndiswrapper on several occasions before (for other wireless devices), but I can't seem to get it to work with this card.

I already installed the Windows driver, and ndiswrapper confirms that the driver and card are present.  However, network manager and the network configuration tool in Ubuntu do not see the card.  The card is using wlan0, and when I do a iwconfig, the extension is not listed.  I already added the wlan0 alias to /etc/modprobe.d/ndiswrapper and added the device to /etc/iftab.  Any ideas?

---

