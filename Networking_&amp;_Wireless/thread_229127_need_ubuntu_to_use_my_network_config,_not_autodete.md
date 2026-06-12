---
title: "need ubuntu to use my network config, not autodetect"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by spudw on 2006-08-04
ubuntu wont automatically load my manually configured dns servers. i have to retype them in network settings everytime i restart. need help!

---

### Post by OpsVentus on 2006-08-04
Is your network interface set to DHCP? Then it will get the dns-servers from the DHCP-server everytime.
One way is to set static-ip to keep your dns-servers.

Cheers,
Bart.

---

### Post by eXisor on 2006-08-04
Edit the /etc/network/interfaces file for the devices. Type 'man 5 interfaces' to get the manual for the file.

---

