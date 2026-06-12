---
title: "Creating simple gateway"
date: 2023-10-19
forum: Networking &amp; Wireless
---

### Post by tyk88 on 2023-10-19
Hi,

I though asking for some help because I've not been able to get my gateway to work properly. My goal was just to make quickly a gateway so I can test how a certain "PC tool" works over it.
The PC tool sends a multicast message which is received by dut. The exchange few messages and dut is pinged and a TCP connection is opened.

What I've done is that I've just tried googling instructions. :) Many of the results just are about 20 years old so I'm not sure how valid they still are :)

Windows PC: 172.16.0.19, 255.255.255.0 (no gateway defined or 172.16.0.254, tried both)
Gateway eth0: 172.16.0.254
Gateway eth1: 192.168.100.254
DUT: 192.168.100.50, 255.255.255.0, 192.168.100.254

gateway is a laptop with ubuntu 20.04. I've installed pimd there. I have not made any changes to it's default configuration.

netplan conf: /etc/netplan/01-network-manager-all.yaml
```

network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eth0:
      match:
        macaddress: <MAC0>
      set-name: eth0
      addresses:
        - 172.16.0.254/24


    eth1:
      match:
        macaddress: <MAC1>
      set-name: eth1
      addresses:
        - 192.168.100.254/24

```


Then applying changes:
netplan apply

Next modifications to /etc/sysctl.conf


net.ipv4.ip_forward=1
net.ipv4.conf.all.mc_forwarding=1 # not sure about this


Activating changes: sysctl -p

Then iptables changes:
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables -A FORWARD -i eth1 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
iptables -t mangle -A PREROUTING -d <multicast address> -j TTL --ttl-set 64


Then storing iptable changes : dpkg-reconfigure iptables-persistent
And of course: service pimd start

This has worked couple of times. Most of the time I just see the multicast message in eth0, but not in eth1 (I'm monitoring them with wireshark in the gateway).

so, what is wrong in my configuration? What would be the best way to do this?

---

### Post by TheFu on 2023-10-19
Sorry, but I can't help.   When multicast is involved, nothing is simple.  It doesn't behave like other protocols, IME.

---

### Post by tyk88 on 2023-10-24
Configuration above works.

Issue was in our own device "DUT". it was not listening IGMP "membership query" messages. Those were dropped already in HW. After I enabled those, everything started to work :)

---

