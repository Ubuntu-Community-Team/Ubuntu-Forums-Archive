---
title: "Omit gateway for second network interface in /etc/network/interfaces"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by bernievoigt on 2008-11-26
Hi!

I'm trying to setup my routing properly but can't figure out how to do it in /etc/network/interfaces. Here's my configuration:

```
# local lookup
iface lo inet loopback

# dhcp from dsl router
auto eth1
iface eth1 inet dhcp

# local network between this and another host
auto eth2
iface eth2 inet static
      address 192.168.1.11
      netmask 255.255.255.0
      network 192.168.1.0

```
The resulting routing is:
```
$ route -en
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt
 Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2
10.0.2.0        0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         192.168.1.11    0.0.0.0         UG        0 0          0 eth2
0.0.0.0         10.0.2.2        0.0.0.0         UG        0 0          0 eth1
```

I'd like to get rid of the default gateway entry for the eth2 interface as this is just a local network. The eth1 interface and gateway route is my outbound internet connection. Having the two gateway entries in the routing table kills my internet connectivity. I have to delete the eth2 gateway route manually to get it back. Is there a way to omit the default gateway definition which seems to be added automatically, when left out in /etc/network/interfaces.

Thanks for help! Bernhard

---

### Post by SpaceTeddy on 2008-11-26
i've never seen this behaviour before. If the gateway is ommited in the interfaces, then it will not set one (at least that's what it does on my servers... ). Also, why does it set itself as default gateway - this does not make much sense. 

Is it possible that you are still pulling some gateway information via dhcp from somehwere else ? If you unplug all network cables and reboot the machine, does this entry still persist ?

:confused:

---

### Post by bernievoigt on 2008-11-26
An additional issue came up... There is also the problem that the start of the eth2 interface seems to overwrite the resolve information. To remedy the situation after /etc/init.d/networking start, I issue the following commands:
```

ifdown eth2 && ifup eth2 && ifdown eth1 && ifup eth1 && \
route del -net 0.0.0.0 gw 192.168.1.11 

```
In this case the eth1 dhcp information about nameservers comes in after the start of eth2. However, I still need to delete the default route for eth2.

Thanks again for any help! Bernhard

---

