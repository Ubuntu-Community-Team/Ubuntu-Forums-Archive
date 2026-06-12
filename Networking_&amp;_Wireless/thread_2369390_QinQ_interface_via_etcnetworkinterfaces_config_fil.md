---
title: "QinQ interface via /etc/network/interfaces config file"
date: 2017-08-22
forum: Networking &amp; Wireless
---

### Post by ackowa2 on 2017-08-22
I'm able to setup Q-in-Q interfaces via ip link command:
ip link add link eth0 eth0.123 type vlan proto 802.1ad id 123

and this creates the eth0.123 interface with correct encapsulation of vlan id 123 and ether type 0x88a8

Is there any way to do this in the /etc/network/interfaces configuration file or am I required to do this via a custom script?

---

### Post by ackowa2 on 2017-08-25
Seems like no one knows of any config settings for defining QinQ vlans inside the interfaces config file.
So it seems one has to do this via the ip links commands.

How ever realized that these can be added as command from post-up in the interfaces config file
Example:

auto ens255f1
iface ens255f1 inet manual
        post-up ip link add link ens255f1 ens255f1.123 type vlan proto 802.1ad id 123
        post-up ip link set ens255f1.123 up


auto ens255f1.123
iface ens255f1.123 inet manual
        post-up ip link add link ens255f1.123 ens255f1.123.10 type vlan proto 802.1Q id 10
        post-up ip link set ens255f1.123.10 up


auto ens255f1.123.10
iface ens255f1.123.10 inet static
        address 192.168.10.1
        netmask 255.255.255.0

---

