---
title: "Transparent bridge FORWARD rules not working in nested KVM"
date: 2017-11-20
forum: Networking &amp; Wireless
---

### Post by dmpostma on 2017-11-20
I am attempting to deploy an Ubuntu 16.04 host as a transparent bridge between two hosts in a nested KVM environment.

Topology:

[FONT=courier new]
...........10.10.100.0/24.......................10.10.10.0/24 (bridged network)....................................
(Client).2-----------------.1(virtualrouter1).1----------(ubuntubridge)----------.2(virtualrouter2)-----(Internet)
...............................192.168.31.1..............ens3      (.253)   ens4.............192.168.31.2.................
................................(loopback).............................................(loopback)..................[/FONT]

Scenario: Testing potential to deploy ubuntubridge in transparent mode, with IPTABLES FORWARD rules, as an NFV/Microservice for lab/demonstration environment.

Goal: block telnet traffic from Client to anything beyond the ubuntubridge. Note: with default DROP rules for INPUT, OUTPUT, and FORWARD, all traffic passes through bridge (icmp, routing protocol traffic, etc.)

Results:

Regardless of IPTABLES rules, all telnet traffic is allowed through the Ubuntu transparent bridge. Client can telnet to virtualrouter2 regardless of IPTABLES rules in place on the ubuntubridge device (jfv-telnet). All documentation I have been able to find indicate that IPv4 forwarding in Ubuntu 16.04 in transparent bridge mode is processed by IPTABLES once the following settings are put in place on the ubuntubridge device (note: I am aware that the tcp specific FORWARD rules are redundant for this scenario):

lab@jfv-telnet:~$ sudo cat /proc/sys/net/ipv4/ip_forward
1


lab@jfv-telnet:~$ sudo iptables -S
-P INPUT DROP
-P FORWARD DROP
-P OUTPUT DROP
-A FORWARD -p tcp -m tcp --sport 23 -j DROP
-A FORWARD -p tcp -m tcp --dport 23 -j DROP

lab@jfv-telnet:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 52:54:00:1b:a7:f3  
          inet addr:10.10.10.253  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::5054:ff:fe1b:a7f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:112100 (112.1 KB)  TX bytes:8164 (8.1 KB)


ens3      Link encap:Ethernet  HWaddr 52:54:00:f2:00:03  
          inet6 addr: fe80::5054:ff:fef2:3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2001 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36875 (36.8 KB)  TX bytes:125885 (125.8 KB)


ens4      Link encap:Ethernet  HWaddr 52:54:00:1b:a7:f3  
          inet6 addr: fe80::5054:ff:fe1b:a7f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:523 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114213 (114.2 KB)  TX bytes:49345 (49.3 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:284400 (284.4 KB)  TX bytes:284400 (284.4 KB)


lab@jfv-telnet:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


auto br0
iface br0 inet static
address 10.10.10.253
netmask 255.255.255.0
pre-up ifconfig ens3 down
pre-up ifconfig ens4 down
pre-up brctl addbr br0
pre-up brctl addif br0 ens3
pre-up brctl addif br0 ens4
pre-up ifconfig ens3 0.0.0.0
pre-up ifconfig ens4 0.0.0.0
post-down ifconfig ens3 down
post-down ifconfig ens4 down
post-down ifconfig br0 down
post-down brctl delif br0 ens3
post-down brctl delif br0 ens4
post-down brctl delbr br0


Question:

What steps do I need to take to further troubleshoot this scenario, or what settings am I missing in Ubuntu 16.04 to process transit IPv4 traffic through the IPTABLES rules when used as a transparent bridge?

Thanks,

MP

---

