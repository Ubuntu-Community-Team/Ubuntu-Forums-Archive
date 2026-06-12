---
title: "Triple NIC gateway issues"
date: 2014-07-24
forum: Networking &amp; Wireless
---

### Post by kritt on 2014-07-24
Triple NIC config:
p6p4: public IP
em1: behind router private IP (NAT)
em2: behind router private IP (NAT)

With the current settings, all NICs can ping their gateways through ping -I. Only p6p4 can ping public IPs (8.8.8.8). 
If I comment out the p6p4 gateway line and I uncomment the em1, em1 can ping 8.8.8.8 but p6p4 can't. 
How can I ping public IPs from both interfaces? Any advise would be greatly appreciated!

interfaces:
```
auto p6p4
iface p6p4 inet static
        address 82.x.x.x
        netmask 255.255.x.x
        gateway 82.x.x.x


auto em1
iface em1 inet static
        address 192.168.207.11
        netmask 255.255.255.0
        network 192.168.207.0
        dns-nameservers x.x.x.x x.x.x.x
        #gateway 192.168.207.1
        up route add -net 192.168.207.0 netmask 255.255.255.0 gw 192.168.207.1 dev em1


auto em2
iface em2 inet static
        address 192.168.208.11
        netmask 255.255.255.0
        network 192.168.208.0
        dns-nameservers x.x.x.x x.x.x.x
        up route add -net 192.168.208.0 netmask 255.255.255.0 gw 192.168.208.1 dev em2
        up route add -net 224.0.0.0/8 dev em2
```


route -n
```
[FONT=tahoma]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         82.102.93.77    0.0.0.0         UG    0      0        0 p6p4
82.102.93.76    0.0.0.0         255.255.255.252 U     0      0        0 p6p4
192.168.207.0   192.168.207.1   255.255.255.0   UG    0      0        0 em1
192.168.207.0   0.0.0.0         255.255.255.0   U     0      0        0 em1
192.168.208.0   192.168.208.1   255.255.255.0   UG    0      0        0 em2
192.168.208.0   0.0.0.0         255.255.255.0   U     0      0        0 em2
224.0.0.0       0.0.0.0         255.0.0.0       U     0      0        0 em2[/FONT]
```

//edit: I've tried a couple of solutions that I've found, using a table and adding ip route/rules for traffic originating from  em1 IPs without avail.

---

### Post by sedawk on 2014-07-24
To simplify the matter lets say that your computer needs a unique way to reach 8.8.8.8 and you cannot
tell him to use either p6p4 or em1 as he likes. You have to tell him which to use. That is what your routing
table does - it tells your PC how to reach 8.8.8.8.
(Basically option "-I" is only useful for local stuff, not for pinging an IP behind gateways because that always
 involved gateways).
If you want to achieve something like load balancing or failsafe redundancy, these are more advanced network techniques ...

---

### Post by kritt on 2014-07-24
sedawk thank you for your reply. 
My goal is to be able to have SSH access to the server via both em1 and p6p4 from outside the local network. As with pinging, SSH works towards p6p4 when it's got the default gateway and it works for em1 when it has the default gateway, but in both cases the other interface is unreachable from outside.

//edit: I understand what a default gateway is and that fundamentally there can't be two. I'm sure there's a solution to this, most possibly using a table to define which packets should be routed through the secondary interface.

---

