---
title: "Host Unreachable from internal card"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by fiztlen on 2008-08-08
At the moment I'm trying to configure a gateway / firewall using Hardy Server.  I think I have the internal network setup (DHCP seems to work and if I ping by name it's resolved correctly), but I can't reach the internet from the internal network, including the corresponding card on the gateway (espresso).

```
root@espresso:/etc/shorewall# cat /proc/sys/net/ipv4/ip_forward
1

root@espresso:/etc/shorewall# ping -I eth1 www.google.com
PING www.l.google.com (64.233.161.99) from 192.168.1.4 eth1: 56(84) bytes of data.
64 bytes from od-in-f99.google.com (64.233.161.99): icmp_seq=1 ttl=241 time=22.7 ms
64 bytes from od-in-f99.google.com (64.233.161.99): icmp_seq=2 ttl=241 time=21.0 ms

--- www.l.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 21.051/21.912/22.774/0.874 ms

root@espresso:/etc/shorewall# ping -I eth0 64.233.161.99
PING 64.233.161.99 (64.233.161.99) from 192.168.2.1 eth0: 56(84) bytes of data.
From 192.168.2.1 icmp_seq=1 Destination Host Unreachable
From 192.168.2.1 icmp_seq=2 Destination Host Unreachable
From 192.168.2.1 icmp_seq=3 Destination Host Unreachable

--- 64.233.161.99 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4008ms, pipe 3
```

As you may've guessed, I'm using shorewall to configure iptables.  I temporarily opened everything (I think), no change in results:
```
root@espresso:/etc/shorewall# shorewall stop
Stopping Shorewall...
IP Forwarding Enabled
done.

root@espresso:/etc/shorewall# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

root@espresso:/etc/shorewall# !ping
ping -I eth0 64.233.161.99
PING 64.233.161.99 (64.233.161.99) from 192.168.2.1 eth0: 56(84) bytes of data.
From 192.168.2.1 icmp_seq=1 Destination Host Unreachable
```

I'm not at my box now, but 90% sure the default route is eth1, and I think I set a gateway of 192.168.1.1 on both interfaces.

I'm sure I'm missing something obvious, but haven't found the right search terms.

Thank you for any help / links / anything.  :confused:

---

