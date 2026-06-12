---
title: "Routing issue"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by JasonLund on 2008-05-28
I have setup a router to replace our old cisco that was running with two 10 half duplex ports.  This connects the town network to the school network.  I setup the routing tables and everything was working until Nagios started to complain that it could not see (ping) the town switch. I can ping the switch (192.168.2.11) from the town side and from the router, but I cannot ping it from any computer on any of the subnets on the school side.  I can ping other town devices from the school side and Nagios can find the Town Servers which are on the same subnet (192.168.2.xxx). I did find one printer that I cannot ping from the school side as well.  The only thing I can find that ties the switch and printer together is that their ping times are slow with +7 milliseconds.  The other devices that I can ping from the school side seem to be under 1 millisecond.  Is there a setting that prevents routing any traffic if there is a slow network response?

I have verified that iptables is allowing everything through INPUT, FORWARD and OUTPUT and ifw is not running.  I know that the netmask is set correctly since I can ping ip address both below and above both the switch and printer.  Any thoughts?

---

### Post by SpaceTeddy on 2008-05-29
i don't know if i understand your setup right... can you please draw a pitcure of it. That usually helps me understand things better :)

At first glance, i would say that you are missing routes somewhere... but there is no telling for sure - of course :(

---

### Post by JasonLund on 2008-06-02
Here is a quick rendition:
[IMG]http://capenet.cape.k12.me.us/~jason_lund/ubuntunetwork.gif[/IMG]

The issue is that anything from the school networks (ie the 172.21.xxx.xxx network or any other school network like 172.19.xxx.xxx) cannot see the two devices at 192.168.2.60 and 192.168.2.13.  Though they can easily see and interact with the devices at 192.168.2.1, 192.168.2.40 and 192.168.2.108.  The machines on the 192.168.2.xxx network can see the two devices and interact with them without issue.  The only difference I can find is that the two devices have long ping times.  Here is an example:

```
PING 192.168.2.60 (192.168.2.60): 56 data bytes
64 bytes from 192.168.2.60: icmp_seq=0 ttl=64 time=8.232 ms
64 bytes from 192.168.2.60: icmp_seq=1 ttl=64 time=6.718 ms
64 bytes from 192.168.2.60: icmp_seq=2 ttl=64 time=6.789 ms
64 bytes from 192.168.2.60: icmp_seq=3 ttl=64 time=6.772 ms
64 bytes from 192.168.2.60: icmp_seq=4 ttl=64 time=6.642 ms
64 bytes from 192.168.2.60: icmp_seq=5 ttl=64 time=6.663 ms
64 bytes from 192.168.2.60: icmp_seq=6 ttl=64 time=6.923 ms
^C
--- 192.168.2.60 ping statistics ---
7 packets transmitted, 7 packets received, 0% packet loss
round-trip min/avg/max/stddev = 6.642/6.963/8.232/0.525 ms
```

This was from my machine on the 192.168.2.xxx network.  The other device has equally long ping times.  The other three devices are comming in under 1 millisecond.  Final note, the ubuntu server can ping the two devices.

---

### Post by SpaceTeddy on 2008-06-03
mhm - can you show me the routing table of one of the non-working clients, one of the working clients are the ubuntu server, please. I still think this is a routing issue. The only other explanations would be hard-fault, which would make no sense since two devices usually don't fail at the same time. 

You can get the routing table on a windows machine with
```
route print
```
and on a linux with
```
route -n
```

thanks :)

---

### Post by JasonLund on 2008-06-05
Here is the routing table from a non-working machine (Nagios - 172.21.1.6):

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
172.21.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth0
127.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 lo
0.0.0.0         172.21.0.254    0.0.0.0         UG    0      0        0 eth0

```

Here is the netstat -rn from my woring mac from the 192.168.2.xxx network:

```
Internet:
Destination        Gateway            Flags    Refs      Use  Netif Expire
default            192.168.2.1        UGSc      100       24    en1
127                127.0.0.1          UCS         0        0    lo0
127.0.0.1          127.0.0.1          UH          1        2    lo0
169.254            link#6             UCS         0        0    en1
192.168.2          link#6             UCS         8        0    en1
192.168.2.1        0:40:10:14:53:46   UHLW       97       24    en1   1089
192.168.2.2        0:1:2:69:79:84     UHLW        2        0    en1   1199
192.168.2.57       0:20:4a:68:46:56   UHLW        0        0    en1   1142
192.168.2.108      0:17:a4:8b:31:3c   UHLW        3    14957    en1   1194
192.168.2.123      0:16:76:a7:c4:27   UHLW        0        1    en1   1192
192.168.2.161      127.0.0.1          UHS         0        0    lo0
192.168.2.163      0:d:93:40:a9:50    UHLW        0        0    en1    867
192.168.2.250      0:c:f1:fa:c1:51    UHLW        0      122    en1    988
192.168.2.255      link#6             UHLWb       2       61    en1

```

The routing table for the Ubuntu Server is:

```

Destination      Gateway          Genmask           Flags    Metric    Ref     Use   Iface
192.168.2.0      0.0.0.0          255.255.255.0     U        0           0       0    eth0
172.24.0.0       172.21.0.254     255.255.0.0       UG       0           0       0    eth1
172.25.0.0       172.21.0.254     255.255.0.0       UG       0           0       0    eth1
172.18.0.0       172.21.0.254     255.255.0.0       UG       0           0       0    eth1
172.19.0.0       172.21.0.254     255.255.0.0       UG       0           0       0    eth1
172.16.0.0       172.21.0.254     255.255.0.0       UG       0           0       0    eth1
172.17.0.0       172.21.0.254     255.255.0.0       UG       0           0       0    eth1
172.22.0.0       172.21.0.254     255.255.0.0       UG       0           0       0    eth1
172.23.0.0       172.21.0.254     255.255.0.0       UG       0           0       0    eth1
172.20.0.0       172.21.0.254     255.255.0.0       UG       0           0       0    eth1
172.21.0.0       0.0.0.0          255.255.0.0       U        0           0       0    eth1
0.0.0.0          192.168.2.1      0.0.0.0           UG       100         0       0    eth0
0.0.0.0          172.21.0.254     0.0.0.0           UG       100         0       0    eth1

```

---

