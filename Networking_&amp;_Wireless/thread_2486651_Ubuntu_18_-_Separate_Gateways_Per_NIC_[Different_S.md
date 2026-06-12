---
title: "Ubuntu 18 - Separate Gateways Per NIC [Different Subnets]"
date: 2023-05-07
forum: Networking &amp; Wireless
---

### Post by Glenn_Teachey on 2023-05-07
I'm setting up my system and need each NIC to route its traffic out/in it's own gateway.

I found some posts on here directing to links such as this one - [https://www.thomas-krenn.com/en/wiki/Two_Default_Gateways_on_One_System](https://www.thomas-krenn.com/en/wiki/Two_Default_Gateways_on_One_System) - saying to add rules to /etc/rc.local.
Is this the only way to have this work?
Currently my configuration looks like this:
```
network:
    version: 2
    ethernets:
        eth0:
            dhcp4: true
            dhcp4-overrides:
                route-metric: 100
            dhcp6: false
            match:
                driver: hv_netvsc
                macaddress: xxxx
            set-name: eth0
        eth1:
            dhcp4: true
            dhcp4-overrides:
                route-metric: 200
            dhcp6: false
            match:
                driver: hv_netvsc
                macaddress: xxxx
            set-name: eth1
            routes:
             - to: 10.0.4.0/24
               via: 10.0.4.1
               table: 201
             - to: 0.0.0.0/0
               via: 10.0.4.1
               table: 201
            routing-policy:
             - from: 10.0.4.4/32
               table: 201
             - to: 10.0.4.4/32
               table: 201
             - OutgoingInterface: eth1

```
Which doesn't allow routing to work on the eth1 interface.
```
root@multinicvm3ub18:~# ping 10.0.1.4 -c 2 -I eth1
PING 10.0.1.4 (10.0.1.4) from 10.0.4.4 eth1: 56(84) bytes of data.

--- 10.0.1.4 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1023ms
pipe 2
```

But as soon as I add the ip rule "oif" to that routing table I can get response.
```
root@multinicvm3ub18:~# ip rule add oif eth1 table 201
```
```
root@multinicvm3ub18:~# ping 10.0.1.4 -c 2 -I eth1
PING 10.0.1.4 (10.0.1.4) from 10.0.4.4 eth1: 56(84) bytes of data.
64 bytes from 10.0.1.4: icmp_seq=1 ttl=64 time=0.911 ms
64 bytes from 10.0.1.4: icmp_seq=2 ttl=64 time=1.00 ms

--- 10.0.1.4 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1033ms
rtt min/avg/max/mdev = 0.911/0.959/1.007/0.048 ms
root@multinicvm3ub18:~#
```

So, does netplan's YAML file not support this parameter and is this the only way to make this work on Ubuntu?

---

### Post by TheFu on 2023-05-08
Standard support for 18.04 ends this month.  Please do yourself a favor and move to either 20.04 or 22.04 LTS releases.
At this stage, nobody should be doing a new install of anything older than 20.04.

BTW, 18.04 is about the time the change from the interfaces file to netplan happened.  Whether one or the other is used is a 50/50 guess on that release.

I haven't seen eth0 or eth1 device names in a long time.  The driver determines the correct ethernet device name.  I've been seeing ensX or enpXsY for many years now, including on 18.04 systems.

I'd look at the routing table to see what is actually being set.
```
ip route |column -t
```

Sometimes it is just easier to script the 'ip' command you want than to deal with netplan.

---

