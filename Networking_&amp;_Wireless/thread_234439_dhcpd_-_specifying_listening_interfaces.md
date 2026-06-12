---
title: "dhcpd - specifying listening interfaces"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by domstyledesign on 2006-08-11
I'm trying to setup my ubuntu dapper box as a wireless router.  I've got my client machine connected to the internet using static IP's, but dhcp is very desireable.

the problem that i'm having is getting dhcpd to ONLY listen to requests on eth0.  many sites talk about adding "DHCPDARGS=eth0" to /etc/sysconfig/dhcpd, but the /etc/sysconfig didn't even exist on my system.  i created it, but no good.

more searching led me to a /etc/default/dhcp file - looks promising - INTERFACES="eth0"

still no luck.

when i try to run dhcpd, i get this message
```
Listening on LPF/eth0/00:02:e3:0f:53:79/192.168.0.0
Sending on   LPF/eth0/00:02:e3:0f:53:79/192.168.0.0
No subnet declaration for ath0 (192.168.2.4).
Please write a subnet declaration in your dhcpd.conf file for the
network segment to which interface ath0 is attached.
exiting.
```
eth0 is statically set to 192.168.0.1 mask 255.255.255.0 and is the interfaces on which other devices will broadcast for a lease.
ath0 is dynamically set by my router.

i can get the server to run by adding ```
subnet 192.168.2.0 netmask 255.255.255.0 {}
``` to /etc/dhcpd.conf, but i don't want to listen to broadcasts on my wireless card!

what am i doing wrong?

---

### Post by NetworkGuy on 2006-08-13
I think you are doing it right.  Without specifying a range, the dhcp server will not hand out any addresses on your ath0.

---

