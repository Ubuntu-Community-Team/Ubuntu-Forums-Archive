---
title: "DHCP random failures"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by Almindor on 2007-05-08
Hey guys I have a weird problem since updating to Fiesty Fawn.

My configuration:

Desktop PC with 2 ethernet NICs (both working) set as:

eth0 - DHCP -- this is the "internet" interface, configured to use DHCP. It is bound to my 1st NIC and my ISP is Chello (requires MAC to be this one)

eth1 - statis set to level C private (192...). I use FireStarter to share this one without a DHCP server on this machine (it's all static).

My problem:

In about 1/3 of boots, my eth0 doesn't get it's IP address from the DHCP server. The weird thing is, that just turning eth0 off and on is enough to get it working again. (through the system/.../network visual thing, not ifconfig).

I have no clue what does this but it started after I updated to Fiesty (along .. other strange problems but not network related). FireStarter isn't used all the time, I only turn it on when I need my laptop to get net from this 

Here's some info stuff (when it works, when it doesn't the difference is only that eth0 has no IPv4 address):

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:50:8D:47:53:19  
          inet addr:85.216.134.48  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::250:8dff:fe47:5319/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1913 errors:0 dropped:12 overruns:0 frame:0
          TX packets:1928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1436577 (1.3 MiB)  TX bytes:277513 (271.0 KiB)
          Interrupt:18 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:E0:4C:30:C3:95  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.102.1  Bcast:172.16.102.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.20.1  Bcast:172.16.20.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Route -n:

172.16.20.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.16.102.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
85.216.128.0    0.0.0.0         255.255.248.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         85.216.128.1    0.0.0.0         UG    0      0        0 eth0

iptables -L (as root):

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

