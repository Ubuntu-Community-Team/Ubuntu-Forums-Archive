---
title: "can't  install wireless card on ubuntu 7.10"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by earthsaver on 2008-05-10
I have a netgear wpn111 wireless card I noticed this is not on the list of supported cards i have an 8 year old gateway with gusty gibbon and it doesn't detect  the card when i plug it in.   I called netgear support and they won't support any linux systems. will it work or should I get a different card  can anyone give me detailed instruction how to get it working.

---

### Post by EXCiD3 on 2008-05-10
Look like you will need to install the wireless card support by using ndiswrapper.

Couple helpful links:
[http://www.linuxcompatible.org/linux_driver_for_wpn111_usb_wireless_adapter_t34324.html](http://www.linuxcompatible.org/linux_driver_for_wpn111_usb_wireless_adapter_t34324.html) [http://www.linuxquestions.org/questions/linux-wireless-networking-41/getting-netgear-wireless-usb-dongle-wpn111-atheros-chipset-to-work-on-ubuntu-6.06-515914/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/getting-netgear-wireless-usb-dongle-wpn111-atheros-chipset-to-work-on-ubuntu-6.06-515914/)

---

### Post by earthsaver on 2008-05-11
I tried nsdiswrapper but when I install the autorun.inf file from the driver cd it says invalid driver.

---

### Post by EXCiD3 on 2008-05-11
Haha easy mistake to make. The Autorun.inf file is a configuration file to tell windows what program should autorun when the cd is inserted into a windows machine. :-P There should be a directory with Windows XP drivers inside it. The files that you will need are something like:

netwpn11.inf + wpn111.sys + ar5523.bin 

If you find these, copy them from the cd to your home directory. and use the netwpn11.inf file with ndiswrapper. That should work much better. ;)

---

