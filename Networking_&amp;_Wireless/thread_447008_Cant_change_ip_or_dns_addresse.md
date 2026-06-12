---
title: "Cant change ip or dns addresse"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by alien_doggy on 2007-05-17
I cant change ip or dns addresses in kubuntu feisty 7.04.
When i im changing ip in Network Settings it wont change or when i trye in console.

When i see the config file in /etc/network/interfaces 


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth1
iface eth1 inet static
address 10.0.0.60
netmask 255.255.255.0
gateway 10.0.0.1

it wont change. It will only stay on ip 10.0.0.50. When i change the dns address i will stay on address few seconds then change back to the dns servers from my isp.

I need to change the dns address because it wont work under mac or any linux distro.
To slow resolving.

Anyone have the same issue?

---

