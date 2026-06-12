---
title: "Networking Problems"
date: 2015-09-28
forum: Networking &amp; Wireless
---

### Post by mladoux on 2015-09-28
Hello, 

I'm having issues with the networking on my Ubuntu Server. Only the route on eth0 works. I'm running Ubuntu 14.04 LTS with all updates applied. Here's some relevant junk that might help you figure out where I went wrong:

uname -a output:
```
Linux ubuntu 3.13.0-63-generic #103-Ubuntu SMP Fri Aug 14 21:42:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

ip addr output:
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:16:21:77:5f:e7 brd ff:ff:ff:ff:ff:ff
    inet 141.255.187.242/29 brd 141.255.187.247 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 2a00:16d8:2:407::2/64 scope global 
       valid_lft forever preferred_lft forever
    inet6 fe80::216:21ff:fe77:5fe7/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:16:26:1b:bb:a8 brd ff:ff:ff:ff:ff:ff
    inet 141.255.187.243/29 brd 141.255.187.247 scope global eth1
       valid_lft forever preferred_lft forever
    inet6 2a00:16d8:2:407:b996:8343:665a:2fa3/64 scope global temporary dynamic 
       valid_lft 603050sec preferred_lft 84050sec
    inet6 2a00:16d8:2:407:216:26ff:fe1b:bba8/64 scope global dynamic 
       valid_lft 2591947sec preferred_lft 604747sec
    inet6 fe80::216:26ff:fe1b:bba8/64 scope link 
       valid_lft forever preferred_lft forever
4: eth4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:16:39:1c:5b:39 brd ff:ff:ff:ff:ff:ff
    inet 141.255.187.244/29 brd 141.255.187.247 scope global eth4
       valid_lft forever preferred_lft forever
    inet6 2a00:16d8:2:407::4/64 scope global 
       valid_lft forever preferred_lft forever
    inet6 fe80::216:39ff:fe1c:5b39/64 scope link 
       valid_lft forever preferred_lft forever
5: eth3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:16:04:af:10:bc brd ff:ff:ff:ff:ff:ff
    inet 141.255.187.245/29 brd 141.255.187.247 scope global eth3
       valid_lft forever preferred_lft forever
    inet6 2a00:16d8:2:407::5/64 scope global 
       valid_lft forever preferred_lft forever
    inet6 fe80::216:4ff:feaf:10bc/64 scope link 
       valid_lft forever preferred_lft forever

```

contents of /etc/network/interfaces:

```

# For the table names in config below, those need to be added to /etc/iproute2/rt_tables


# The loopback network interface
auto lo
iface lo inet loopback


# Network Interfaces
auto eth0
iface eth0 inet static
        address 141.255.187.242
        netmask 255.255.255.248
        gateway 141.255.187.241
    post-up /sbin/ip route add 141.255.187.240/29 dev eth0 src 141.255.187.242 table eth0
    post-up /sbin/ip route add default via 141.255.187.241 dev eth0 table eth0
    post-down /sbin/ip rule del from 141.255.187.242 table eth0
    dns-nameservers 8.8.8.8 8.8.4.4
iface eth0 inet6 static
        address 2a00:16d8:2:407::2
        netmask 64
        gateway 2a00:16d8:2:407::1
        pre-up modprobe ipv6
    dns-nameservers 2001:4860:4860::8888 2001:4860:4860::8844


auto eth1
iface eth1 inet static
        address 141.255.187.243
        netmask 255.255.255.248
    post-up /sbin/ip route add 141.255.187.240/29 dev eth1 src 141.255.187.243 table eth1
    post-up /sbin ip route add default via 141.255.187.241 dev eth1 table eth1
    post-up /sbin ip rule add from 141.255.187.243 table eth1
    post-down /sbin/ip rule del from 141.255.187.243 table eth1
iface eth1 inet6 static
        address 2a00:16d8:2:407::3
        netmask 64
        pre-up modprobe ipv6


auto eth4
iface eth4 inet static
        address 141.255.187.244
        netmask 255.255.255.248
    post-up /sbin/ip route add 141.255.187.240/29 dev eth4 src 141.255.187.243 table eth4
    post-up /sbin/ip route add default via 141.255.187.241 dev eth4 table eth4
    post-up /sbin/ip rule add from 141.255.187.244 table eth4
    post-down /sbin/ip rule del from 141.255.187.244 table eth4
iface eth4 inet6 static
        address 2a00:16d8:2:407::4
        netmask 64
        pre-up modprobe ipv6


auto eth3
iface eth3 inet static
        address 141.255.187.245
        netmask 255.255.255.248
    post-up /sbin/ip route add 141.255.187.240/29 dev eth3 src 141.255.187.245 table eth3
    post-up /sbin/ip route add default via 141.255.187.241 dev eth3 table eth3
    post-up /sbin/ip rule add from 141.255.187.245 table eth3
    post-down /sbin/ip rule del from 141.255.187.245 eth3
iface eth3 inet6 static
        address 2a00:16d8:2:407::5
        netmask 64
        pre-up modprobe ipv6

```

contents of /etc/iproute2/rt_tables

```

#
# reserved values
#
255    local
254    main
253    default
0    unspec
#
# local
#
#1    inr.ruhep
24  eth0
25  eth1
26  eth3
27  eth4

```

I've been working on getting it to work all night, maybe I just need a second set of eyes. I need to get the networks on eth1, eth3, and eth4 to be routable and reachable.

---

### Post by SeijiSensei on 2015-09-28
Did you enable packet forwarding by uncommenting the line
```
net.ipv4.ip_forward=1
```
in /etc/sysctl.conf?  Packet forwarding between interfaces is disabled by default for security reasons.  You'll need to reboot to see the effects of this change or run the command
```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```

---

### Post by mladoux on 2015-09-28
Nope, I knew I forgot something, did that, didn't work after the echo line, so rebooted server. Still can't ping other networks, just the main one.

here's my sysctl.conf
```
## /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#


#kernel.domainname = example.com


# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3


##############################################################3
# Functions previously found in netbase
#


# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1


# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1


# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1


# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1




###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#

```

---

### Post by mladoux on 2015-09-28
Correction, only .243 is not working. There must be a typo. I'm going to work on that for a bit, and let you know if I can't figure it out.

---

### Post by mladoux on 2015-09-28
Found a typo in the configuration of .244 that prevented .243 from working, but even after fixing it and rebooting, .243 still refuses to work.

---

### Post by mladoux on 2015-09-28
found a typo in the post-up for eth3, fixed, all is working.

---

