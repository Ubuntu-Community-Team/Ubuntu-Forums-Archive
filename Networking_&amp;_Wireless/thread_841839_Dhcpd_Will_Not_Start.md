---
title: "Dhcpd Will Not Start"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by joezamboni on 2008-06-26
problem solved

---

### Post by superprash2003 on 2008-06-26
please post your dhcpd.conf file here

---

### Post by joezamboni on 2008-06-27
subnet 192.168.1.0 netmask 255.255.255.0 {
  option subnet-mask 255.255.255.0;
  option domain-name-servers joezamboni.com;
  range 192.168.1.100 192.168.1.200;
}

---

### Post by kevdog on 2008-06-27
You've tried:

sudo killall dhcpd

then try

sudo dhcpd eth1

---

### Post by Iowan on 2008-06-27
```
option domain-name "mein";
option domain-name-servers 192.168.1.1;

default-lease-time 604800;
max-lease-time 604800;
use-host-decl-names on;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.104.25;
  option domain-name-servers 192.168.1.1; 
  option domain-name "mein";
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
#  default-lease-time 600;
#  max-lease-time 7200;
}

```
My (working) **/etc/dhcpd.conf**. I don't have the "option subnet mask" (but I just noticed a somewhat redundant couple of lines at the top). I presume you set up eth1 manually?

---

### Post by joezamboni on 2008-06-28
solved

---

### Post by joezamboni on 2008-07-03
1234.tct

---

