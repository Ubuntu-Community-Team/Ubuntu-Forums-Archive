---
title: "Dlink DWA-542 Atheros AR5416/ a/g/n/b Wifi Card"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by kdp8791 on 2008-03-26
Hi people, i need some help. I have a Dlink DWA-542 Wireless Network Card, it has a Atheros AR5416 chipset, in the terminal when i typed in "lspci -nn", i got, "00:09.0 Network controller [0280]: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter [168c:0023] (rev 01)". So i am assuming it has been detected perfectly fine, i just need help finding drivers, so i can actually use it, or any other way to get it up and running. If anyone has any ideas please let me know. Thanks in advance.. :)

---

### Post by ELF_O8 on 2008-03-28
have you heard of ndiswrapper?

you can find it here [http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.52.tar.gz&21884682](http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.52.tar.gz&21884682)

to use ndiswrapper, however, you also need libusb and the build-essential from your linux disk.

in order to work with ndiswrapper, you need the drivers (windows drivers) for your card.

I have found them here [http://www.dlink.com/products/support.asp?pid=502&sec=0#drivers](http://www.dlink.com/products/support.asp?pid=502&sec=0#drivers)

---

### Post by greenstar on 2008-04-06
Madwifi should work for your chipset. Instructions [here]("http://madwifi.org/wiki/UserDocs/Distro/Ubuntu"). Based on info found [here]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/installing-d-link-dwa-542-on-ubuntu-7.10-621861/").

HTH

Greenstar

---

