---
title: "DHCP IP Address Allocation"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by chrisdeeley on 2007-06-13
I'm running Ubuntu 7.04 as a DHCP server.

Does anyone know why my DHCP server allocates an IP Address from the highest end of my range first?
I have set my range as 192.168.0.5 to 192.168.0.50, and it always allocates 192.168.0.50 first followed by 49 etc. Is this normal?

My dhcpd.conf file is as follows:

############################

default-lease-time 60;
max-lease-time 60;
option domain-name "home.local";
option routers 192.168.0.1;
option subnet-mask 255.255.255.0;
option domain-name-servers 192.168.0.1;

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.5 192.168.0.50;
}

############################

I've tried configuring this file manually, and using webmin, and it works fine, just the IP Address's always allocate in reverse order.

---

### Post by arunkv on 2007-06-13
From the [man page for **dhcpd.conf**]("http://www.daemon-systems.org/man/dhcpd.conf.5.html"):

[INDENT]The  DHCP  server generates the list of available IP addresses from a hash table.   This means that the addresses are  not  sorted  in  any particular  order,  and so it is not possible to predict the order in which the DHCP server will allocate IP addresses.   Users of previous versions  of  the  ISC  DHCP server may have become accustomed to the DHCP server allocating IP addresses in ascending order, but  this  is no  longer  possible,  and there is no way to configure this behavior with version 3 of the ISC DHCP server.
[/INDENT]

---

