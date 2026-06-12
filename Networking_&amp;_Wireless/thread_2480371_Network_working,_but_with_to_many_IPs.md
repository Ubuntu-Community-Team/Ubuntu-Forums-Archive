---
title: "Network working, but with to many IPs"
date: 2022-10-27
forum: Networking &amp; Wireless
---

### Post by enboig on 2022-10-27
I upgraded my home server, moving my disks to the new one. After playing a little reinstalling grub and making it uefi compatble, I had some problems setting network; and my openvpn stopped working.

In netplan I just have:
```

# cat /etc/netplan/00-install-config.yaml 
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      addresses:
      - 192.168.1.7/24
      gateway4: 192.168.1.1
#      gateway6: "2001:1::2"
      nameservers:
        addresses:
        - 1.1.1.1
        - 8.8.4.4

```

But somehow I got 2 ip addresses:
```

# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 30:e1:71:6a:ad:e0 brd ff:ff:ff:ff:ff:ff
    altname enp0s31f6
    inet 192.168.1.7/24 brd 192.168.1.255 scope global eno1
       valid_lft forever preferred_lft forever
    inet 192.168.1.77/24 brd 192.168.1.255 scope global secondary noprefixroute eno1
       valid_lft forever preferred_lft forever
    inet6 fe80::32e1:71ff:fe6a:ade0/64 scope link 
       valid_lft forever preferred_lft forever
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:74:3d:0e brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
15: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none 
    inet 10.8.0.1/24 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::901f:555a:7b2e:e8db/64 scope link stable-privacy 
       valid_lft forever preferred_lft forever

```

Where does the second IP come from? how could I "reset" network and iptables configuration? This server started around 12.04 and keep upgrading it; so it may have some unneeded packages/configuration.

Thanks

---

### Post by enboig on 2022-10-27
I blacklisted the device in /etc/dhcpcd.conf and disabled dhcpcd in systemd. After rebooting the extra IP was gone, and no problems with other services (openvpn wasn't connecting)

---

