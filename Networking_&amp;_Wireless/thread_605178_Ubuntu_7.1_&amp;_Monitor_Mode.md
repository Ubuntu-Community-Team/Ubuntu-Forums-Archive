---
title: "Ubuntu 7.1 &amp; Monitor Mode"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by sylvestor2002 on 2007-11-06
I recently purchased a Dynex Wifi card (model: dx-wgnbc from Best Buy)

I am able to configure my card for use with my wifi access point.  (ie:  I can surf the internet or use synaptic package manager to download programs.)

I am interested in using airodump-ng.  However I can not seem to run this program.  I tried the following: 

B]sudo airodump-ng ath0
[sudo] password for knight:
ioctl(SIOCSIWMODE) failed: Invalid argument
Error setting monitor mode on ath0[/B]

Obviously, I'm having trouble getting my card into monitor mode.  My chipset seems to be Atheros.  From all the posts I've seen, I thought all Atheros chipsets worked with airodump-ng ?  Is is possible that some Atheros chipsets can not be put into monitor mode ?  (By the way, I did install the madwifi drivers)

This is partly what I get when I issue an lspci -v command:

[B]06:00.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
        Subsystem: Unknown device 17f9:0008
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 3c000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>[/B]

Please let me know if there is an easy way to findout if my card does not have the proper drivers to put it into monitor mode or if you think it is impossible with this card.

thanks,

sylvestor.

---

### Post by spd106 on 2007-11-07
I'm not up to date with the current best/easiest method of using aircrack-ng et al, but Madwifi is certainly capable of monitor mode.

It's a subject that has been covered many times on this forum as well as on lots of other websites. For the latest developments try [http://www.aircrack-ng.org/doku.php](http://www.aircrack-ng.org/doku.php)

---

