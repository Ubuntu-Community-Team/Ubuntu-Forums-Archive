---
title: "Air Live WT-2000PCI fully recognized except for DHCP."
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by Adrian_b on 2006-10-29
Hi, i'm having a problem with my newly bought Air Live WT-2000PCI ( [http://www.ovislink.com.tw/wt-2000pci.htm](http://www.ovislink.com.tw/wt-2000pci.htm) )
In Ubuntu 6.06, it's automaticly recognized as ra0, i can do an 'iwconfig ra0 key open -WEPKEY- && iwconfig ra0 essid -ESSID-' but when i try to get my adress and etc. by DHCP by doing 'dhclient ra0', i get 2 or 3 DHCPDISCOVER, but no receivings.
(In Xubuntu 6.10, the interface is called wlan0 but gives the same results.)
In Windows XP, it does this perfectly. (so i'm guessing the WT-2000PCI card is not fully linux-compatible?)

This method worked with my previous wireless card (SMCWPIT-G)

---

