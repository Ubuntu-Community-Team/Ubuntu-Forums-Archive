---
title: "ugh... Cant get both NICs to route through their assigned gateways! HELP plz"
date: 2013-11-20
forum: Networking &amp; Wireless
---

### Post by sbctwc on 2013-11-20
Hello all
 I am new to the forums.

Here is my problem. Ive been assigned a task to configure the NIC cards (eth0 and eth1) on an Ubuntu Linux 10.04 box. One NIC will be used for internet traffic ,and the second NIC will be used for VLAN backup traffic.  The first NIC, eth0 , has DNS entries in /etc/resolv.conf, but the second NIC will not be assigned any DNS. These are static IPs of course. 

for eth0:

IP: 10.146.112.34
Gateway: 10.146.112.1
Netmask: 255.255.255.0

for eth1:

IP: 10.146.123.8
Gateway: 10.146.123.1
Netmask: 255.255.255.0

I need the traffic following to/from eth0 to be routed through 10.146.112.1, and the traffic flowing to/from eth1 to be routed through 10.146.123.1. I attempted to use policy routing to make this work, but for some strange reason, I am able to ping to the box to and from the internet through eth0 but when I try to ping from the LAN or from the internet to eth1, it does not ping at all. Also if i ping from the box to the gateway address for eth1, it gives me a destination host unreachable error. 

Here is my output for ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr 5c:f3:fc:b5:33:90          inet addr:10.146.112.34  Bcast:10.146.112.255  Mask:255.255.255.0
          inet6 addr: fe80::5ef3:fcff:feb5:3390/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2951 errors:0 dropped:0 overruns:0 frame:0
          TX packets:883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:322770 (322.7 KB)  TX bytes:201609 (201.6 KB)
          Interrupt:28 Memory:92000000-92012800


eth1      Link encap:Ethernet  HWaddr 5c:f3:fc:b5:33:92
          inet addr:10.146.123.8  Bcast:10.146.123.255  Mask:255.255.255.0
          inet6 addr: fe80::5ef3:fcff:feb5:3392/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:2996 (2.9 KB)
          Interrupt:40 Memory:94000000-94012800


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7077 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:530720 (530.7 KB)  TX bytes:530720 (530.7 KB)


usb0      Link encap:Ethernet  HWaddr 5e:f3:fc:bb:33:93
          inet addr:169.254.95.120  Bcast:169.254.95.255  Mask:255.255.255.0
          inet6 addr: fe80::5cf3:fcff:febb:3393/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2673351 (2.6 MB)  TX bytes:953496 (953.4 KB)



```

Please ignore the usb0 interface. My team and I have no idea what that is, and we have no way of getting rid of it!

I set up the /etc/iproute2/rt_tables  file as such:

```
## reserved values
#
255     local
254     main
253     default
0       unspec
#
# local
#
#1      inr.ruhep
200     firstnet
300     secondnet



```


firstnet = routing table for eth0
secondnet = routing table for eth1

my /etc/network/interfaces file is as such:

```
$ cat /etc/network/interfaces# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        address 10.146.112.34
        netmask 255.255.255.0
        network 10.146.112.0
        broadcast 10.146.112.255
        gateway 10.146.112.1


#Added to test policy routing


        post-up ip route add 10.146.112.0/24 dev eth0 src 10.146.112.34 table firstnet
        post-up ip route add default via 10.146.112.1 dev eth0 table firstnet
        post-up ip rule add from 10.146.112.34/24 table firstnet
        post-up ip rule add to 10.146.112.34/24 table firstnet
        post-down ip rule del from 10.146.112.34/24 table firstnet
        post-down ip rule del to 10.146.112.34/24 table firstnet








# configuration for second interface eth1
auto eth1
allow-hotplug eth1
iface eth1 inet static
        address 10.146.123.8
        netmask 255.255.255.0
        gateway 10.146.123.1
        post-up ip route add 10.146.123.0/24 dev eth1 src 10.146.123.8 table secondnet
        post-up ip route add default via 10.146.123.1 dev eth1 table secondnet
        post-up ip rule add from 10.146.123.8/24 table secondnet
        post-up ip rule add to 10.146.123.8/24 table secondnet
        post-down ip rule del from 10.146.123.8/24 table secondnet
        post-down ip rule del to 10.146.123.8/24 table secondnet



