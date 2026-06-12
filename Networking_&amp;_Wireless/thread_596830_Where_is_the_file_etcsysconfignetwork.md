---
title: "Where is the file /etc/sysconfig/network"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-10-30
Hi folks,


Ubuntu 7.04 server amd64


I can't find /etc/sysconfig/network but instead I have /etc/network/interfaces

$ cat /etc/network/interfaces```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.0.10
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast  192.168.0.255
	gateway 192.168.0.1

```

I don't have following items on it;
NETWORKING=yes
HOSTNAME="mybox.mydomain.com"


Whether on Ubuntu we don't have /etc/sysconfig/network which is for RedHat only.  Then where to put the above 2 items.


TIA


B.R.
satimis

---

### Post by Lambert on 2007-10-30
Debian distros work a little different as far as networking. I'm not that familiar with what the "NETWORKING=yes" function would be needed for but the hostname is maintained in the /etc/hosts file.

---

