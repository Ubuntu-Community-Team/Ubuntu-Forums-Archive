---
title: "Network bonding with vlans and ping goes via lo instead of bond"
date: 2016-02-15
forum: Networking &amp; Wireless
---

### Post by BlackDex on 2016-02-15
Hello there,

I have a setup with 3 nics.
1 nic is used for management.
the other 2 are used for data/vdi.

The data/vdi nic's are bonded and on that bond are 2 vlan bonds.
So there is a bond0 which uses eth0 and eth1.
On that bond there are vlans on separate virtual-interfaces bond0.14 and bond0.15.
There are already other servers running on both vlans like the gateway and a few other servers, which all can communicate with each other without problems.

When i add an IP address via `ip addr add 192.168.14.10/24 dev bond0.14` and `ip addr add 192.168.15.10/24 dev bond0.15`
The IP's are nicely added and of course pingable on that host.

Now for some reason sometimes i can't ping the gateway on both vlan's which is located on .1.
I Also can't ping an other server on .5 (on both vlan's/subnets).

When ifdown/ifup the bond0.1[4|5] interface it sometimes does ping both the gateway and other server (after adding the IP again)

So i did some digging using tcpdump, and i found that when i couldn't ping the gateway or the other server the ping goes via the loopback instead of the correct bond0.xx device.
If i check `route -n` the route is correctly configured for that subnet.
When i check `arp` it shows it did check on the correct interface, but couldn't determine a MAC address.

Does anyone have a clue where to look? I find i strange that it pings on the loopback instead via the correct bond0.xx interface.

Thx in advance.

The interface config is like below, and i added the IP's as above for testing.
```

auto eth0
iface eth0 inet manual
    bond-lacp_rate slow
    bond-xmit_hash_policy layer2
    bond-miimon 100
    bond-master bond0
    mtu 1500
    bond-mode balance-tlb

auto eth1
iface eth1 inet manual
    bond-lacp_rate slow
    bond-xmit_hash_policy layer2
    bond-miimon 100
    bond-master bond0
    mtu 1500
    bond-mode balance-tlb

auto bond0
iface bond0 inet manual
    bond-lacp_rate slow
    bond-xmit_hash_policy layer2
    bond-miimon 100
    mtu 1500
    bond-mode balance-tlb
    hwaddress xx:xx:xx:xx:xx:xx
    bond-slaves none

auto bond 0.14
iface bond0.14 inet manual
    vlan-raw-device bond0
    mtu 1500
    vlan_id 14

auto bond 0.15
iface bond0.15 inet manual
    vlan-raw-device bond0
    mtu 1500
    vlan_id 15

```

---

### Post by BlackDex on 2016-03-04
I have solved this a while ago.
The problem lied in a switch configuration which wasn't under my control.
So after the switch config update it was fixed.

---

