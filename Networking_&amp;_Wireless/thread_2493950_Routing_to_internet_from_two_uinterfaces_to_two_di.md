---
title: "Routing to internet from two uinterfaces to two different gateways"
date: 2023-12-31
forum: Networking &amp; Wireless
---

### Post by hnpilot on 2023-12-31
I have a small home office for which I just got a fiber connection.

My target is to have a DMZ zone (a few servers) and LAN zone (for family members, printer and WLAN).

My traffic to internet currently goes via a  5G modem. I have an Ubuntu 22.04 router/firewall using netplan and firwalld.

There are 4 interfaces: enp1s0 (DMZ), enp3s0 (LAN), enp4s0 (5G) and enp5s0 (FC).

I would like to first route the LAN to use the FC but leave for now the DMZ to use 5G, so basically it should go like this: enp1s0 -> enp4s0 and enp3s0 -> enp5s0.

My netplan config is as follows:

```
network:
   ethernets:
     enp5s0:
        dhcp4: true
     enp4s0:
        addresses: []
        dhcp4: true
     enp3s0:
        dhcp4: false
        addresses:
        - 192.168.192.1/24
        routes:
        - to: 0.0.0.0/0
          via: A.B.C.D      
        nameservers:
           addresses:
           - 1.1.1.1
           - 8.8.8.8
           - 8.8.4.4
     enp1s0:
        addresses:
        - 192.168.200.1/24
       routes:
      - to: default
      via: E.F.G.H
      nameservers:
         addresses:
         - 8.8.8.8
         - 1.1.1.1
        search: []
  version: 2
```

I thought that it would route the LAN (192.168.192.0/24) via FC, but when I check it with whatismyip.com, it returns the 5G IP (E.F.G.H).

My weakest point in setting up a server is networking so I would really appreciate any ideas how to proceed.

An additional problem is that (at least currently) the FC connection gets IP via dhcp, so A.B.C.D would change. Is there any way to forward traffic from one interface to another interface, interface by interface, not hard-coding the IPs.

I have tried to google the problem but at least so far to no avail...

wbr

hannu

---

### Post by The Cog on 2023-12-31
Well, I didin't think netplan could do that, but apparently it can.
1: You should not have two default routes in one routing table. If they are equal priority then Linux will use them alternately, per-connection or per-packet. If they are different priorities then only one will be used.
2: Linux can have hundreds of separate routing tables. I think you only need two. Linux has rules to specify which connections should use which routing table.
3: There are rules that specify which table should be used under what circumstances. Incoming interface/address is often used to select which routing table to use. Rules are numbered in order of being consulted.
4: You can't override "local" routes to locally connected networks (I don't think so, anyway).

I think in your case you need two extra tables. Add table 100 perhaps, with a default route pointing over the 5G router and table 200 with a default route pointing over the Fibre Connection router.
The tables only need one default route each. 
Then add a rule 100 that says anything coming from DMZ uses table 100, and rule 200 that says anything from LAN uses table 200. You can use input-interface or source-address in the rule.
Table main will have two default routes, but no matter because the earlier rules will have decided the route anyway.

This conversation may help clear things up. You can see the usual arrangement of tables and rules:
```
root@pi400:~# ip rule
0:	from all lookup local 
32766:	from all lookup main 
32767:	from all lookup default 
root@pi400:~# 
root@pi400:~# 
root@pi400:~# ip route list table local
broadcast 127.0.0.0 dev lo proto kernel scope link src 127.0.0.1 
local 127.0.0.0/8 dev lo proto kernel scope host src 127.0.0.1 
local 127.0.0.1 dev lo proto kernel scope host src 127.0.0.1 
broadcast 127.255.255.255 dev lo proto kernel scope link src 127.0.0.1 
broadcast 192.168.0.0 dev wlan0 proto kernel scope link src 192.168.0.105 
local 192.168.0.105 dev wlan0 proto kernel scope host src 192.168.0.105 
broadcast 192.168.0.255 dev wlan0 proto kernel scope link src 192.168.0.105 
root@pi400:~# 
root@pi400:~# 
root@pi400:~# ip route list table main
default via 192.168.0.1 dev wlan0 proto dhcp src 192.168.0.105 metric 303 
192.168.0.0/24 dev wlan0 proto dhcp scope link src 192.168.0.105 metric 303 
root@pi400:~# 
root@pi400:~# 
root@pi400:~# ip route list table default
root@pi400:~# 

```

There are things I'm not sure about here though. 
The default routes in table main are learned via dhcp. If you just specify an outgoing interface (not an IP address) in a table, it will try to use ARP which probably won't work. I'm not sure how you would get the right address in there.
This post looks very helpful: [https://askubuntu.com/questions/1169002/how-to-use-netplan-to-create-two-separate-routing-tables](https://askubuntu.com/questions/1169002/how-to-use-netplan-to-create-two-separate-routing-tables)

---

