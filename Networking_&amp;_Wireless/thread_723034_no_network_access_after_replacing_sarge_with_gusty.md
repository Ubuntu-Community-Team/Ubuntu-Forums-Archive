---
title: "no network access after replacing sarge with gusty gibbon"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by chiefchimp on 2008-03-13
I replaced debian sarge with gutsy gibbon on my Intel 82845 based P4 system this morning despite and using the same network settings (manual config ip = 192.168.1.100, mask 255.255.255.0, gateway & DNS 192.168.1.254, b/cast 192.168.1.255) now I can't access the network although I can ping localhost, 127.0.0.1, 192.168.1.100 & host's name.
I have tried using e100 module and eepro100 with the same result.

lspci excerpt

02.08.0 Ethernet Controller: Intel Corp. 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

---

### Post by chiefchimp on 2008-03-14
I have tried disabling the onboard intel NIC and installing a realtek 8139 card

tried dhcp with both the intel and realtek NICs

reburned install CD

tried kubuntu 7.04

tried different cables and switch ports

uninstalling knetworkmanager

none of these have made the least bit of difference

---

