---
title: "Enabling a second network interface causes the first to stop working?"
date: 2016-07-05
forum: Networking &amp; Wireless
---

### Post by nbutlerimax on 2016-07-05
Hi all.

Not sure where I'm going wrong here, but I can't get multiple NIC's to work on my virtual Ubuntu 16.04 server. The virtual network interfaces are on different VLANs, so the server should pick up 2 different IP's on different networks.

I have 2 virtual network interfaces connected to the VM. When I start up the server, only 1 NIC was configured in /etc/network/interfaces:
```

source /etc/network/interfaces.d/*

#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto ens160
iface ens160 inet static
      address 192.168.5.10
      netmask 255.255.255.128
      gateway 192.168.5.1
      broadcast 192.168.5.127
      dns-nameservers 192.168.5.20


```

I have also confirmed that it will pick up an address on DCHP, but I wan't the static address configured..

So, having confirmed that I can ping the server from another workstation on that address, and I can ping from the server to the workstation OK, I then edit the interfaces file again to enable the other interface:
```

source /etc/network/interfaces.d/*

#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto ens160
iface ens160 inet static
      address 192.168.5.10
      netmask 255.255.255.128
      gateway 192.168.5.1
      broadcast 192.168.5.127
      dns-nameservers 192.168.5.20

#The secondary network interface
auto ens192
iface ens192 inet dhcp

```

Just to confirm, in case you're wondering, I got the interface names from the following:
```

dmesg | grep -i eth
(truncated reply):
eth0: NIC link is Up 10000 Mbps
eth1: NIC link is Up 10000 Mbps
ens160: renamed from eth0
ens192: renamed from eth1

```

So, I reboot the server and check ifconfig. The server has an IP on both interfaces. This is where things get a bit weird.
```

#FROM THE SERVER:
ping -I ens160 google.com
PING google.com (203.5.76.208) from 192.168.5.10 ens160: 56(84) bytes of data
64 bytes from cache.google.com (203.5.76.208): icmp_seq=1 ttl=56 time=1.46ms

ping -I ens192 google.com
PING google.com (203.5.76.208) from 192.168.7.10 ens160: 56(84) bytes of data
From 192.168.7.10 icmp_seq=1 Destination Host Unreachable
From 192.168.7.10 icmp_seq=2 Destination Host Unreachable
From 192.168.7.10 icmp_seq=3 Destination Host Unreachable

```

But then I try to ping the server from another workstation:
```

$ ping 192.168.5.10
PING 192.168.5.10 (192.168.5.10): 56 data bytes
Request timeout for icmp_seq 0
Request timeout for icmp_seq 1
Request timeout for icmp_seq 2
^C
--- 192.168.5.10 ping statistics ---
4 packets transmitted, 0 packets received, 100.0% packet loss



$ ping 192.168.7.10
PING 192.168.7.10 (192.168.7.10): 56 data bytes
64 bytes from 192.168.7.10: icmp_seq=0 ttl=64 time=0.387 ms
64 bytes from 192.168.7.10: icmp_seq=1 ttl=64 time=0.405 ms
64 bytes from 192.168.7.10: icmp_seq=2 ttl=64 time=0.439 ms
^C
--- 192.168.7.10 ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.387/0.410/0.439/0.022 ms



```


So, after enabling the second NIC on the server:
[LIST]
[*]I can ping out from the server on the ens160 interface
[*]I can't ping the server from a workstation to the ens160 interface
[*]I can't ping out from the server on the ens192 interface
[*]I can ping the server from a workstation to the ens192 interface
[/LIST]


So, does anyone have any ideas about where I am getting stuck and how to resolve this? Other posts I've looked at mention IP Routes, but I'm not very experienced with them, and couldn't get my head around the replied people were posting.

Thanks in advance!
Nathan

---

### Post by TheFu on 2016-07-06
It is a routing issue.

Outbound routes and probably inbound routes from the other machines.  If they don't know how to get to the specific IP, then it won't transit. In multi-NIC setups, the defaults are not sufficient. Manual routing is likely required except for the simplest needs.

Also, vlans have NOTHING to do with this. VLANs provide a logical separation only. The interfaces are on different subnets, hence the routing issues.  No way to help with the information provided. Would need the routing table from this machine and both the routing tables AND the subnet/ip information from the other machines trying to get back in.  Routing is a two-way problem. If you don't control the network used by the other systems, you cannot solve half the issue.

You will need more knowledge about routing to make this work, probably.

---

