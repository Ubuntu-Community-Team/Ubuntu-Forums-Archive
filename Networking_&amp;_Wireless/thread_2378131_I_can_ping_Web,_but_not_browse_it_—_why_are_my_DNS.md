---
title: "I can ping Web, but not browse it — why are my DNS settings failing?"
date: 2017-11-20
forum: Networking &amp; Wireless
---

### Post by gbambo on 2017-11-20
Update 6 @ 2:56p on Nov 21


I am working on a creating a small network of virtual machines and containers. So far, I am stuck configuring the host though. There is no virtual machine involved in this connection. Though there are two bridges in place.

Just to clarify, this is on bare-metal in a data center. There is no ISP or modem. The hypervisor is not implicated in the path to the Internet. I am running Ubuntu 17.10.

What works and what does not:
- ping 8.8.8.8 - succeeds
- ping 213.133.98.98 - succeeds
- google.com - failure in name resolution
- web browsing &#8211; no internet connection
- web browsing with firewall disabled - no internet connection
- host google.com &#8211; no servers could be reached
- NoMachine, remoting into host using - succeeds
- antivirus - none


[COLOR=#242729][FONT=Arial]ifconfig -a returns:[/FONT][/COLOR]
lxdbr0 broadcast = 0.0.0.0
enp7s0 broadcast = 0.0.0.0
enp7s0 netmask = 255.255.255.255
[COLOR=#242729][FONT=Arial]My conclusion was that netmask = 255.255.255.255 was the immediate problem as it had enp7s0on a single-address subnet, with no room for a gateway, etc. This was preventing access to DNS services, thus the pattern of failures. But adding static routing to cure that did not restore Internet/WAN access.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I think the contents of /etc/network/interfaces provides most of the other necessary context. Oh, and the fact that netmask on enp7s0 shows as 255.255.255.255 when I run ifconfig -a.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Gateway and broadcast were assigned by my vendor re enp7s0. Using Ubuntu 17.10. I believe I disabled Network Manager.

[/FONT][/COLOR]
# This is /etc/network/interfaces for use on Host
# The loopback network interface
auto lo
iface lo inet loopback

# This is the WAN port
auto enp7s0
iface enp7s0 inet static
address 78.46.80.146
netmask 255.255.255.224
network 78.46.80.128
broadcast 78.46.80.159
gateway 78.46.80.129
# static route entry follows, wherein x.x.0.0 is a wildcard
up ip route add 78.46.0.0/27 via 78.46.80.129 || true
dns-nameserver 213.133.98.98 
dns-nameserver 8.8.8.8

# Virtual bridge on enp6s0 for virtual machine use
auto br0
iface br0 inet static
address 192.168.122.2
netmask 255.255.255.0
network 192.168.122.0
broadcast 192.168.122.255
# gateway 192.168.122.1
up ip route add 192.168.0.0/16 via 78.46.80.129 || true
bridge_ports enp6s0
bridge_stp on
bridge_maxwait 0
bridge_fd 0

# Virtual bridge for container use
auto lxdbr0
iface lxdbr0 inet static
address 10.36.109.2
netmask 255.255.255.0
network 10.36.109.0
broadcast 10.36.109.255
# gateway 10.36.109.1
up ip route add 192.168.0.0/16 via 78.46.80.129 || true
bridge_ports
bridge_stp on
bridge_maxwait 0
bridge_fd 0





/etc/resolv.conf
nameserver 213.133.98.98
nameserver 8.8.8.8





Kernel IP routing table
Destination --- Gateway --- Genmask --- Flags --- Metric Ref Use --- Iface
default --- 78.46.80.129 --- 0.0.0.0 --- UG --- 0 0 0 --- enp7s0
10.36.109.0 --- 0.0.0.0 --- 255.255.255.0 --- U --- 0 0 0 --- lxdbr0
78.46.0.0 --- 78.46.80.129 --- 255.255.255.224 --- UG --- 0 0 0 --- enp7s0
78.46.80.128 --- 0.0.0.0 --- 255.255.255.224 --- U --- 0 0 0 --- enp7s0
78.46.80.129 --- 0.0.0.0 --- 255.255.255.255 --- UH --- 0 0 0 --- enp7s0
link-local --- 0.0.0.0 --- 255.255.0.0 --- U --- 1000 0 0 --- enp7s0
192.168.0.0 --- 78.46.80.129 --- 255.255.0.0 --- UG --- 0 0 0 --- enp7s0
192.168.122.0 --- 0.0.0.0 --- 255.255.255.0 --- U --- 0 0 0 --- br0


ARP
Address --- HWtype --- HWaddress --- Flags --- Mask --- Iface
78.46.80.129 --- ether --- 30:b6:4f:3f:eb:ba --- C --- enp7s0

---

### Post by bashiergui on 2017-11-22
The netmask 255.255.255.255 tells the computer that no other computers are in your network. Which means you can&#8217;t talk to any other computers. The broadcast address is usually 255.255.255.255.

Why did you choose the nameserver 213.133.98.98? That appears to be a German data center. I&#8217;d use 8.8.8.8 myself which could clear up the name resolution problem. Comment it out and see if it resolves.

I don&#8217;t know why ifconfig -a returns different information from your /etc/network/interfaces config does. That seems odd and undesirable.

---

### Post by SeijiSensei on 2017-11-22
> **bashiergui said:**
> The netmask 255.255.255.255 tells the computer that no other computers are in your network. Which means you can’t talk to any other computers. The broadcast address is usually 255.255.255.255.
Actually, the broadcast address depends on the netmask.  For a client in the 192.168.1.0/24 network, the broadcast address is 192.168.1.255.  The "all-ones" broadcast address, 255.255.255.255, matches any host on the network.  For instance, a client computer using DHCP to obtain its address will send the request to 255.255.255.255.

On a "class-B" subnet, like 172.16.0.0/16, the broadcast address would be 172.16.255.255.  For a class-A network like 10.0.0.0/8, the broadcast address is 10.255.255.255.

---

### Post by gbambo on 2017-11-22
So I tried commenting out 213.x.x.x. Still no Internet connectivity. I am using the 213.x.x.x DNS because the machine is in the German data center you identified.

---

### Post by collisionystm on 2017-11-22
So in regards to your WAN - 'dns-nameservers' is plural. You are missing the S at the end. You can define your NS in one line.

```
dns-nameservers 213.133.98.98 8.8.8.8
```

You do not need to configure the static route that you had in there. It is just redundant to what is already defined with your IP/Subnet on the enp7s0 interface.
```

78.46.0.0/27 via 78.46.80.129

```

As for your bridge interface, enp6s0. I'm not quite understanding what you are trying to do. First of all, you need to define enp6s0 as an iface.
```
iface enp6s0 inet manual
```

Secondly, you are setting an IP address of 192.168.122.2 with a 24 bit mask and then adding a static route for 192.168.0.0/16 to go out the WAN?
A 16 bit mask covers everything from 192.168.0.1 to 192.168.255.254. I don't have enough time to explain how routing works but basically this isn't usable. 


Last, the LXC network isn't configured in /etc/network/interfaces. It is setup in /etc/default/lxd-bridge.

Try this config and point your clients to 192.168.122.1. You will need to have *nat setup within iptables/ufw to allow packets to masquerade. I recommend setting up UFW because its very straightforward.
Check out
```
man ufw
```
```
man ufw-framework
```

```

### WAN ###
auto enp7s0
iface enp7s0 inet static
    address 78.46.80.146
    netmask 255.255.255.224
    gateway 78.46.80.129
    dns-nameservers 213.133.98.98 8.8.8.8

### LAN - BRIDGED NETWORK ###
# Interface
iface enp6s0 inet manual
# Bridge
auto br0
iface br0 inet static
    bridge_ports enp6s0
    address 192.168.122.1
    netmask 255.255.255.0
    bridge_stp on
    bridge_maxwait 0
    bridge_fd 0

```

---

