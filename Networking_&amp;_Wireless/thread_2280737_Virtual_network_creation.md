---
title: "Virtual network creation"
date: 2015-06-02
forum: Networking &amp; Wireless
---

### Post by mjgalindoramos on 2015-06-02
I mean to create a virtual network using virtualbox on 6 virtual machines.

The first virtual machine will work as a router/firewall for the network, using it's 4 interfaces (maximum on virtualbox).
eth0 is a NAT to connect the network to the internet.
eth1 is the first virtual network, it connects to only one virtual machine with an static ip
eth2 the second. Connects to 3 virtual machines and uses dhcp for those machines.
eth3 host-only network.

My /etc/network/interfaces file in this virtual machine is:

```
# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp


#Red interna 1 (Actuando como router)


auto eth1
iface eth1 inet static
    address 192.168.1.1 
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255


#Red interna 2 (DHCP)
auto eth2
iface eth2 inet static
    address 192.168.2.1
    network 192.168.2.0
    netmask 255.255.255.0    
    broadcast 192.168.2.255    
#Red Host-Only


auto eth3
iface eth3 inet static
    address 192.168.56.10
    netmask 255.255.255.0
    network 192.168.56.0
    broadcast 192.168.56.255    

```

My problem is I can't seem to configure the dhcp server (isc-dhcp-server) as it fails when I choose the eth2 interface on dpkg-reconfigure.
Is something wrong with my interfaces file? Should I configure eth2 as it is in it or since it's going to use dhcp for the clients in some other way?
Thanks, I'm new to this.

---

