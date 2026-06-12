---
title: "Ubuntu 18.04.3 - promlem setting up static IP with netplan"
date: 2019-10-15
forum: Networking &amp; Wireless
---

### Post by jim-anderson on 2019-10-15
I am installing Ubuntu 18.04.3 on a computer and I have run into a problem setting up the computer with a static IP.

When I run:

> 
netplan generate
netplan --debug apply


I get:

```
** (generate:12021): DEBUG: 15:52:55.938: Processing input file /etc/netplan/01-network-card.yaml..
** (generate:12021): DEBUG: 15:52:55.938: starting new processing pass
** (generate:12021): DEBUG: 15:52:55.938: eno1: setting default backend to 1
** (generate:12021): DEBUG: 15:52:55.938: Configuration is valid
** (generate:12021): DEBUG: 15:52:55.938: Generating output files..
** (generate:12021): DEBUG: 15:52:55.938: NetworkManager: definition eno1 is not for us (backend 1)
DEBUG:netplan generated networkd configuration changed, restarting networkd
DEBUG:no netplan generated NM configuration exists
DEBUG:eno1 not found in {}
DEBUG:Merged config:
network:
  bonds: {}
  bridges: {}
  ethernets:
    eno1:
      addresses:
      - 192.168.1.235/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.0.1
      nameservers:
        addresses:
        - 8.8.8.8
        - 8.8.4.4
  vlans: {}
  wifis: {}


```

If I ping 8.8.8.8, or any of the IP addresses on my local network, I get:

> connect: Network is unreachable

My /etc/netplan/01-network-card.yaml file, which is a modified version of what I downloaded from the internet, is as follows:

```
network:
    version: 2
    renderer: networkd
    ethernets:
        eno1:
            dhcp4: no
            dhcp6: no
            addresses: [192.168.1.235/24]
            gateway4: 192.168.0.1
            nameservers:
                addresses: [8.8.8.8,8.8.4.4]

```

The results of:

ip addr show are:

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 5c:26:0a:1d:d9:44 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.235/24 brd 192.168.1.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::71fb:c807:cd73:84eb/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp2s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether ec:55:f9:74:0a:5c brd ff:ff:ff:ff:ff:ff


```

I'm still experimenting, but and advise or help will be appreciated.

Jim A

---

### Post by jim-anderson on 2019-10-15
Solved explanation - I was proof reading the results of 'ip addr show' and noticed that I had a typo on the IP address that I wanted to use for the computer. The address reported was:

192.168.1.235/24

and should have been:

192.168.0.235/24

Dumb computer should have known better.

Jim A.

---

