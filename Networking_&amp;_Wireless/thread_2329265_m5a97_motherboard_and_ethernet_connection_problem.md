---
title: "m5a97 motherboard and ethernet connection problem"
date: 2016-06-29
forum: Networking &amp; Wireless
---

### Post by muhammed_ozbilici on 2016-06-29
i am using this motherboard and can connect on ethernet cable via ssh from another computer , but can't connect to web on this computer, how can i fix this ?

---

### Post by gordintoronto on 2016-06-29
What version of Linux? What router? Have you disabled DHCP in network manager? If so, you need to fill in the blanks in your static IP address setup.

---

### Post by muhammed_ozbilici on 2016-06-30
ubuntu 14.04
here is /etc/network/interfaces file
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto p4p1
iface p4p1 inet static
address 192.168.1.91
netmask 255.255.255.0
gateway 192.168.1.1
dns-search 192.168.1.1
dns-nameservers 192.168.1.1

---

