---
title: "Edgy Routing Problem - 2 nics"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by jim87410 on 2007-03-20
Hi, I have been messing with this problem for several days and can't seem to find the solution.  I appreciate any help anyone can give... Thanks in advance.

I have a box(ibm-server) running 6.10 server w/ 2 nics.
eth0: IP 192.168.0.215/24
eth1: IP 192.168.1.1/24

-- My gateway (Ubuntu Desktop) to the Internet is 192.168.0.210
-- I have a laptop (W2K) connected via crossover to ibm-server:eth1 with address of 192.168.1.100
-- The laptop can ping eth1.
-- The laptop can ping eth0.
-- The laptop cannot ping the gateway (Request timed out)

-- The gateway can ping ibm-server:eth0.
-- By adding the route (ip route add to 192.168.1.0/24 via 192.168.0.215 dev eth0) to the gateway, the gateway can ping ibm-server:eth1.
-- The gateway cannot ping the laptop. 

-- HERE IS THE INTERFACES FILE
jim@ibm-server:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.215
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.210
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 205.171.3.65 205.171.2.65

# The secondary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        dns-nameservers 205.171.3.65 205.171.2.65

# SAW A POST THAT SUGGESTED THE BELOW... IT DIDN'T MAKE A DIFFERENCE
# up route add -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.0.210
# down route del -net 192.168.0.0 netmask 255.255.0.0 gw 192.168.0.210

-- IFCONFIG
jim@ibm-server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:A1:99:1A:6D  
          inet addr:192.168.0.215  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe99:1a6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11435 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:631323 (616.5 KiB)  TX bytes:1112818 (1.0 MiB)
          Interrupt:185 Base address:0x7400 

eth1      Link encap:Ethernet  HWaddr 00:40:F4:E9:6C:3E  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fee9:6c3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37615 (36.7 KiB)  TX bytes:13388 (13.0 KiB)
          Interrupt:177 Base address:0xef00 

-- ROUTE
jim@ibm-server:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
localnet            *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.210   0.0.0.0         UG    0      0        0 eth0

-- SOME MORE PING TESTS...
jim@ibm-server:/etc/network$ ping 192.168.0.210
PING 192.168.0.210 (192.168.0.210) 56(84) bytes of data.
64 bytes from 192.168.0.210: icmp_seq=1 ttl=64 time=0.179 ms

jim@ibm-server:/etc/network$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=128 time=0.252 ms

jim@ibm-server:/etc/network$ ping -I eth0 192.168.1.100
PING 192.168.1.100 (192.168.1.100) from 192.168.1.1 eth0: 56(84) bytes of data.
From 192.168.0.210: icmp_seq=2 Redirect Host(New nexthop: 192.168.0.215)

jim@ibm-server:/etc/network$ ping -I eth0 192.168.0.210
PING 192.168.0.210 (192.168.0.210) from 192.168.0.215 eth0: 56(84) bytes of data.
64 bytes from 192.168.0.210: icmp_seq=1 ttl=64 time=0.279 ms

jim@ibm-server:/etc/network$ ping -I eth1 192.168.0.210
PING 192.168.0.210 (192.168.0.210) from 192.168.0.215 eth1: 56(84) bytes of data.
From 192.168.1.1 icmp_seq=2 Destination Host Unreachable

jim@ibm-server:/etc/network$ ping -I eth1 192.168.1.100
PING 192.168.1.100 (192.168.1.100) from 192.168.1.1 eth1: 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=128 time=0.400 ms

The minimum goal would be for the laptop to route to the Internet....  maximum goal would be for everyone to see everyone.

---

### Post by mchan on 2007-04-05
Look up from forum and search "Dual LANS Setting" / MChan,
I posted full detailed conf on page 2 with Marc's help.
and hope this help you too.
Let me know if you need further help, I will do my best to walk you through.
MChan

---

