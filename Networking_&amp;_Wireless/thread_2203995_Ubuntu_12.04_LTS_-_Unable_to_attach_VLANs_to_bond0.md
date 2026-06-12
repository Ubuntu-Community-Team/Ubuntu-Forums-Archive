---
title: "Ubuntu 12.04 LTS - Unable to attach VLANs to bond0 or bond1 (bond-mode=4)"
date: 2014-02-06
forum: Networking &amp; Wireless
---

### Post by dcasem1 on 2014-02-06
[COLOR=#252523][FONT=Helvetica]I receive the following error:[/FONT][/COLOR]

```
[COLOR=#252523][FONT=Helvetica]Feb  5 20:09:33 cloud2 kernel: [ 6491.529572] 8021q: VLANs not supported on bond0[/FONT][/COLOR]

```
[COLOR=#252523][FONT=Helvetica]
when attempting to add vlans to bond0. The bonding works just fine if I comment out the VLANs and bridges. [/FONT][/COLOR]

[COLOR=#252523][FONT=Helvetica]Here are the configs attempted:[/FONT][/COLOR]

Version1
```

##Loopback
auto lo
iface lo inet loopback
 
auto bond0
iface bond0 inet static
#pre-up /sbin/ethtool -s bond0 speed 1000 duplex full autoneg on
post-up ifenslave bond0 eth0 eth2
pre-down ifenslave -d bond0 eth0 eth2
bond-slaves none
bond-mode 4
bond-lacp-rate fast
bond-miimon 100
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1
address 10.80.25.196
netmask 255.255.255.192
up route add -net 10.0.0.0/8 gw 10.80.25.193


#VLAN FOR MANAGEMENT
auto bond0.1439
iface bond0.1439 inet static
    address 10.80.207.198
    netmask 255.255.255.192
    gateway 10.80.207.193
    vlan-raw-device bond0
 
#BRIDGE FOR MANAGEMENT
auto cloudbr1439
iface cloudbr1439 inet manual
    bridge_ports bond0.1439
    bridge_fd 5
    bridge_stp off
    bridge_maxwait 1


#VLAN FOR FOR GUEST 
auto bond0.1891
iface bond0.1891 inet static
    address 10.81.153.134
    netmask 255.255.255.192
    gateway 10.81.153.129
    vlan-raw-device bond0
 
 
#BRIDGE FOR GUEST
auto cloudbr1891
iface cloudbr1891 inet manual
    bridge_ports bond0.1891
    bridge_fd 5
    bridge_stp off
    bridge_maxwait 1


#VLAN FOR STORAGE 
auto bond0.2213
iface bond0.2213 inet static
    address 10.81.119.134
    netmask 255.255.255.192
    gateway 10.81.19.129
    vlan-raw-device bond0
 
 
#BRIDGE FOR STORAGE
auto cloudbr2213
iface cloudbr2213 inet manual
    bridge_ports bond0.2213
    bridge_fd 5
    bridge_stp off
    bridge_maxwait 1


```
[COLOR=#252523][FONT=Helvetica]

Version2
[/FONT][/COLOR]```
##Loopback
auto lo
iface lo inet loopback


[COLOR=#252523][FONT=Helvetica]
[/FONT][/COLOR]auto bond0
iface bond0 inet static
#pre-up /sbin/ethtool -s bond0 speed 1000 duplex full autoneg on
post-up ifenslave bond0 eth0 eth2
pre-down ifenslave -d bond0 eth0 eth2
bond-slaves none
bond-mode 4
bond-lacp-rate fast
bond-miimon 100
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1
address 10.80.25.196
netmask 255.255.255.192
up route add -net 10.0.0.0/8 gw 10.80.25.193


#VLAN FOR MANAGEMENT
auto bond0.1439
allow-hotplug bond0.1439
iface bond0.1439 inet static
    address 10.80.207.198
    netmask 255.255.255.192
    gateway 10.80.207.193
    pre-up /etc/network/bondingstate UP bond0 1439
    pre-down /etc/network/bondingstate DOWN bond0 1439
 
#BRIDGE FOR MANAGEMENT
auto cloudbr1439
iface cloudbr1439 inet manual
    bridge_ports bond0.1439
    bridge_fd 5
    bridge_stp off
    bridge_maxwait 1




#VLAN FOR GUEST
auto bond0.1891
allow-hotplug bond0.1891
iface bond0.1891 inet static
    address 10.81.153.134
    netmask 255.255.255.192
    gateway 10.81.153.129
    pre-up /etc/network/bondingstate UP bond0 1891
    pre-down /etc/network/bondingstate DOWN bond0 1891
 
 
#BRIDGE FOR GUEST
auto cloudbr1891
iface cloudbr1891 inet manual
    bridge_ports bond0.1891
    bridge_fd 5
    bridge_stp off
    bridge_maxwait 1
 
#VLAN FOR STORAGE
auto bond0.2213
allow-hotplug bond0.2213
iface bond0.2213 inet static
    address 10.81.119.134
    netmask 255.255.255.192
    gateway 10.81.19.129
    pre-up /etc/network/bondingstate UP bond0 2213
    pre-down /etc/network/bondingstate DOWN bond0 2213
 
 
#BRIDGE FOR STORAGE
auto cloudbr2213
iface cloudbr2213 inet manual
    bridge_ports bond0.2213
    bridge_fd 5
    bridge_stp off
    bridge_maxwait 1


[COLOR=#252523][FONT=Helvetica]
[/FONT][/COLOR]
```[COLOR=#252523][FONT=Helvetica]


[/FONT][/COLOR]

---

