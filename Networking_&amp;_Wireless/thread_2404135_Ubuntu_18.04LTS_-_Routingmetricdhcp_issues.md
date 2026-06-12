---
title: "Ubuntu 18.04LTS - Routing/metric/dhcp issues"
date: 2018-10-20
forum: Networking &amp; Wireless
---

### Post by mr-c2 on 2018-10-20
I have a Lenovo P410 workstation where I run Ubuntu 18.04LTS and SoftEther VPN-server. I have in total 5 network interfaces - one on the motherboard and four through a Intel-based PCIE-card.
For my VPN-server, I want the incoming connections (and internet access for the system itself in general) to come through eno0, so lets call this the "main" interface. In addition there is the ens3f0|1|2|3 on the network card acting as "sources" for different hubs (which had different purposes).


In addition to eno0, I the 4-port network card have a mix of connections:
ens3f0: A bridge to the same network as ETH0 and ens3f1 where the same router provides an IP (e.g. 192.168.1.x over DHCP)
ens3f1: A bridge to the same network as ETH0 and ens3f0 where the same router provides an IP (e.g. 192.168.1.x over DHCP)
ens3f2: Connected to a different network, which over dhcp delivers a public ip (so direct connection to the internet).
ens3f3: Connected to a different network, which over dhcp delivers a public ip (so direct connection to the internet).


So, I want incoming connections on eno0. Also, when the system itself access the internet, I want this connection to be used. When I first did the install, this was the only interface that had an connection.


