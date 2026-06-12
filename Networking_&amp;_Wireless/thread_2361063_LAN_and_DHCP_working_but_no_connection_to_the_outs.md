---
title: "LAN and DHCP working but no connection to the outside world!"
date: 2017-05-11
forum: Networking &amp; Wireless
---

### Post by gelo31415 on 2017-05-11
Dear All,

I have not used Linux/Ubuntu in several years and cant get the issue fixed with google alone. :confused:

I am trying to set up a basic server but it just cant communicate outside the network! I have invested several hours in trying to fix the issue, but so far I had little success. It is connected directly to my router and the connections on all other devices work as intended. :???:](*,)

Hope I can get some help here! Many thanks in advance!

Here are some infos on my Ubuntu Server 16.04.2 LTS configuration:

Interfaces:
```
 GNU nano 2.5.3         File: /etc/network/interfaces


source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto enp3s0
iface enp3s0 inet dhcp
netmask 255.255.255.0
gateway 192.168.0.1


```

pinging google.com: nothing happens. No error message.

Pinging googles IP:
```
ping 172.217.22.67
PING 172.217.22.67 (172.217.22.67) 56(84) bytes of data.

^C
--- 172.217.22.67 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7055ms

```

Pinging a LAN device:
```
ping 192.168.0.5
PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.
64 bytes from 192.168.0.5: icmp_seq=1 ttl=64 time=101 ms
64 bytes from 192.168.0.5: icmp_seq=2 ttl=64 time=3.04 ms
64 bytes from 192.168.0.5: icmp_seq=3 ttl=64 time=3.91 ms
64 bytes from 192.168.0.5: icmp_seq=4 ttl=64 time=3.19 ms
64 bytes from 192.168.0.5: icmp_seq=5 ttl=64 time=3.01 ms
64 bytes from 192.168.0.5: icmp_seq=6 ttl=64 time=3.36 ms
64 bytes from 192.168.0.5: icmp_seq=7 ttl=64 time=3.02 ms
64 bytes from 192.168.0.5: icmp_seq=8 ttl=64 time=3.22 ms
64 bytes from 192.168.0.5: icmp_seq=9 ttl=64 time=3.36 ms
64 bytes from 192.168.0.5: icmp_seq=10 ttl=64 time=2.98 ms
64 bytes from 192.168.0.5: icmp_seq=11 ttl=64 time=3.01 ms
64 bytes from 192.168.0.5: icmp_seq=12 ttl=64 time=3.19 ms
64 bytes from 192.168.0.5: icmp_seq=13 ttl=64 time=2.96 ms
^C
--- 192.168.0.5 ping statistics ---
13 packets transmitted, 13 received, 0% packet loss, time 12018ms
rtt min/avg/max/mdev = 2.966/10.722/101.084/26.086 ms

```

ifconfig and lshw -c network:
```

# ifconfig -a
enp3s0    Link encap:Ethernet  HWaddr 1c:1b:0d:b6:c8:68
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e1b:dff:feb6:c868/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:257452 (257.4 KB)  TX bytes:114169 (114.1 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:13392 (13.3 KB)  TX bytes:13392 (13.3 KB)

wlp2s0    Link encap:Ethernet  HWaddr f4:06:69:e1:a1:f9
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          
# sudo lshw -c network
  *-network DISABLED
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 83
       serial: f4:06:69:e1:a1:f9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-77-generic firmware=17.352738.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:315 memory:91300000-91301fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 15
       serial: 1c:1b:0d:b6:c8:68
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.0.9 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:312 ioport:e000(size=256) memory:91204000-91204fff memory:91200000-91203fff



```

---

### Post by chili555 on 2017-05-11
> source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto enp3s0
iface enp3s0 inet dhcp
netmask 255.255.255.0
gateway 192.168.0.1This is pretty confusing as you have specified some settings that are not needed if you want to connect with DHCP which, incidentally, I do not recommend. If you want to reach the server by ssh and ftp, you probably don't want an ever-changing IP address by D(ynamic)HCP.

I suggest that you amend the file to something like:```
source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto enp3s0
iface enp3s0 inet static
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8
```Restart the interface:```
sudo ifdown enp3s0 && sudo ifup -v enp3s0
```Did you connect?```
ping -c3 192.168.0.1
ping -c3 www.ubuntu.com
```

---

