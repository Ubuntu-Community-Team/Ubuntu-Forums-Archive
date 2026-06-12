---
title: "Ubuntu Server 14.04.4 LTS problem with public static ip"
date: 2017-02-16
forum: Networking &amp; Wireless
---

### Post by poliman-pl on 2017-02-16
I have server based on Ubuntu Server which has four network cards - from em1 to em4. In /etc/network/interfaces I put:
auto em1 em4
iface em1 inet static
        address 192.168.100.202
        network 192.168.100.0
        netmask 255.255.255.0
        broadcast 192.168.100.255
        gateway 192.168.100.2               #not sure that here should  be gateway if below is another gateway, this is local router in company
        dns-nameservers 192.168.100.2

#values provided by isp
iface em4 inet static
        address 31.X.X.180
        network 31.X.X.176
        netmask 255.255.255.248
        gateway 31.X.X.177             #not sure that here should be gateway if above is another gateway
        dns-nameservers 193.106.244.10 193.106.244.20
[HR][/HR]**ifconfig command output:**
em1       Link encap:Ethernet  HWaddr d8:9d:67:2a:c9:18
          inet addr:192.168.100.202  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::da9d:67ff:fe2a:c918/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19310863 errors:0 dropped:1942387 overruns:0 frame:0
          TX packets:1929148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3446416045 (3.4 GB)  TX bytes:1699818696 (1.6 GB)
          Interrupt:59

em2       Link encap:Ethernet  HWaddr d8:9d:67:2a:c9:19
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:126662 (126.6 KB)  TX bytes:8408 (8.4 KB)
          Interrupt:60

em4       Link encap:Ethernet  HWaddr d8:9d:67:2a:c9:1b
          inet addr:31.X.X.180  Bcast:31.X.X.183  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:330135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:78394465 (78.3 MB)  TX bytes:2429561 (2.4 MB)
          Interrupt:60

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:270476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:85851060 (85.8 MB)  TX bytes:85851060 (85.8 MB)

[HR][/HR]**ip link show command output:**
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: em1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether d8:9d:67:2a:c9:18 brd ff:ff:ff:ff:ff:ff
3: em2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DEFAULT group default qlen 1000
    link/ether d8:9d:67:2a:c9:19 brd ff:ff:ff:ff:ff:ff
4: em3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether d8:9d:67:2a:c9:1a brd ff:ff:ff:ff:ff:ff
5: em4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether d8:9d:67:2a:c9:1b brd ff:ff:ff:ff:ff:ff

[HR][/HR]route command output:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default           router            0.0.0.0           UG    0        0       0    em1
31.X.X.176      *               255.255.255.248 U      0       0        0    em4
192.168.100.0  *               255.255.255.0    U     0        0        0    em1
[HR][/HR]**route -n command output:**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0          192.168.100.2   0.0.0.0          UG    0      0        0     em1
31.X.X.176     0.0.0.0         255.255.255.248 U     0      0        0     em4
192.168.100.0   0.0.0.0         255.255.255.0  U     0      0        0     em1
[HR][/HR]**ufw status command output:**
Status: inactive
[HR][/HR]**tracert command output (from windows host from outside network):**
tracert 31.X.X.180

Tracing route to 31-X-X-180.noc.fibertech.net.pl [31.X.X.180]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  192.168.101.1
  2     4 ms     3 ms     2 ms  1.1.1.1
  3     5 ms     7 ms     5 ms  host17201.internet-examps.pl [93.X.X.123]
  4    12 ms    10 ms    11 ms  vc3s.pl [89.25.159.158]
  5    11 ms    11 ms    11 ms  31-X-X-22.net.pl [31.X.X.22]
  6     *        *        *     Request timed out.
  7     *        *        *     Request timed out.
  8     *        *        *     Request timed out.

other steps like 6,7,8 until 30.
[HR][/HR]**ping command output (from windows host outside network):**
C:\Users\poli003>ping 31.X.X.180

Pinging 31.X.X.180 with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 31.X.X.180:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),


[HR][/HR]And finally my problem (I suppose You know what's going on):
Server has local ip address and public ip address. But this public ip is  not reachable in network. I can't ping this address, put this ip in web  browser should show login panel but this not happen. Firewall (ufw) is  disabled at the moment until I resolve this problem. Routes which show  route command are default. What is configured wrong? Besides I have no  idea why ifconfig command output shows em1, em2, em4 and lo if I have  configured only em1, em4 and loopback. If any more informations You need -  say.

---

### Post by wildmanne39 on 2017-02-16
Thread closed. Please do not post duplicates, it dilutes community effort.

---

