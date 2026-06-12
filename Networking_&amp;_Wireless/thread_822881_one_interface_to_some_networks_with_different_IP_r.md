---
title: "one interface to some networks with different IP ranges"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by volmark on 2008-06-08
As I understand eth represents a physical networks card. I have only one physical interface on my system. I need to bind only one interface to some networks with different IP ranges.
If I do something wrong with network I’ll be forced to do a lot of physical work to recreate the system.

Added following lines to /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

iface eth0 inet static
address 192.168.1.222
netmask 255.255.255.0
gateway 192.168.1.4

iface eth0 inet static
address 192.168.111.222
netmask 255.255.255.0
gateway 192.168.111.111 

Got following error messages trying restart with sudo /etc/init.d/networking restart

* Reconfiguring network interfaces... /etc/network/interfaces:13: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:13: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"

My /etc/resolv.conf looks like

search cust.cdnet.dk
nameserver 85.218.184.3
nameserver 85.218.129.11
nameserver 85.218.128.141

What I’m doing wrong????????????

---

### Post by SpaceTeddy on 2008-06-09
you should use virtual interfaces, not real ones for multiple configuration. This said, your config is almost right - just add rename the second device from eth0 to eth0:0.
This will bind a second (now virtual) network card to your already bound physical eth0. You will have two network cards in the system, but they both use the same physical one :)

i think that is what you wanted...

hope it helps :)

PS: you can only have ONE default gateway. Two are not possible ! so one if the gateways must go.

---

### Post by volmark on 2008-06-12
The default gateway should be on the same IP range or it cannot be found. On the large LANs you will use more then one gateways with metric priority.

---

