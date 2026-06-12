---
title: "Xen dom0 can't access network"
date: 2015-09-29
forum: Networking &amp; Wireless
---

### Post by chelmite2 on 2015-09-29
I'm a xen newbie.

I managed to get a saucy installation of ubuntu xen to upgrade to 14.04 (on the way to 15.04).
However, after rebooting, I cannot access the network.

```
% uname -a
Linux dom0 3.13.0-65-generic #105-Ubuntu SMP Mon Sep 21 18:50:58 UTC 2015 x86_64 x86_x4 x86_64 GNULinux

```
ifconfig shows:
```
lo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24592 (24.5 KB)  TX bytes:24592 (24.5 KB)


ovsbr0    Link encap:Ethernet  HWaddr e0:cb:4e:a8:10:27  
          inet addr:10.0.2.106  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::fc73:a1ff:fe6d:862b/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:5962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1049070 (1.0 MB)  TX bytes:19637 (19.6 KB)


p7p1      Link encap:Ethernet  HWaddr e0:cb:4e:a8:10:27  
          inet addr:10.0.2.117  Bcast:10.0.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1056886 (1.0 MB)  TX bytes:35967 (35.9 KB)


xenbr0    Link encap:Ethernet  HWaddr 22:ef:a8:28:1f:c2  
          inet6 addr: fe80::20ef:a8ff:fe28:1fc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:3042 (3.0 KB)



```
Oddly, I can ping my router:
```
PING 10.0.2.1 (10.0.2.1) 56(84) bytes of data.64 bytes from 10.0.2.1: icmp_seq=1 ttl=64 time=0.527 ms
64 bytes from 10.0.2.1: icmp_seq=2 ttl=64 time=0.338 ms
64 bytes from 10.0.2.1: icmp_seq=3 ttl=64 time=0.297 ms



```
My router shows that the 10.0.2.117 interface (p7p1) is connected.
I cannot ping my AT&T router:
```
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.From 10.0.2.106 icmp_seq=1 Destination Host Unreachable
From 10.0.2.106 icmp_seq=2 Destination Host Unreachable
From 10.0.2.106 icmp_seq=3 Destination Host Unreachable

```
What's odd is that it's referencing 10.0.2.106, rather than the 192.168.1.254 address!
I cannot ping any ip address on the Internet:
```
% ping ubuntu.com
PING ubuntu.com (91.189.94.50) 56(84) bytes of data.
From 10.0.2.106 icmp_seq=1 Destination Host Unreachable
```
I can access the AT&T router from another computer connected to the local router, and I can ping outside addresses.

/etc/sysctl.conf contains:
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
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1


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
net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
net.ipv4.conf.all.log_martians = 1
#
net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0

```

/etc/network/interfaces contains:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# Xen network interface for "dom0"
auto xenbr0
iface xenbr0 inet dhcp


bridge_ports p7p1


# The primary network interface
auto p7p1
iface p7p1 inet dhcp
#    dns-nameservers 68.94.156.1 68.94.157.1


allow-hotplug ovsbr0
iface ovsbr0 inet dhcp

```

When I try to restart networking, I get:
```
# service networking restart
stop: Job failed while stopping
start: Job is already running: networking

```

---

