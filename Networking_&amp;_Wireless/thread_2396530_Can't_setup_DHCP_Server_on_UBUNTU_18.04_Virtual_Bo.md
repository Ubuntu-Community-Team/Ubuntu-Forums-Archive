---
title: "Can't setup DHCP Server on UBUNTU 18.04 Virtual Box in Network with GNS3"
date: 2018-07-17
forum: Networking &amp; Wireless
---

### Post by bicad0 on 2018-07-17
I try to setup a Ubuntu server on Virtual Box, the clients computer can't detect the DHCP server, i install the DHCPd
[LEFT][COLOR=#333333][FONT=monospace]sudo apt install isc-dhcp-server

i define my network and range
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]subnet 192.168.1.0 netmask 255.255.255.0 {
 range 192.168.1.150 192.168.1.200;

[LEFT][COLOR=#333333][FONT=monospace]sudo systemctl restart isc-dhcp-server.service[/FONT][/COLOR][/LEFT][B][I][U][SUB][SUP]
[/SUP][/SUB][/U][/I][/B][/FONT][/COLOR][/LEFT]Nothing goes up

---

### Post by SeijiSensei on 2018-07-17
What does /var/log/syslog show?  What about

```
sudo systemctl status isc-dhcp-server.service
```

Please copy and paste the contents of dhcpd.conf inside of [noparse]```

```[/noparse] tags here.

---

