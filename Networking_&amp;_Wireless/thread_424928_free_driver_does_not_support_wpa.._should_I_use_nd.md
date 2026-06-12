---
title: "free driver does not support wpa.. should I use ndiswrapper?"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by feydrutha on 2007-04-27
I have a wireless card with a Texas Instruments acx111 chipset, on a brand new feisty install, and I need to get it connected to a wireless access point with WPA.

The feisty installation set me up with the acx module, but unfortunately, this module does not support WPA as mentioned [here]("http://acx100.sourceforge.net/wiki/WPA") in the project wiki, not even with wpa_supplicant.

So the question is: should I remove the free driver and install ndiswrapper instead?

---

### Post by madmetal on 2007-04-27
> **feydrutha said:**
> I have a wireless card with a Texas Instruments acx111 chipset, on a brand new feisty install, and I need to get it connected to a wireless access point with WPA.

The feisty installation set me up with the acx module, but unfortunately, this module does not support WPA as mentioned [here]("http://acx100.sourceforge.net/wiki/WPA") in the project wiki, not even with wpa_supplicant.

So the question is: should I remove the free driver and install ndiswrapper instead?

if ndiswrapper is ok with your card (sorry but i dunno know) then its better to install ndiswrapper..

---

### Post by Kobalt on 2007-04-27
Yes you need to use ndiswrapper + windows drivers in order to have WPA support on ACX111 based cards...
you can find the proper drivers here if you need them : > #
Card: Linksys WPC54G v2, 54Mbps

    *
      Chipset: Texas Instruments ACX 111
    *
      pciid: 104c:9066
    *
      Driver: Linksys [ftp://ftp.linksys.com/pub/network/wpc54gv2_driver_utility_v2.02.zip](ftp://ftp.linksys.com/pub/network/wpc54gv2_driver_utility_v2.02.zip)
    *
      Other: linux-2.6.8-gentoo kernel, ndiswrapper 0.10.Kept having kernel panic (interrupt-related) upon module load until I set CONFIG_PCI_MSI=y (and unset CONFIG_4KSTACKS, just in case.) Also, used &#8220;ndiswrapper -i LSTINDS.INF&#8221; (NOT lsbcmnds.inf). Works with 64 and 128-bit WEP. Sometimes need to repeat config info (and commit) repeatedly, else driver & card will ignore requested setup. Also works with Gentoo 2.6.9-r9, ndiswrapper 0.12 and drivers that came from CD.
    *
      Other: Working fine on Ubuntu Breezy Badger (kernel 2.6.12) using ndiswrapper 1.9 / ndiswrapper-utils 1.7 and lstinds.inf driver.
    *
      Other: Ndiswrapper is not needed. In Ubuntu Dapper (and probably in other Linux distributions as well) this card is supported natively with the acx driver. See [http://ubuntuforums.org/showthread.php?t=75448](http://ubuntuforums.org/showthread.php?t=75448)
From ndiswrapper website : [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,29/id,list_g-l/#l](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,29/id,list_g-l/#l)

---