ifconfig printout:
> 
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST> mtu 1500
inet 192.168.1.109 netmask 255.255.255.0 broadcast 192.168.1.255
ether 6c:0b:84:e2:7c:a6 txqueuelen 1000 (Ethernet)
RX packets 823457 bytes 66366883 (66.3 MB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 384757 bytes 36716871 (36.7 MB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0
device interrupt 20 memory 0xfb500000-fb520000


ens3f0: flags=4419<UP,BROADCAST,RUNNING,PROMISC,MULTICAST> mtu 1500
inet 192.168.1.191 netmask 255.255.255.0 broadcast 192.168.1.255
ether f4:ce:46:a6:ef:dc txqueuelen 1000 (Ethernet)
RX packets 2482593 bytes 385314548 (385.3 MB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 1279581 bytes 66591362 (66.5 MB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0
device memory 0xfb280000-fb2fffff


ens3f1: flags=4419<UP,BROADCAST,RUNNING,PROMISC,MULTICAST> mtu 1500
inet 192.168.1.192 netmask 255.255.255.0 broadcast 192.168.1.255
ether f4:ce:46:a6:ef:dd txqueuelen 1000 (Ethernet)
RX packets 2480815 bytes 385172870 (385.1 MB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 1277175 bytes 66492929 (66.4 MB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0
device memory 0xfb200000-fb27ffff


ens3f2: flags=4419<UP,BROADCAST,RUNNING,PROMISC,MULTICAST> mtu 1500
inet XX.XX.XX.XX netmask 255.255.255.0 broadcast XX.XX.XX.255
ether f4:ce:46:a6:ef:de txqueuelen 1000 (Ethernet)
RX packets 184602 bytes 14416240 (14.4 MB)
RX errors 0 dropped 17 overruns 0 frame 0
TX packets 134340 bytes 11552772 (11.5 MB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0
device memory 0xfb180000-fb1fffff


ens3f3: flags=4419<UP,BROADCAST,RUNNING,PROMISC,MULTICAST> mtu 1986
inet XX.XX.XX.XX netmask 255.255.255.0 broadcast XX.XX.XX.255
ether f4:ce:46:a6:ef:df txqueuelen 1000 (Ethernet)
RX packets 636746 bytes 75801968 (75.8 MB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 736989 bytes 106662664 (106.6 MB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0
device memory 0xfb100000-fb17ffff


lo: flags=73<UP,LOOPBACK,RUNNING> mtu 65536
inet 127.0.0.1 netmask 255.0.0.0
loop txqueuelen 1000 (Local Loopback)
RX packets 77061 bytes 7536918 (7.5 MB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 77061 bytes 7536918 (7.5 MB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0


Since ip-ranges/gateway etc. will be the same here on some networks, setting the routes will not help. So 


route -n printout:
> Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 XX.XX.XX.1 0.0.0.0 UG 100 0 0 ens3f3
0.0.0.0 192.168.1.1 0.0.0.0 UG 101 0 0 eno1
0.0.0.0 192.168.1.1 0.0.0.0 UG 102 0 0 ens3f0
0.0.0.0 192.168.1.1 0.0.0.0 UG 103 0 0 ens3f1
0.0.0.0 XX.XX.XX.1 0.0.0.0 UG 104 0 0 ens3f2
XX.XX.XX.0 0.0.0.0 255.255.255.0 U 100 0 0 ens3f3
XX.XX.XX.0 0.0.0.0 255.255.255.0 U 101 0 0 ens3f2
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 ens3f3
192.168.1.0 0.0.0.0 255.255.255.0 U 99 0 0 eno1
192.168.1.0 0.0.0.0 255.255.255.0 U 100 0 0 ens3f1
192.168.1.0 0.0.0.0 255.255.255.0 U 101 0 0 ens3f0
192.168.1.0 0.0.0.0 255.255.255.0 U 102 0 0 eno1

So i tried chaning the metric with 'ifmetric', which seems to help temporarily. E.g. for some reason ens3f3 get metric 100, but I want eno0 to have it. So e.g. I can set metric to 99 for eno1, and it works for a while before reverting to the old setting. I can see in syslog that this interface do a dhcp-request quite often - like just under every 10th minute. I seen the lease time is noted in syslog as 'lease time 1200', which is 20 minutes.


Example from syslog:
> 
Oct 20 11:20:08 SE-L2-VPN NetworkManager[724]: <info> [1540027208.8204] dhcp4 (ens3f3): nameserver 'YYY.YYY.YY.253'
Oct 20 11:20:08 SE-L2-VPN NetworkManager[724]: <info> [1540027208.8204] dhcp4 (ens3f3): nameserver 'ZZZ.ZZZ.ZZ.253'
Oct 20 11:20:08 SE-L2-VPN NetworkManager[724]: <info> [1540027208.8204] dhcp4 (ens3f3): domain name 'QQQ.QQQQQQQQQ.com'
Oct 20 11:20:08 SE-L2-VPN NetworkManager[724]: <info> [1540027208.8205] dhcp4 (ens3f3): state changed bound -> bound
Oct 20 11:20:08 SE-L2-VPN systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct 20 11:20:08 SE-L2-VPN dbus[709]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 20 11:20:08 SE-L2-VPN systemd[1]: Started Network Manager Script Dispatcher Service.
Oct 20 11:20:08 SE-L2-VPN nm-dispatcher: req:1 'dhcp4-change' [ens3f3]: new request (1 scripts)
Oct 20 11:20:08 SE-L2-VPN nm-dispatcher: req:1 'dhcp4-change' [ens3f3]: start running ordered scripts...
Oct 20 11:20:08 SE-L2-VPN dhclient[22366]: bound to XX.XX.XX.22 -- renewal in 578 seconds.
Oct 20 11:29:46 SE-L2-VPN dhclient[22366]: DHCPREQUEST of XX.XX.XX.22 on ens3f3 to XX.XX.XX.1 port 67 (xid=0x3341cae3)
Oct 20 11:29:46 SE-L2-VPN dhclient[22366]: DHCPACK of XX.XX.XX.22 from XX.XX.XX.1
Oct 20 11:29:46 SE-L2-VPN NetworkManager[724]: <info> [1540027786.4694] dhcp4 (ens3f3): address XX.XX.XX.22
Oct 20 11:29:46 SE-L2-VPN NetworkManager[724]: <info> [1540027786.4694] dhcp4 (ens3f3): plen 24 (255.255.255.0)
Oct 20 11:29:46 SE-L2-VPN NetworkManager[724]: <info> [1540027786.4694] dhcp4 (ens3f3): gateway XX.XX.XX.1
Oct 20 11:29:46 SE-L2-VPN dbus[709]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'




In addition, the ens3f2 interface looses ip-lease. If I use ifconfig to take the interface down and then up again, it gets an ip - but after a while that interface is without an ip-address again (it gets the IP from the same "source" and ens3f3. Also, the router which ens0, ens3f0 and ens3f1 is connected to, also receive this IP from the same place (router ens0/ens3f0/ens3f1 is connected to, is connected to a FTTH-connection. ens3f2 and ens3f3 is also connected to FTTH-connections, but different once - so yeah, three different FTTH-connections in play here - all with the same path in the ISP-network). 

So, main issue: How to I get the ens0 to be the "default" interface? I hope this can fix some of the other issues. I suspect ens3f2 looses IP because of the L2 VPN-server when there is no connection (...device...) connected to that interface. I suspect ens3f3 can get the same problem when ens0 have taken over its role.

---

### Post by mr-c2 on 2018-10-23
Ok, I solved some of the issues. 

* I noticed the system was not running 18.04LTS, but 17.10. When doing a release-upgrade to 18.04LTS, I ran into some SecureBoot-issues, and just did a reinstall. With a fresh install, the dhcp-issue is gone.
* The metric-issue seems now to be solved by specifying metric-value in /etc/network/interfaces.

Now I get this:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eno1
0.0.0.0         192.168.1.1     0.0.0.0         UG    102    0        0 ens3f1
0.0.0.0         XX.XX.XX.1      0.0.0.0         UG    103    0        0 ens3f2
0.0.0.0         XX.XX.XX.1      0.0.0.0         UG    104    0        0 ens3f3
XX.XX.XX.0      0.0.0.0         255.255.255.0   U     0      0        0 ens3f3
XX.XX.XX.0      0.0.0.0         255.255.255.0   U     0      0        0 ens3f2
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ens3f1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ens3f0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1
```


XX.XX.XX = My public IPs gateway/destination. All interfaces get ip through dhcp.

And I guess my limited understanding of routing might be an issue here. Everything seems to be working fine for eno1. The VPN-server software will use the other interfaces will be bridged to the VPN-server. But I need to look into asymetrical routing for this to work?

---

