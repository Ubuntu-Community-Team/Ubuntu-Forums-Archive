---
title: "Adding a new ip to network interfaces?"
date: 2015-08-12
forum: Networking &amp; Wireless
---

### Post by ygtripps on 2015-08-12
Okay I am trying to add a new ip to my dedicated box, but it is not actually working (I know this because it crashed my box's network). If anyone can help me with this that would be wonderful!

Here is the current networking as well as the part I want to add:

Ip:
```

    auto vmbr3
    iface vmbr3 inet static
    	address 192.99.218.240
    	netmask 255.255.255.0
    	network 192.99.218.0
    	broadcast 192.99.218.255
    	gateway 192.99.218.254
    	bridge_ports eth3
    	bridge_stp off
    	bridge_fd 0 

```

Actual file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# for Routing
auto vmbr1
iface vmbr1 inet manual
	post-up /etc/pve/kvm-networking.sh
	bridge_ports dummy0
	bridge_stp off
	bridge_fd 0


# vmbr0: Bridging. Make sure to use only MAC adresses that were assigned to you.
auto vmbr0
iface vmbr0 inet static
	address 167.114.116.16
	netmask 255.255.255.0
	network 167.114.116.0
	broadcast 167.114.116.255
	gateway 167.114.116.254
	bridge_ports eth0
	bridge_stp off
	bridge_fd 0


iface vmbr0 inet6 static
	address 2607:5300:60:6B10::
	netmask 64
	post-up /sbin/ip -f inet6 route add 2607:5300:60:6Bff:ff:ff:ff:ff dev vmbr0
	post-up /sbin/ip -f inet6 route add default via 2607:5300:60:6Bff:ff:ff:ff:ff
	pre-down /sbin/ip -f inet6 route del default via 2607:5300:60:6Bff:ff:ff:ff:ff
	pre-down /sbin/ip -f inet6 route del 2607:5300:60:6Bff:ff:ff:ff:ff dev vmbr0


auto vmbr2
iface vmbr2 inet static
    address 10.21.21.254
    netmask 255.255.255.0
    bridge_ports none
    bridge_stp off
    bridge_fd 0
    post-up echo 1 > /proc/sys/net/ipv4/ip_forward
    post-up iptables -t nat -A POSTROUTING -s '10.21.21.0/24' -o vmbr0 -j MASQUERADE
    post-down iptables -t nat -D POSTROUTING -s '10.21.21.0/24' -o vmbr0 -j MASQUERADE

```

---

### Post by SeijiSensei on 2015-08-12
Do you mean you want one interface to have multiple IP addresses?  With Ethernet adapters, you can just use interfaces like "eth0:0", "eth0:1", etc.  I don't know how that would translate to your situation.  Also when I've done this all the addresses have been in the same subnet, but I don't know if that is a requirement.  You might need to do some [fancy things with the routing tables]("http://lartc.org/howto/lartc.rpdb.html") if they are in different subnets.

---

