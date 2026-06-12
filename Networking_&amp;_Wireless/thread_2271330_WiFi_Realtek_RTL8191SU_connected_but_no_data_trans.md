---
title: "WiFi Realtek RTL8191SU: connected but no data transfer"
date: 2015-03-29
forum: Networking &amp; Wireless
---

### Post by Einfachlacm on 2015-03-29
Hi,

I have the all-in-one Acer Aspire Z5751 with the WiFi integrated card Realtek RTL8191SU. I can connect to the WLAN without any problem but 5 minutes later there is no more data transfer, even when the connexion is normal. I have this proble with all the distributions after the 12.10 release (even **12.04.5** and 14.04.2).

I think is a problem with the driver, it worked until 12.04 and then I imagine it has been changed. I read lot of people that have problems with the same card and tried lot of things but i couldnt solved it. I have even downloaded the driver from the realtek site and installed it with the install.sh file. Maybe i should block the old driver? how can I do that? 

I'm using now Elementary Luna 0.2, the only one that works.

Thanks a lot for your help!!

Kind regards.

lsusb
Carte WIFI = Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter

lshw
*-network
description: Interface réseau sans fil
identifiant matériel: 2
information bus: usb@2:1.6
nom logique: wlan0
numéro de série: 1c:65:9d:6e:97:7d
fonctionnalités: ethernet physical wireless
configuration: broadcast=yes driver=r8712u ip=192.168.0.10 multicast=yes wireless=IEEE 802.11bgn

---

### Post by sandyd on 2015-03-29
*Moved to Networking & Wireless*

---

