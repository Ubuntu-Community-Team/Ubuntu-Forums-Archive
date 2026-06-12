---
title: "/etc/network/interfaces"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by sulekha on 2008-07-06
Hi,

the following are some of the lines in my /etc/network/interfaces file

auto lo
iface lo inet loopback
iface eth0 inet static

can any one explain  what these lines are and what is their purpose ?

 iface i know it means interface
 eth0 - ethernet card 0
 inet means what ?
 
 what is meant by loopback , auto lo ?

---

### Post by nixscripter on 2008-07-06
Loopback is a virtual interface which simply sends the packets from the local computer to itself. Leave that auto, as some daemons use it to for networking tricks, particularly RPC.

---

### Post by jamesapnic on 2008-07-06
> iface i know it means interface
eth0 - ethernet card 0
inet means what ?

The inet means that the interface will be used for "Internet" networking, i.e. using TCP/IP.  Static means that it has been supplied with a fixed address and that is not, for example, using DHCP.

---

