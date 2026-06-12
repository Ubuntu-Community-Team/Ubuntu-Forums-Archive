---
title: "ubuntu network settings manual input daily"
date: 2014-04-06
forum: Networking &amp; Wireless
---

### Post by burge38 on 2014-04-06
sudo nano /etc/network/interfaces

sudo nano /etc/network/interfaces# This file describes the network interfaces a$
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth1
iface eth1 inet dhcp
address 192.168.1.35
netmask 255.255.255.0
gateway 192.168.1.255

file I keep changing to 

# and how to activate them. For more information, see interfaces(5).# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp

every now and then I get error telling me I logged out to all network software ie filezilla,putty and my beloved coffeecup html editor (network error software caused connection to abort)

to stop this I have to enter eth1 details manual any clues peeps cheers for looking and thanks in advanced were is the admin with the beard gone the guy that's knows everything forgot his name has he left to open own site if so can I have site address please

---

