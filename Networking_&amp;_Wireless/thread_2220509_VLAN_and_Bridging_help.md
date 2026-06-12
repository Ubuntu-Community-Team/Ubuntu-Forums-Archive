---
title: "VLAN and Bridging help"
date: 2014-04-28
forum: Networking &amp; Wireless
---

### Post by Ryan_Stapleton on 2014-04-28
Hello All,
   I have been reading some forum posts and seem to have hit a wall.  I have the feeling that I am missing something simple though.

I am trying to setup vlans and bridge them for my KVM VMs.

I have added the 8021q to /etc/modules 

My /etc/networking/interfaces file is similar to this (only some IPs changed)

auto lo
iface lo inet loopback

auto eth0.10
iface eth0.10 inet static
    vlan-raw-device eth0

auto eth0.11
iface eth0.11 inet static
   vlan-raw-device eth0

auto br10
iface br10 inet static
   address 192.168.10.11
   netmask 255.255.255.0
   gateway 192.168.10.1
   bridge_ports eth0.10
   bridge_stp off
   bridge_fd 0
   bridge_maxwait 0

auto br11
iface br11 inet static
   address 192.168.11.11
   netmask 255.255.255.0
   bridge_ports eth0.11
   bridge_stp off
   bridge_fd 0
   bridge_maxwait 0


This also fails even if I remove the br11 and eth0.11

What happens is the machine boots as I expect but it does not allow me to ping or go anywhere.

I have done a done a tcpdump -i eth0 and I see a lot of ARP and STP packets so I feel that something is happening on eth0 but not going to my vlans or bridging between.

route -n shows:
Destination     Gateway         Genmask        Flags  Metric  Ref  Use  Iface
0.0.0.0          192.168.10.1   0.0.0.0           UG     100      0     0     br10
192.168.10.0  0.0.0.0          255.255.255.0   U       0         0    0     br10
192.168.11.0  0.0.0.0          255.255.255.0   U       0         0    0     br11

If I change it to not use vlan's such as 
/etc/network/interface

auto eth0
iface eth0 inet static
    address 192.168.10.11
    netmask 255.255.255.0
    gateway 192.168.10.1

it will boot fine with the network but I don't have my vlans of course


This is also on a Dell Server.

I would love to know what am I missing?

Thank you for your time.

---

### Post by Ryan_Stapleton on 2014-04-28
I just realized I didn't post the Ubuntu version.  It is 12.04 LTS.

---

