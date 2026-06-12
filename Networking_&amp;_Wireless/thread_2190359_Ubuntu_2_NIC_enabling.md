---
title: "Ubuntu 2 NIC enabling"
date: 2013-11-27
forum: Networking &amp; Wireless
---

### Post by Ryan_Jay on 2013-11-27
Hi all, 

Please help me out. I'm to desperate now. :(

I'm running ubuntu server and i'm having a problem with my NIC. 
My Scenario.

[router]----eth0----[ubuntu server]---eth1---[switch]---[windows server]

Router-DHCP server enabled.
Windows Server- Domain Controller, DHCP Enable.
-------------------------------------------------------------

My problem is how do i configure my eth1 to communicate to my domain? every time i ping my windows server the reply was "Destination Host Unreachable "
I configure my both eth interfaces static.
But, when i try pinging the internet the result was successful.
Please help me. :(

MY eth config.
/etc/network/interfaces
#internet
auto eth0
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1

#Local Network
auto eth1
iface inet static
address 192.168.1.6
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.10

PS. Please help with iptables.

Thank you guys.

---

