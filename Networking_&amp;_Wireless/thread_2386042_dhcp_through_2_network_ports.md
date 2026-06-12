---
title: "dhcp through 2 network ports"
date: 2018-02-28
forum: Networking &amp; Wireless
---

### Post by pagui2 on 2018-02-28
Hi all, this is my home situation:

[Acces Point with DHCP server] 192.168.1.1
|
| wireless network
|
wlan0 192.168.1.100 with DHCP
PC with xubuntu 16.04
eth0
|
| cable network
|
NAS DS218J

I would like that the NAS (which does not have a wifi card), use the PC's wifi card to get an IP address through DHCP, is this possible?
I  saw that, creating a new ethernet connection on the PC in "internet  sharing" mode, the NAS navigates and the ip is assigned by the PC, but I  would like it to have an IP of the 192.168.1.0/24 network assigned by  the AP

Thank you

---

### Post by SeijiSensei on 2018-02-28
Run dhcp-helper on the PC. It can be configured to forward the requests. See [http://manpages.ubuntu.com/manpages/artful/man8/dhcp-helper.8.html](http://manpages.ubuntu.com/manpages/artful/man8/dhcp-helper.8.html) for details.

---

