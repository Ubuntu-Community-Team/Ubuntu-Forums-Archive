---
title: "Broadcom, Intel or Atheros?"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by nick_h on 2008-10-21
I am considering buying a cheap mini-PCI wireless card for my Dell laptop.  There seem to be three reasonable options:

**Dell TrueMobile 1370**

Lower power version of the 1350 which was originally an option for my laptop.
Based on the Broadcom BCM4318 chipset.
Supported by the b43 driver - [link](http://linuxwireless.org/en/users/Drivers/b43#supported)
Is the older bcm43xx driver now obsolete?
Should support my LED and Wireless disable button.

**Intel Pro 2200BG**

The Intel Linux ipw2200 driver is maintained by Intel. 
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

**Atheros AR5006XS**

Based on the AR5414 chipset.
Supported by the ath5k driver - [link](http://linuxwireless.org/en/users/Drivers/ath5k#supportedchips)
However it says: "Support for newer devices like AR5414 and PCI express is pretty new and might not work so well."
Also supported by the madwifi driver - [link](http://madwifi.org/wiki/Compatibility/Atheros)


All three look like they should work out of the box with Hardy, but I have seen a few threads describing problems especially with Broadcom chipsets.

I would prefer a native driver and it would obviously be good if the LED and disable button worked.

Does anyone have experience with any of these cards?

Any comments or suggestions?

---

### Post by Ayuthia on 2008-10-21
> **nick_h said:**
> I am considering buying a cheap mini-PCI wireless card for my Dell laptop.  There seem to be three reasonable options:

**Dell TrueMobile 1370**

Lower power version of the 1350 which was originally an option for my laptop.
Based on the Broadcom BCM4318 chipset.
Supported by the b43 driver - [link](http://linuxwireless.org/en/users/Drivers/b43#supported)
Is the older bcm43xx driver now obsolete?
Should support my LED and Wireless disable button.

**Intel Pro 2200BG**

The Intel Linux ipw2200 driver is maintained by Intel. 
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

**Atheros AR5006XS**

Based on the AR5414 chipset.
Supported by the ath5k driver - [link](http://linuxwireless.org/en/users/Drivers/ath5k#supportedchips)
However it says: "Support for newer devices like AR5414 and PCI express is pretty new and might not work so well."
Also supported by the madwifi driver - [link](http://madwifi.org/wiki/Compatibility/Atheros)


All three look like they should work out of the box with Hardy, but I have seen a few threads describing problems especially with Broadcom chipsets.

I would prefer a native driver and it would obviously be good if the LED and disable button worked.

Does anyone have experience with any of these cards?

Any comments or suggestions?

From what I have seen, the 4318 card has not fared out too well in Hardy.  There have been quite a few people that cannot get it to work with b43, ndiswrapper, and it does not work with the wl driver.  The bcm43xx driver still exists in 2.6.24 but I am pretty sure that it is removed in the 2.6.27 kernel.  I have not seen or heard much about the 4318 card working/not working in Intrepid though.

---

### Post by nick_h on 2008-10-22
Thanks. From reading other threads I wasn't very keen on the Broadcom.

Has anyone had any luck with the Atheros or Intel cards?

Maybe I'll just try to get a very cheap one from eBay. :)

---

### Post by ahumeniy on 2009-12-14
I have a ThinkPad with the ThinkPad 802.11 A/B/G miniPCI card (based on Atheros) and it works out of the box with the athk driver.

---

### Post by nick_h on 2009-12-15
Thanks.  The Atheros does look like a good choice.

---

