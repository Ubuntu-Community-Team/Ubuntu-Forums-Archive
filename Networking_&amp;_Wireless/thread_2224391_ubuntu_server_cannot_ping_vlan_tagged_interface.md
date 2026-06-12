---
title: "ubuntu server cannot ping vlan tagged interface"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by bickyz on 2014-05-16
Hi I have Ubuntu Server 12.04.4 LTS with one physical NIC eth0 and I have tagged few vlans to eth0 but I am unable to ping those vlan ip addresses from other computers:

This eth0 is connected to a HP Procruve Switch port 24 and the config of those vlans are:

VLAN 181
ip address 10.18.32.1 255.255.255.0
untagged 20-24


VLAN 38
ip address 10.18.64.1 255.255.255.0
tagged 20-24

VLAN 25
ip address 10.25.32.1 255.255.255.0
tagged 20-24

Following is the ip addresses on Ubuntu server
/etc/network/interfaces 

# The primary network interface
allow-hotplug eth0

auto eth0
address 10.18.32.199
netmask 255.255.255.0
network 10.18.32.0
broadcast 10.18.32.255
gateway 10.18.32.1


auto eth0.38
iface eth0.38 inet dhcp
vlan-raw-device eth0

auto eth0.25
iface eth0.25 inet dhcp
vlan-raw-device eth0


When I do ifconfig I can see that server has aquired ip addresses for eth0.38 & eth0.25. 
From other PCs I have no issue ping/ssh to 10.18.32.199 whereas I cannot ping eth0.35 (10.18.64.x) / eth0.25 (10.25.32.x) ip address. 
From this Ubuntu Server with or without vlan tagged/configured on eth0 port I can ping other PCs on 10.18.64.x or 10.25.32.x network.

Have I missed anything on this server ?

Any help would be much appreciated, thank you.

---

### Post by TheJ0X3r on 2014-06-05
Hi [COLOR=#000000]bickyz, 

Did you found a solution for your problem? I'm asking because I've a simliar kind of problem in Ubuntu 12.04.4 LTS but my problem only occurs with Kernel 3.2.0-60 or newer.
[COLOR=#000000]I'm routing my internet on vlan10 on my server en wh[/COLOR]en I boot my server with Kernel 3.2.0-59 everything is working just fine. However when is boot my server with a newer Kernel ([COLOR=#000000]3.2.0-60, [COLOR=#000000]3.2.0-61, [COLOR=#000000]3.2.0-62 or [COLOR=#000000]3.2.0-63) something weard happens. My server boots, it brings up the interface vlan10 and it gets a DCHP lease from my ISP. However I cannot reach the gateway of my ISP so routing to the internet is not possible. The routing table is exactly the same as with the older x.59 Kernel and I cannot find a solution for this problem... 

I'm hoping that you point me in the right direction :)[/COLOR][COLOR=#000000][/COLOR][/COLOR][/COLOR][/COLOR]
Thanks!
[/COLOR]

---

