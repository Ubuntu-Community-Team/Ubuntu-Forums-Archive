---
title: "How do I use NetPlan with NetworkManager?"
date: 2019-06-18
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2019-06-18
Coming from Lubuntu to ubuntu
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=19.04
DISTRIB_CODENAME=disco
DISTRIB_DESCRIPTION="Ubuntu 19.04"

wireless ip address for the computer is 192.168.2.5
I like to use the OpenDNS Our FamilyShield nameservers are:
208.67.222.123
208.67.220.123

I was told to set my dns servers in nm-connection-editor ip address 4 dns servers 208.67.222.123, 208.67.220.123 but they do not work. then was told

sudo nano /etc/netplan/01-network-manager-all.yaml
set up /etc/netplan  with
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```

sudo netplan generate
sudo netplan apply

I have done this and the porn still gets through. And yes I have cleared the browser cash. And check to make sure I have the right DNS addresses. Did I do something wrong?

ip a output
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp1s0f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether f0:76:1c:2a:c0:67 brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 30:10:b3:85:76:49 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.5/24 brd 192.168.2.255 scope global dynamic noprefixroute wlp2s0
       valid_lft 74960sec preferred_lft 74960sec
    inet6 fe80::6de0:a55a:b617:4f47/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: vmnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether 00:50:56:c0:00:01 brd ff:ff:ff:ff:ff:ff
    inet 192.168.17.1/24 brd 192.168.17.255 scope global vmnet1
       valid_lft forever preferred_lft forever
    inet6 fe80::250:56ff:fec0:1/64 scope link 
       valid_lft forever preferred_lft forever
5: vmnet8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether 00:50:56:c0:00:08 brd ff:ff:ff:ff:ff:ff
    inet 172.16.229.1/24 brd 172.16.229.255 scope global vmnet8
       valid_lft forever preferred_lft forever
    inet6 fe80::250:56ff:fec0:8/64 scope link 
       valid_lft forever preferred_lft forever

```

---

### Post by chili555 on 2019-06-18
Did you clear the dnsmasq cache?```

sudo systemd-resolve --flush-caches

```I wouldn't suggest that you mix Network Manager with netplan. If you haven't already, set your DNS nameservers in NM: [https://i.stack.imgur.com/ueR0q.png](https://i.stack.imgur.com/ueR0q.png)

---

