---
title: "Problem: Cannot get my Orinoco card working with monitor mode."
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by lasivian on 2008-03-04
Problem: Cannot get my Orinoco card working with monitor mode.

Card: Orinoco (Lucent Technologies), Model PC24E-H-FC, Firmware 6.10

OS: Xubuntu 7.10
Kernel: 2.6.22-14-generic

So far: Card functioned with basic orinoco drivers. But it did not have any monitor capacity to show open networks. All wireless info had to be added by hand.

Installed hostap package under synaptic.
Installed hostap_utils package under synaptic.
Blacklisted orinoco and orinoco_cs in /etc/modprobe.d/blacklist.

lsmod | grep orinoco returns nothing.
lsmod | grep hostap shows:
     hostap_pci        56976  0
     hostap           114436  1 hostap_pci
     ieee80211_crypt    7040  1 hostap

cardctl ident shows the card as:
     product info: "Lucent Technologies", "WaveLAN/IEEE", "Version 01.01", ""

cardctl status shows:
     function 0: [ready]

card now does not show up in either ifconfig or iwconfig.

Things I might have missed:

     Do I have to do something to the kernel to apply the driver, or is this done automatically by the package?
     What packages are required for the hostap driver to "work"?
     How can I tell if the hostap driver is correctly installed?

thanks

---

### Post by lasivian on 2008-03-04
Any ideas? even silly ones?

I really don't want to go back to Windows :cry:

---

