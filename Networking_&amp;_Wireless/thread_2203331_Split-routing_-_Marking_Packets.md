---
title: "Split-routing - Marking Packets"
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by Juggler00 on 2014-02-02
I am looking to set-up split-routing on my Ubuntu server (12.04) and have it set such that http packets (port 80) exit out my default Ethernet interface, while all others use the VPN.

Before running the VPN, I see:
```
root@server:~$ netstat -rne
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
```When I run OpenVPN with the following flagged script:
```
--up /etc/openvpn/up.sh

root@server:~$ sudo cat /etc/openvpn/up.sh#!/bin/bash
#
# First it is necessary to disable Reverse Path Filtering on all
# current and future network interfaces:
#
for i in /proc/sys/net/ipv4/conf/*/rp_filter ; do
      echo 0 > $i
done

ip route flush table 4 
ip route add table 4 default via 192.168.2.1 dev eth0  metric 100 
ip route add table 4 192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.3 

iptables -t mangle -A PREROUTING -p tcp —-dport 80 -j MARK --set-mark 4
ip rule add fwmark 4 table 4
ip route flush cache
```I now see the two tables as expected:
```
root@rackserver:~$ netstat -rne
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.184.10.15      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 bond0
10.184.10.11    10.184.10.15      255.255.255.255 UGH   0      0        0 tun0
10.184.10.15    0.0.0.0         255.255.255.255 UH    0      0        0 tun0
109.201.154.200 192.168.2.1     255.255.255.255 UGH   0      0        0 bond0
128.0.0.0       10.184.10.15      128.0.0.0       UG    0      0        0 tun0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 bond0

root@server:~$ sudo ip route show table 4
default via 192.168.2.1 dev eth0  metric 100 
192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.3 
```However… this doesn’t seem to work. All web traffic is still being routed via my VPN rathern than my eth0 interface. Please help, I’ve been working on this for several days now and getting nowhere.

---

### Post by tomearp on 2014-02-03
> **Juggler00 said:**
> I now see the two tables as expected:
```
root@rackserver:~$ netstat -rne
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.184.10.15      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 bond0
10.184.10.11    10.184.10.15      255.255.255.255 UGH   0      0        0 tun0
10.184.10.15    0.0.0.0         255.255.255.255 UH    0      0        0 tun0
109.201.154.200 192.168.2.1     255.255.255.255 UGH   0      0        0 bond0
128.0.0.0       10.184.10.15      128.0.0.0       UG    0      0        0 tun0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 bond0

root@server:~$ sudo ip route show table 4
default via 192.168.2.1 dev eth0  metric 100 
192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.3 
```

The first route and the sixth route are directing all Internet-bound traffic over the VPN. The first route catches IP addresses in the range 0.0.0.0 - 127.255.255.255, the sixth route catches IP addresses in the range 128.0.0.0 - 255.255.255.255.

The third route will not get used because its metric is 100; the other two routes will take precedence as their metrics are 0.

---

