---
title: "local VM Host network routing and masqerade"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by jbardin on 2008-08-14
Hi,

I have a host with kvm/libvirt, using the default NAT interfaces for the guests. 

What I'm trying to do is route traffic from the host, to the guest subnet, and within the guest subnet. What I want most, is for guests to be able to communicate directly, without bridging eth0.

I have vnet0 with 10.8.0.1, and I can ping it.
The host has one interface, eth0.

There is a route for 10.8.0.0/24 on vnet0. I just can't seem to get the iptables right. The default nat table created by libvirt is:
*nat
:PREROUTING ACCEPT [3996:483357]
:POSTROUTING ACCEPT [1965:140054]
:OUTPUT ACCEPT [1977:141524]
-A POSTROUTING -s 10.8.0.0/255.255.255.0 -j MASQUERADE 
COMMIT

Everything is being accepted in *filter.

Where am I losing the packets?

---

### Post by Fire_Chief on 2008-08-14
You want the guests to be reachable by other PCs on the network or for the virtual guests to talk to each other? 

You can't do the first one with the current setup because the connection method is using NAT instead of bridging. Masquerading NAT was designed to hide the network behind it and make it appear as just one IP address to the rest of the world.

I'm not very familiar with how libvirt handles the individual guest connections (virtual switch or individual connections to outside world). Can the guests ping each other directly? I would think they should be able to do so.

Cheers!

---

### Post by jbardin on 2008-08-14
I would like to have the guests somewhat isolated from the outside network, which is why I'm leaving them on the NAT.

I also thought that the guests should be able to ping each other on the virtual network, but no such luck. I thought that it was setup as a virtual switch, because I see local arp packets going accross vnet0. IP packets to the virtual network just seem to go nowhere though.

---

### Post by Fire_Chief on 2008-08-14
Based on the doc found at [http://kvm.qumranet.com/kvmwiki/Networking]("http://kvm.qumranet.com/kvmwiki/Networking")

You can have individual connections, private group connections (isolated VLAN style where guests can see each other but not the Internet), or public bridged connections. You could mix and match these setups similar to what is shown in this diagram [http://libvirt.org/archnetwork.html]("http://libvirt.org/archnetwork.html")

Cheers!

---

### Post by jbardin on 2008-08-14
Thank for the link.

It look like that's what libvirt is doing already, although there mmay be some default that's different between distro's here. Each guest gets a vnet# interface, which is bridged to vnet0. I just can't see why the guests can't communicate with each other.

---