```

my /etc/sysctl.conf file is as such:

```
2$ cat /etc/sysctl.conf#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#


#kernel.domainname = example.com


# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7


##############################################################3
# Functions previously found in netbase
#


# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1


# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1


# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1


# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1




###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
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



```

This is what I get when I restart the networking service:

```
 sudo /etc/init.d/networking restart * Reconfiguring network interfaces...                                                                                                                                                                                                       RTNETLINK answers: No such file or directory
RTNETLINK answers: No such process
RTNETLINK answers: No such file or directory
ssh stop/waiting
ssh start/running, process 14441
ssh stop/waiting
ssh start/running, process 14513



```

and I am unable to ping to 10.146.123.8 from the LAN nor from the internet.  

I have no idea what I am doing wrong!  Please assist me.  All help will be GREATLY appreciated!


Thanks!


Ping examples:


From the internet as well as the LAN to eth0:


Pinging 10.146.112.34 with 32 bytes of data:
Reply from 10.146.112.34: bytes=32 time=44ms TTL=57
Reply from 10.146.112.34: bytes=32 time=42ms TTL=57
Reply from 10.146.112.34: bytes=32 time=42ms TTL=57
Reply from 10.146.112.34: bytes=32 time=42ms TTL=57


Ping statistics for 10.146.112.34:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 42ms, Maximum = 44ms, Average = 42ms





From the box to the internet:

ping [www.yahoo.com](www.yahoo.com)
PING ds-any-fp3-real.wa1.b.yahoo.com (98.139.180.149) 56(84) bytes of data.
64 bytes from ir1.fp.vip.bf1.yahoo.com (98.139.180.149): icmp_seq=1 ttl=45 time=72.5 ms
64 bytes from ir1.fp.vip.bf1.yahoo.com (98.139.180.149): icmp_seq=2 ttl=45 time=274 ms
64 bytes from ir1.fp.vip.bf1.yahoo.com (98.139.180.149): icmp_seq=3 ttl=43 time=56.3 ms
64 bytes from ir1.fp.vip.bf1.yahoo.com (98.139.180.149): icmp_seq=4 ttl=45 time=58.8 ms
64 bytes from ir1.fp.vip.bf1.yahoo.com (98.139.180.149): icmp_seq=5 ttl=45 time=63.3 ms
64 bytes from ir1.fp.vip.bf1.yahoo.com (98.139.180.149): icmp_seq=6 ttl=43 time=72.3 ms
64 bytes from ir1.fp.vip.bf1.yahoo.com (98.139.180.149): icmp_seq=7 ttl=45 time=70.7 ms
64 bytes from ir1.fp.vip.bf1.yahoo.com (98.139.180.149): icmp_seq=8 ttl=43 time=67.1 ms
^C
--- ds-any-fp3-real.wa1.b.yahoo.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7009ms
rtt min/avg/max/mdev = 56.322/91.952/274.355/69.176 ms

from the internet to 10.146.123.8:


Pinging 10.146.123.8 with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.


Ping statistics for 10.146.123.8:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),


From the LAN to the box via eth1

Pinging 10.146.123.8 with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.


Ping statistics for 10.146.123.8:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

From the box to 10.146.123.1:


:/etc/iproute2$ ping 10.146.123.1
PING 10.146.123.1 (10.146.123.1) 56(84) bytes of data.
From 10.146.123.8 icmp_seq=2 Destination Host Unreachable
From 10.146.123.8 icmp_seq=3 Destination Host Unreachable
From 10.146.123.8 icmp_seq=4 Destination Host Unreachable
From 10.146.123.8 icmp_seq=6 Destination Host Unreachable
From 10.146.123.8 icmp_seq=7 Destination Host Unreachable
From 10.146.123.8 icmp_seq=8 Destination Host Unreachable
From 10.146.123.8 icmp_seq=9 Destination Host Unreachable
From 10.146.123.8 icmp_seq=10 Destination Host Unreachable
From 10.146.123.8 icmp_seq=11 Destination Host Unreachable
From 10.146.123.8 icmp_seq=12 Destination Host Unreachable
From 10.146.123.8 icmp_seq=13 Destination Host Unreachable
From 10.146.123.8 icmp_seq=14 Destination Host Unreachable









Please help!  Thanks!

---

### Post by sbctwc on 2013-11-22
107 views and not ONE response? Come on guys!

---

