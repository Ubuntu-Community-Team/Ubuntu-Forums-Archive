---
title: "bcm43xx firmware AP mode"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by triplicate on 2008-03-15
I have a PCI wireless card using the bcm43xx firmware which is automatically included in the restricted drivers manager. I have been trying to get AP mode (master mode) to work, to make the card act like a wireless access point to no avail. I have googled this issue, and I have seen several patches for a known bug in the firmware that makes AP mode not work right. However, all of the patches were dated June 2005, and as it was a known issue, I am pretty sure it would have been patched with the firmware released with the current release of bcm43xx-fwcutter.

Anyway, if I do iwscsan eth0 with my laptop, looking for the PCI card which is installed on my desktop, I can't see it. 

I've also tried installing the proprietary drivers with ndiswrapper, and in that case, I can't even change the mode to master in the first place.

Has anyone who has a card with the bcm43xx chipset gotten master mode to work correctly? Help a brotha out.

---

### Post by Who on 2008-03-25
> **triplicate said:**
> I have a PCI wireless card using the bcm43xx firmware which is automatically included in the restricted drivers manager. I have been trying to get AP mode (master mode) to work, to make the card act like a wireless access point to no avail. I have googled this issue, and I have seen several patches for a known bug in the firmware that makes AP mode not work right. However, all of the patches were dated June 2005, and as it was a known issue, I am pretty sure it would have been patched with the firmware released with the current release of bcm43xx-fwcutter.

Anyway, if I do iwscsan eth0 with my laptop, looking for the PCI card which is installed on my desktop, I can't see it. 

I've also tried installing the proprietary drivers with ndiswrapper, and in that case, I can't even change the mode to master in the first place.

Has anyone who has a card with the bcm43xx chipset gotten master mode to work correctly? Help a brotha out.

I am just struggling through the same issues: no luck

I don't get any error messages when I put the card in to master mode, and it does _think_ it is in master mode, but no other computers can see the network it should be making...

The feeling in the OpenWrt and bcm-users IRC channels that I have just spend a little time in is that it is unlikely to work without bleeding edge bcm43 (not the 43xx) drivers, and even then it is kinda hit and miss.

OpenWrt keeps a 2.4 kernel target for Broadcom so they can use the official drivers...

Sorry to bring bad news... I would suggest getting a different network card - if you're in a hurry...

Who

---

