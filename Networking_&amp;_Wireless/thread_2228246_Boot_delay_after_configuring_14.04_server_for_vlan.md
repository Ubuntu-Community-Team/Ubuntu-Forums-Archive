---
title: "Boot delay after configuring 14.04 server for vlans"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by david226 on 2014-06-06
I have an Ubuntu 14.04 server that I've just configured to have a presence on each of 5 vlans.

When the message 'Starting configure virtual network devices' appears the boot process pauses and the message 'Waiting for network configuration' appears. A while later 'Waiting up to 60 more seconds for network configuration' appears and after another pause the boot process continues. The strange thing is that once the server is up and running everything appears to be working as it should. The server has its configured IP address on each of the vlans and responds on each of the vlans as it should. It's configured this way to be a dhcp server serving each of the vlans and it all works. So what's causing the delay in booting and, if the messages are correct, configuring the networking?

This is my interfaces file:

# The loopback network interface
auto lo
iface lo inet loopback


# configure vlans
auto em1.3 em1.4 em1.5 em1.7 em1.9


# configure bridge br0
auto br0
iface br0 inet static
address 10.10.10.20
network 10.10.10.0
netmask 255.255.255.0
gateway 10.10.10.1
dns-nameservers 10.10.10.1
vlan-raw-device em1
bridge_ports em1.3


# configure bridge br1
auto br1
iface br1 inet static
address 10.10.20.20
network 10.10.20.0
netmask 255.255.255.0
gateway 10.10.20.1
dns-nameservers 10.10.20.1
vlan-raw-device em1
bridge_ports em1.4


# configure bridge br2
auto br2
iface br2 inet static
address 10.30.0.20
network 10.30.0.0
netmask 255.255.0.0
gateway 10.30.0.1
dns-nameservers 10.30.0.1
vlan-raw-device em1
bridge_ports em1.5


# configure bridge br3
auto br3
iface br3 inet static
address 10.10.70.20
network 10.10.70.0
netmask 255.255.255.0
gateway 10.10.70.1
dns-nameservers 10.10.70.1
vlan-raw-device em1
bridge_ports em1.7


# configure bridge br9
auto br9
iface br9 inet static
address 10.10.99.20
network 10.10.99.0
netmask 255.255.255.0
gateway 10.10.99.1
dns-nameservers 10.10.99.1
vlan-raw-device em1
bridge_ports em1.9


# Secondary network interface
# standalone network: 10.10.98.0
# only for capturing mirrored traffic
auto p2p1
iface p2p1 inet static
address 10.10.98.20
network 10.10.98.0
netmask 255.255.255.0


Any help would be greatly appreciated.

David

---

### Post by eddy-beaupre on 2014-06-13
> **david226 said:**
> I have an Ubuntu 14.04 server that I've just configured to have a presence on each of 5 vlans.

When the message 'Starting configure virtual network devices' appears the boot process pauses and the message 'Waiting for network configuration' appears. A while later 'Waiting up to 60 more seconds for network configuration' appears and after another pause the boot process continues. The strange thing is that once the server is up and running everything appears to be working as it should. The server has its configured IP address on each of the vlans and responds on each of the vlans as it should. It's configured this way to be a dhcp server serving each of the vlans and it all works. So what's causing the delay in booting and, if the messages are correct, configuring the networking?

David


I have the same issue, here's my network configuration :

```

auto lo eth0 eth0.253
iface lo inet loopback

iface eth0 inet static
        address 10.139.4.250
        netmask 255.255.255.128
        hwaddress ether 00:02:46:00:3d:05

iface eth0.253 inet dhcp
        post-up /sbin/route add -net 10.139.0.0 netmask 255.255.0.0 gw 10.139.4.129 dev eth0 || true
        vlan-raw-device eth0

```

---

### Post by The Cog on 2014-06-13
I'm not sure about bridging so I could be talking rubbish here. But I have a machine here with 54 vlans, and it boots in seconds. Each vlan has its own IP address and is configured like this:
```
iface eth0.490 inet static
    address 10.7.33.113
    netmask 255.255.255.240
    [COLOR="#0000CD"]up ip route add default via 10.7.33.116 table 490
    up ip rule add priority 490 fwmark 0x490 table 490
    up ip route flush cache
    down ip rule del priority 490
    down ip route flush table 490[/COLOR]
```
You probably aren't using virtual routing tables so don't need most of this stuff (I've coloured it blue). So all you really need is the address and netmask. The raw device is taken from the interface.vlan name automatically. I don't have a stanza for eth0 at all in my config.

So you might be better off just configuring interfaces br0.3, br1.4, br2.5, br3.7 and br9.9. 
I think that the delay may be something trying to do dhcp but I'm not certain of that. You may need to run tcpdump on another machine to see if that's the case.

---

