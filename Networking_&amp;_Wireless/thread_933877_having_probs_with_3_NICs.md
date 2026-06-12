---
title: "having probs with 3 NICs"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by wachaca on 2008-09-29
Hello,
I have a Ubuntu 8.06 LTS which I installed 3 network cards.
All 3 cards are recognized by the system.

For now I have given them all static IP addresses within the same network. 
This is the interfaces file
> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0
iface eth0 inet static
address 172.16.0.178
netmask 255.255.255.0
network 172.16.0.0
broadcast 172.16.0.255

auto eth1
iface eth1 inet static
address 172.16.0.11
netmask 255.255.255.0
network 172.16.0.0
broadcast 172.16.0.255

auto eth2
iface eth2 inet static
address 172.16.0.12
netmask 255.255.255.0
network 172.16.0.0
broadcast 172.16.0.255


I currently have ETH0 and ETH1 connected to the network, but ALL 3 IP address respond to PING!
When I unplug ETH0, NONE of the 3 IPs respond.
When I unplug ETH1, ALL 3 still repond.

When I assign ETH1 an IP of another network (192.168.168.20) and try to ping it, it does not respond (I can ping other machines in that network and I did switch the cable to the other switch).

ifconfig returns the following
> eth0      Link encap:Ethernet  HWaddr 00:01:80:4b:f7:77
          inet addr:172.16.0.178  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:80ff:fe4b:f777/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16593 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:19287018 (18.3 MB)  TX bytes:1621829 (1.5 MB)
          Interrupt:20 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:1e:58:a6:ca:5e
          inet addr:172.16.0.11  Bcast:172.16.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28242 (27.5 KB)  TX bytes:2340 (2.2 KB)
          Interrupt:18 Base address:0x8000

eth2      Link encap:Ethernet  HWaddr 00:1e:58:a6:d2:6a
          inet addr:172.16.0.12  Bcast:172.16.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:616 (616.0 B)  TX bytes:616 (616.0 B)


Where am I going wrong?
Why is ETH0 capturing all the packets?

:confused:

Thanks

---

