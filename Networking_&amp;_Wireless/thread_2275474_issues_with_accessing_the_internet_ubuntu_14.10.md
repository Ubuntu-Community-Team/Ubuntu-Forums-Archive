---
title: "issues with accessing the internet ubuntu 14.10"
date: 2015-04-26
forum: Networking &amp; Wireless
---

### Post by KaSAndra on 2015-04-26
Hello everyone

i currently am having an issue with the networking on my machine 
i have a qemu-kvm virtual machine running and was trying to setup a network bridge and was following one of the many guides on the net on how to do bridged connections but failed which killed my internet connection
i have now tried to remove it all and restore the ethernet connection and i still dont have internet access even though i have an ip which i suppose it obtained from the router even though i cant ping the router

the output of ifconfig
```
eth0      Link encap:Ethernet  HWaddr 54:04:a6:46:a2:3b  
          inet addr:192.168.2.110  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::5604:a6ff:fe46:a23b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:839313 (839.3 KB)  TX bytes:159590 (159.5 KB)
          Interrupt:18 Memory:f9100000-f9120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:314642 (314.6 KB)  TX bytes:314642 (314.6 KB)

usb0      Link encap:Ethernet  HWaddr 02:55:52:04:63:39  
          inet addr:192.168.42.24  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::55:52ff:fe04:6339/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8888 errors:2 dropped:0 overruns:0 frame:2
          TX packets:8784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7105494 (7.1 MB)  TX bytes:1814129 (1.8 MB)


```

the usb0 is actually my samsung galaxy S5 being used for its internet connection which works

output from ping 192.168.2.1 (routers ip address)
```
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.110 icmp_seq=1 Destination Host Unreachable
From 192.168.2.110 icmp_seq=2 Destination Host Unreachable
From 192.168.2.110 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.2.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3015ms
pipe 3

```

output from route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     *               255.255.255.0   U     1      0        0 eth0

```

output from iptables -L
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain
ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootps
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:bootps

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

ACCEPT     all  --  anywhere             192.168.122.0/24     ctstate RELATED,ESTABLISHED
ACCEPT     all  --  192.168.122.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootpc

```

any ideas?

---

