---
title: "Getting IP OFF NIC"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by vdatadin on 2008-04-16
Hello,

I've just installed Ubuntu 7.10 on PC that previously ran Windows - completely replacing everything. The PC is on a DHCP LAN, but cannot access the network - because, as I've now been told - an IP address was put on the Network Interface Card.

How do I go about accessing and removing the IP address on the PC's NIC in Ubuntu?

Thank you

---

### Post by jonallport on 2008-04-17
To the best of my knowledge there is no way to hard-wire an IP address into a NIC.

What this person may have been alluding to was you DHCP server configuration.  It is quite feasable that you network admin wanted static IP addresses handed out based on the hostname of the requesting station.  If you've steamrolled over Windows and built Ubuntu on top you've probably also changed the hostname.  

Try setting the hostname to the same as the Windows installation was (or borrow a friend/neighbour's identity and see of you get "their" IP address)

Also, run 'dhclient eth0' (or whatever iface it is) and post the result, please.

Hope that helps,
Jon

---

