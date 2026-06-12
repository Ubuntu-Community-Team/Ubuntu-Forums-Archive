---
title: "Creating wired lan between ubuntu 14.04 and windows 7"
date: 2015-01-05
forum: Networking &amp; Wireless
---

### Post by jay69 on 2015-01-05
Hi everyone,

I am currently trying to setup a connection between 2 laptops, one runnung ubuntu 14.04 and the other windows 7, i am trying to setup the connection through a ethernet QoS Switch. The connection is to enable a data stream from the windows laptop to the ubuntu one. However neither computer seems to recognise each other. If anyone has any advice it would be greatly appreciated.

Cheers

Jay

---

### Post by TheFu on 2015-01-05
Standard networking - set static IPs on both, then put the hostname to IP xref into the /etc/hosts (and whatever Windows calls theirs). You must be root/administrator to modify these files.

Or many home routers can be setup to do internal DNS with DHCP reservations.  If you use that, then both PCs can have DHCP enabled still, which is easier for laptops.  [http://lifehacker.com/5822605/how-to-set-up-dhcp-reservations-so-you-never-have-to-check-an-ip-address-again](http://lifehacker.com/5822605/how-to-set-up-dhcp-reservations-so-you-never-have-to-check-an-ip-address-again)

To test whether this connectivity is working (either with static IPs and hosts file updates OR using the router for internal DNS), try to ping A from B then B from A. If that works, then you've setup nominal IP networking between those 2 systems.

---

