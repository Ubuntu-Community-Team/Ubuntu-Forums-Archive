---
title: "Question about KVM routing"
date: 2016-02-05
forum: Networking &amp; Wireless
---

### Post by Bashed on 2016-02-05
I have KVM host (Centos) and created an Ubuntu 14 server VM. I have a bunch of IPs routed on the switch to the KVM host VLAN, so that's set.

Problem is, I can't seem to get the IPs on the VM guest (Ubuntu server) pinging. I'm told by lousy support at Solusvm that I need to bind the subnets to the *HOST* KVM. Then someone else tells me they should not be bound on the host, but the VM guest itself. Could use some help here.

I'm told I need to assign a handful of /27 subnets to my KVM host node (Centos 6). I routed them correctly at the Cisco switch, so that's all go. I need to know for sure, on KVM host are IPs bound there or only and strictly the guest VM?

Traceroute & ping works fine on gateway on each subnet, but not on the public IPs.

I tried this method, didn't work.
[http://www.ducea.com/2006/07/15/linux-tips-how-to-quickly-bind-a-range-of-ips-on-redhat-based-systems/](http://www.ducea.com/2006/07/15/linux-tips-how-to-quickly-bind-a-range-of-ips-on-redhat-based-systems/)

I created ifcfg-eth0-range1, added below and restarted network. Still can't ping public IPs.

```
IPADDR_START=xx.xx.98.66  
IPADDR_END=xx.xx.98.90    
CLONENUM_START=0
```

The /27 subnets are already assigned to the Ubuntu KVM VM itself. 

Even MTR doesn't work

```
$ mtr --no-dns -rw xx.xx.42.188
Start: Fri Feb 5 16:42:14 2016
HOST: castle Loss% Snt Last Avg Best Wrst StDev
1.|-- 192.168.88.1 0.0% 10 0.9 1.3 0.9 2.5 0.3
2.|-- 94.246.207.117 0.0% 10 2.5 2.1 1.5 3.0 0.3
3.|-- 89.221.64.2 0.0% 10 1.5 4.3 1.5 11.8 3.3
4.|-- 81.20.144.98 0.0% 10 1.6 3.1 1.4 12.2 3.2
5.|-- 81.20.144.98 0.0% 10 2.8 4.7 1.5 24.9 7.1
6.|-- 217.159.159.122 0.0% 10 3.5 11.3 2.1 34.6 12.3
7.|-- ??? 100.0 10 0.0 0.0 0.0 0.0 0.0
8.|-- 194.126.123.2 0.0% 10 4.6 3.8 1.9 8.7 2.1
9.|-- 62.115.34.133 0.0% 10 3.0 4.5 1.8 18.9 5.1
10.|-- 62.115.134.220 0.0% 10 12.4 13.2 12.4 14.6 0.5
11.|-- 62.115.141.201 0.0% 10 12.8 14.9 12.4 20.7 3.2
12.|-- 4.68.110.225 90.0% 10 18.2 18.2 18.2 18.2 0.0
13.|-- 4.69.156.5 0.0% 10 122.5 121.1 119.8 122.5 0.8
14.|-- 4.69.156.5 0.0% 10 120.4 120.5 119.8 122.3 0.6
15.|-- 4.28.184.174 0.0% 10 124.7 124.8 123.5 128.7 1.4
16.|-- xx.xx.19.52 50.0% 10 145.1 130.3 124.4 145.1 8.8 (core router)
17.|-- ??? 100.0 10 0.0 0.0 0.0 0.0 0.0 
```


```
[root@kvm1 network-scripts]# ip addr show br1
30: br1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN 
    link/ether 26:7e:4a:b2:9a:e3 brd ff:ff:ff:ff:ff:ff
    inet xx.xx.98.66/27 brd xx.xx.98.95 scope global br1
    inet6 fe80::247e:4aff:feb2:9ae3/64 scope link 
       valid_lft forever preferred_lft forever

[root@kvm1 network-scripts]# ip addr show br0
4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN 
    link/ether 00:25:90:a1:76:06 brd ff:ff:ff:ff:ff:ff
    inet xx.xx.200.2/24 brd xx.xx.200.255 scope global br0
    inet6 fe80::fc16:3cff:fe9d:705b/64 scope link 
       valid_lft forever preferred_lft forever
[root@kvm1 network-scripts]# ip route
xx.xx.98.64/27 dev br1  proto kernel  scope link  src xx.xx.98.66 
10.0.0.0/24 dev eth1  proto kernel  scope link  src 10.0.0.9 
xx.xx.200.0/24 dev br0  proto kernel  scope link  src xx.xx.200.2 
169.254.0.0/16 dev eth1  scope link  metric 1003 
169.254.0.0/16 dev br0  scope link  metric 1004 
169.254.0.0/16 dev br1  scope link  metric 1030 
default via xx.xx.200.1 dev br0 

[root@kvm1 network-scripts]# service network restart
Shutting down interface br0:                               [  OK  ]
Shutting down interface eth0:                              [  OK  ]
Shutting down interface eth1:                              [  OK  ]
Shutting down loopback interface:                          [  OK  ]
Bringing up loopback interface:                            [  OK  ]
Bringing up interface br1:  Determining if ip address xx.xx.98.66 is already in use for device br0...
Error, some other host already uses address xx.xx.98.66.
                                                           [FAILED]
Bringing up interface eth0:                                [  OK  ]
Bringing up interface eth1:  Determining if ip address 10.0.0.9 is already in use for device eth1...
                                                           [  OK  ]
Bringing up interface br0:  Determining if ip address xx.xx.200.2 is already in use for device br0...
                                                           [  OK  ]

```


For further troubleshooting, I created a Centos 6 VM on the same KVM host with main IPxxx .xx.201.190 and it pings and I can access SSH. On Ubuntu the IPs are not working. 

Why the Ubuntu doesn't work is my confusion here.

The customer apparently updated the /etc/network/interfaces file in Ubuntu like this...


auto eth0:25
iface eth0:25 inet static
address xx.xx.98.90
netmask 255.255.255.255

So, no gateway and the netmask should be .224 as all the subnets assigned are /27 not single IPs. Am I right it should be 224 in the file? Is the gateway line required too? 

I tried changing one of the IPs netmask to 224, restart network on the Ubuntu VM. No ping still. Addded gateway to the same IP, restarted. No ping still.

Well, for one thing service networking restart is not working either. Even rebooted the VM. No ping.

[IMG]http://i.imgur.com/QiKENyk.png[/IMG]

---

