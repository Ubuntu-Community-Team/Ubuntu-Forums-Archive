---
title: "Wavelan Chipset"
date: 2005-08-13
forum: Networking &amp; Wireless
---

### Post by tardi on 2005-08-13
I need some help. I booted into the live CD v5.04 and my Wireless Card does not show up under System -> Administration -> Networking (only modem and eth0). It is seen in the Device Manager as Prism 2.5 Wavelan chipset (I have an IBM X30). Any advice one how to troubleshoot would be appreciated. I want to be sure my wireless is working under ubuntu before doing the installation commitment. Thanks.

---

### Post by Zyberdog on 2005-08-13
It is a known problem that most wireless adapters doesn't work "out-of-the-box" with ubuntu and from what I've read it isn't possible to test wether or not it will work if you do a real installation.

But where there is a problem, there is a path. A program/tool called "ndiswrapper" enables you to manually load up drivers for a lot of different wireless adapters which doesn't work without 3rd party drivers.

If you search these forums there are quite some HOWTOs about working with ndiswrapper and on [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) you can see how high your chances are of getting it to work before installing ubuntu.
A version of ndiswrapper (I believe its v1.1) is located on the ubuntu install cd, further  guidance in this can be found in those HOWTOs.

Oh, and it would be nice to know the brand of the wireless adapter, not just the chipset and host laptop  O:)

---

### Post by tardi on 2005-08-14
Thanks for the info. I appreciate it. I've fumbled with ndiswrapper in the past. I'll check out the HOWTOs on the ubuntu site. The README from the ndiswrapper site still assumes a bit too much knowledge. I can usually get the card recognized by the kernel but then fail to get it actually doing what it's supposed to be doing. Ack.

The adapter is known as  the 'IBM High Rate Wireless LAN Mini PCI Adapter'. It's made by Intel.  Chipset: Harris Semiconductor Prism 2.5. Most guys recommend the prism2_pci driver or hostap driver (see [http://hostap.epitest.fi](http://hostap.epitest.fi)) over the orinoco driver. The orinoco_pci driver seems to crash at high transfer rates (I never found out what version).

---

