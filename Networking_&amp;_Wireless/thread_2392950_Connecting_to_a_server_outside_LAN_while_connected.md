---
title: "Connecting to a server outside LAN while connected to the VPN"
date: 2018-05-27
forum: Networking &amp; Wireless
---

### Post by raac on 2018-05-27
Hi all,

I can't seem to connect to my server using tcp protocol while the server is connected to a VPN. I've done plenty of research and tried to troubleshoot my issue, and I haven't had success. I did a small program that opens a tcp socket on a given port and listens for connection. I CAN make a connection while the server is NOT connected to the VPN from outside the LAN. However, once it connects to the VPN, the client times out. Based on some research, it sounds like server is trying to use the VPN interface during the response.
This is what I have done.

I added this entry in /etc/iproute2/rt_tables

```
85      special
```

Before the server connects to the VPN, it executes the following commands

```

ip route add default via 192.168.1.1 dev eno1 table 85
ip rule add fwmark 0x44 table 85


```

I added a couple of iptable rules

```

sudo iptables -t mangle -S

-P PREROUTING ACCEPT
-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-P POSTROUTING ACCEPT
-A PREROUTING -i eno1 -m conntrack --ctstate NEW -j CONNMARK --set-xmark 0x4d2/0xffffffff
-A OUTPUT -m connmark --mark 0x4d2 -j MARK --set-xmark 0x44/0xffffffff



```

The iptables chains look like this

```


sudo iptables -t mangle -L -v

Chain PREROUTING (policy ACCEPT 221K packets, 482M bytes)
 pkts bytes target     prot opt in     out     source               destination
 1665  472K CONNMARK   all  --  eno1   any     anywhere             anywhere             ctstate NEW CONNMARK set 0x4d2


Chain INPUT (policy ACCEPT 221K packets, 482M bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 109K packets, 589M bytes)
 pkts bytes target     prot opt in     out     source               destination
10133  339M MARK       all  --  any    any     anywhere             anywhere             connmark match  0x4d2 MARK set 0x44


Chain POSTROUTING (policy ACCEPT 110K packets, 589M bytes)
 pkts bytes target     prot opt in     out     source               destination



```

The route table looks like this

```

sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.59.10.5      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eno1
10.59.10.1      10.59.10.5      255.255.255.255 UGH   0      0        0 tun0
10.59.10.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
128.0.0.0       10.59.10.5      128.0.0.0       UG    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eno1
192.168.1.1     0.0.0.0         255.255.255.255 UH    100    0        0 eno1
198.8.80.180    192.168.1.1     255.255.255.255 UGH   0      0        0 eno1



```

The route for the new table looks like this

```

ip route show table special
default via 192.168.1.1 dev eno1

```

I also tried the following and no luck

```

sudo sysctl -w net.ipv4.tcp_fwmark_accept=1

```

Ubuntu server: 18.04
Kernel: 4.15.0-22-generic

Any help would be appreciated.

---

### Post by TheFu on 2018-05-28
Sounds like a routing issue.

What are the LAN IPs for both the client and the server? How do you expect to connect? Which protocol?

My openvpn server routes between the outside VPN clients and all boxed on the intoernal LANs.  That routing is setup in the vpn-server.conf file, in my setup.   For LAN clients talking to each other, the VPN has  nothing to do with anything, at least in my config.

---

