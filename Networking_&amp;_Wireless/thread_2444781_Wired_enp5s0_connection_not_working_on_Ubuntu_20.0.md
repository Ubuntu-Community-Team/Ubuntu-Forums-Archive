---
title: "Wired enp5s0 connection not working on Ubuntu 20.04"
date: 2020-06-04
forum: Networking &amp; Wireless
---

### Post by vasiauvi2 on 2020-06-04
Hi all,
The wireless connection works perfect on my Ubuntu 20.04 Dell laptop, but the wired connection doesn't.
The wire, the router or ISP provider works correctly because I've checked on an other laptop with Windows 10 without any issues. Even called the ISP provider and we came to the conclusion that the issue is from the Ubuntu.

What is strange is that if I disconnect and connect the wired con. the ping to 8.8.8.8 is working briefly and after that is going back again:

```
From 192.168.0.107 icmp_seq=1608 Destination Host UnreachableFrom 192.168.0.107 icmp_seq=1609 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1610 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1611 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1612 Destination Host Unreachable
64 bytes from 8.8.8.8: icmp_seq=1618 ttl=55 time=14.5 ms
64 bytes from 8.8.8.8: icmp_seq=1619 ttl=55 time=14.6 ms
64 bytes from 8.8.8.8: icmp_seq=1620 ttl=55 time=15.6 ms
64 bytes from 8.8.8.8: icmp_seq=1621 ttl=55 time=15.9 ms
64 bytes from 8.8.8.8: icmp_seq=1622 ttl=55 time=16.9 ms
From 192.168.0.107 icmp_seq=1623 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1624 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1625 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1626 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1627 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1628 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1630 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1631 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1632 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1633 Destination Host Unreachable
From 192.168.0.107 icmp_seq=1634 Destination Host Unreachable
```

What is also strange is why it takes the 192.168.0.107 IP when I change from the setting to 192.168.1.139?
Sometimes the *ifconfig* looks like this:

```
ifconfig enp5s0
enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.139  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::c695:1ece:7ed8:e930  prefixlen 64  scopeid 0x20<link>
        inet6 2a02:2f08:4914:9900:ef5a:e062:10cb:9c86  prefixlen 64  scopeid 0x0<global>
        inet6 2a02:2f08:4914:9900:8876:e515:af27:74bf  prefixlen 64  scopeid 0x0<global>
        inet6 2a02:2f08:4914:9900:30f8:b1ed:41c2:6f39  prefixlen 64  scopeid 0x0<global>
        inet6 2a02:2f08:4914:9900:4d6e:ad40:aa1c:d12  prefixlen 64  scopeid 0x0<global>
        inet6 2a02:2f08:4914:9900:5292:2037:9b19:5ad2  prefixlen 64  scopeid 0x0<global>
        ether 18:03:73:91:63:c4  txqueuelen 1000  (Ethernet)
        RX packets 30222  bytes 18873475 (18.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 32886  bytes 3674553 (3.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

sometimes like this:
```
ifconfig enp5s0
enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.107  netmask 255.255.255.0  broadcast 192.168.0.255
        ether 18:03:73:91:63:c4  txqueuelen 1000  (Ethernet)
        RX packets 30440  bytes 18904409 (18.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 33059  bytes 3690528 (3.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
I've run these commands:

```
sudo iptables -F
sudo ifdown enp5s0 && sudo ifup -v enp5s0
sudo gedit /etc/network/interfaces 
**with this config**:
auto lo
iface lo inet loopback


auto enp5s0
iface enp5s0 inet dhcp


#iface enp5s0 inet static
#    address 192.168.1.139
#    netmask 255.255.255.0
#    gareway 192.168.1.1
#    dns-nameservers 8.8.8.8

sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 05
       serial: 18:03:73:91:63:c4
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII
       resources: irq:17 ioport:d000(size=256) memory:f3204000-f3204fff memory:f3200000-f3203fff


```

UPDATE 1: I have Peppermint as dual boot with Ubuntu and in the first the wired connection is working perfectly.
UPDATE 2: the Ubuntu 20.04 is an upgrade from 19.10.

Does anyone have any clue what I could do next?
Thanks for reading and helping me.

---

