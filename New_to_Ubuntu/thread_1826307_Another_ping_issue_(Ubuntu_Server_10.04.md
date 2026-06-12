---
title: "Another ping issue (Ubuntu Server 10.04"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by AnnainOK on 2011-08-16
I posted yesterday with a ping issue that was solved in quick fashion. I have another today. 

From my XP Desktop I can ping my server by IP address, and by the name "server1" I _cannot_ ping by server1.myisp.com. Windows returns a *"Ping request could not find host server1.myisp.com. Please check the name and try again."*

On the server, I've checked "hostname" and "hostname -f" both come back as server1.myisp.com

1. Is this a problem?
2. What can I do to correct it if it is?

Here's a copy of my various configuration files:




### /etc/hosts ###


127.0.0.1       localhost.localdomain localhost
192.168.1.200   server1.myisp.com server1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

###############################################################

### /etc/resolv.conf ###

search myisp.com server1.myisp.com
nameserver 69.8.2.15
nameserver 69.8.2.12

###############################################################

### /etc/networking/interfaces ###


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1

Thanks for the help (again).

---

