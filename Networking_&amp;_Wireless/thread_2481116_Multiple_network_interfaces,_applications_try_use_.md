---
title: "Multiple network interfaces, applications try use (wrong) devices without ip."
date: 2022-11-19
forum: Networking &amp; Wireless
---

### Post by samuli-latvala on 2022-11-19
```
OS: Ubuntu 22.04.1 LTS x86_64
Host: ODYSSEY-X86J4105
Kernel: 6.0.9-060009-generic
Packages: 1062 (dpkg), 7 (snap)
Shell: bash 5.1.16
Memory: 5110MiB / 7785MiB

```

```
GNU nano 6.2                                        /etc/netplan/01-netcfg.yaml *
network:
  version: 2
  ethernets:
    enp2s0:
      dhcp4: no
      dhcp6: no
    enp3s0:
      dhcp4: no
      dhcp6: no


  renderer: networkd
  bonds:
    bond0:
      interfaces: [enp2s0, enp3s0]
      addresses: [192.168.0.6/24]
      routes:
        to: default
        via: 192.168.0.1
      parameters:
        mode: balance-alb
        transmit-hash-policy: layer3+4
        mii-monitor-interval: 100
        primary: bond0
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4

```

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP group default qlen 1000
    link/ether 00:e0:4c:02:27:92 brd ff:ff:ff:ff:ff:ff
3: enp3s0: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP group default qlen 1000
    link/ether 6a:54:f2:32:57:b4 brd ff:ff:ff:ff:ff:ff permaddr 00:e0:4c:02:27:93
4: wlo2: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 34:7d:f6:b5:11:25 brd ff:ff:ff:ff:ff:ff
    altname wlp0s12f0
5: bond0: <BROADCAST,MULTICAST,MASTER,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 6a:54:f2:32:57:b4 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.6/24 brd 192.168.0.255 scope global bond0
       valid_lft forever preferred_lft forever
    inet6 fe80::6854:f2ff:fe32:57b4/64 scope link
       valid_lft forever preferred_lft forever
6: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none
    inet 10.8.0.1/24 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fd42:42:42:42::1/112 scope global
       valid_lft forever preferred_lft forever
    inet6 fe80::283d:26a6:a489:4e4e/64 scope link stable-privacy
       valid_lft forever preferred_lft forever

```

Problem: When game servers are starting up, they are trying to use wrong one or multiple interfaces and fail. If I revert back and use only one network device, problem disappears (This is not something I would like to do).
Problem2: I'm able to connect VPN server but from that point no data is moving to client. 
root cause: Steam applications are bind to ip 0.0.0.0 as a default. I could not pinpoint root cause with VPN.
Question:  How can I setup default network interface for all connections or additionally hide non-ip-interfaces from software? (Forcing application to use specific interface doesn't seem a solution or even option)

-Sam

---

