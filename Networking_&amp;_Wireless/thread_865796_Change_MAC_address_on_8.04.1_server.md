---
title: "Change MAC address on 8.04.1 server"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by richjoyce on 2008-07-21
Hi,

I need to spoof my MAC address on bootup on my server.  I just updated it to Hardy Heron, and now the normal way of doing this by editing /etc/network/interfaces doesn't seem to work

Here is my interfaces file:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
hwaddress ether 00:00:00:00:00:00


And my error when i run `/etc/init.d/networking restart`
> 
 * Reconfiguring network interfaces...                                         
SIOCSIFHWADDR: Device or resource busy - you may need to down the interface
Failed to bring up eth0.


Any help would be appreciated!

Thanks.

---

### Post by richjoyce on 2008-07-21
Figured it out after some google searching,

The problem was it tried to change the MAC after it brought the card back up, and so permission was denied.  This is fixed by using the pre-up option in /etc/network/interfaces, it now reads:

> 
# The primary network interface
auto eth0
iface eth0 inet dhcp
pre-up ifconfig eth0 hw ether 00:00:00:00:00:00


---

