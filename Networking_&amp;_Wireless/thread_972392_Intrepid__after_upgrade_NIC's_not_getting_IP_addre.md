---
title: "Intrepid / after upgrade NIC's not getting IP addresss"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by hanasaki on 2008-11-05
this is a firewall box with an internal (eth1) and external (eth0) NIC
external eth0 gets a dhcp from RoadRunner
internal eth1 gets a static from /etc/network/interfaces

both eth1 and eth0 are in /etc/network/interfaces

when I boot both NIC's come up and can be seen in ifconfig however neither has an IP address.  not even eth1 that has a static IP in interfaces!

/etc/init.d/networking restart / results in everything working as expected
then I log into my id in gnome and it makes eth1 give up the static IP and get one from the dhcp server running on the firewall box 

This all broke with the intrepid upgrade.  Also what is all this NetworkManager and avahi stuff?  it seems to be getting in the way now.

This is all on one box

---

