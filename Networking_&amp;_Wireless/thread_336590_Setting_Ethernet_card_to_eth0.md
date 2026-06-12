---
title: "Setting Ethernet card to eth0"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by chettyk on 2007-01-11
I installed a Realtek Ethernet card after the ethernet port built into my Intel motherboard became faulty. My Dapper Drake had set the Intel port to eth0. When the Realtek card was was installed, Dapper recognises sometimes it as eth1 and at other times as eth2.

Recently, I installed Edgy Eft on the same computer. During the installation process, it was possible to set the Realtek card as the primary port eth0. Is there some way of doing the same thing with my Dapper installation: setting the Realtek card to eth0?

Thanks.

---

### Post by zgornel on 2007-01-12
[http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames](http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames)

---

### Post by chettyk on 2007-01-12
zgornel, Thanks very much for the link. I'll check it out.

Thanks, again.

---

### Post by chettyk on 2007-01-12
zgornel, Reading the webpage you recommended gave me a completely different idea. Since I had Edgy Eft running perfectly well with the Realtek card set as eth0, I copied two configuration files from the Edgy Eft to my Dapper Drake installation

The two files are:

 /etc/iftab
```
eth0 mac [MAC number] arp 1
eth1 mac [MAC number] arp 1

```

The line for eth0 gives the MAC number for the Realtek card and the line for eth1 the MAC number for the old Intel Ethernet port.

The other file that I copied was /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

At the first boot up, the changes seem to work fine.

Thanks again.

---

### Post by zgornel on 2007-01-12
:D Glad to hear it.

---

