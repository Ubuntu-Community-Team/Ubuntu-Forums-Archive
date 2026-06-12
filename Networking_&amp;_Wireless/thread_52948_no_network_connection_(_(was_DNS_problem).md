---
title: "no network connection :( (was DNS problem?)"
date: 2005-07-29
forum: Networking &amp; Wireless
---

### Post by one_ro on 2005-07-29
Dear list,

I like Kubuntu very very much and I'd like to see it fully working. I installed it (Hoary Hedgehog) about three or four times paying attention to any useful installation step, on two different computers but I just cannot configure it for internet.

During the installation I set the network card details:
IP: 192.268.1.105
Mask: 255.255.255.0
Gateway: 192.168.1.1
DNS: 193.231.12.65

Trying to set some other IP addresses for DNS using Control Panel / Internet & Network /  Network Settings (in Administrator mode) is unfortunately futile; it is complaining that I should set an alias first (but the Add botton from the DNS list _does not_ offer this).

When pinging some other computers in the LAN I get responses; the gateway (which is also a router) is also responding; only the DNS server does not respond.

Below you can find the output from "ifconfig -a" and "route -n" (and I have to really type it since I can't connect to Kubuntu from other computer, sigh):

ifconfig -a

eth0     Link encap: Ethernet   HWaddr 00:0C:29:95:A1:77
            inet addr:192.168.1.105  Bcast:192.168.1.255   Mask:255.255.255.0
            inet6 addr: fe80::20c:29ff:fe95:a177/64  Scope:Link
            UP BROADCAST RUNNING MULTICAST   MTU:1500   Metric:1
            RX packets:18 errors:0 dropped:0 overruns:0 frame:0
            TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes :1496 (1.4 KiB)   TX Bytes:1276 (1.2 KiB)
            Interrupt:18 Base address:0x1400

lo         Link encap:Local Loopback
            inet addr:127.0.0.1   Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING MTU:16436  Metric 1
            RX packets:18 errors:0 dropped:0 overruns:0 frame:0
            TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes :0 (0.0 b)   TX Bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
            NOAPR  MTU:1480 Metric:1
            RX packets:18 errors:0 dropped:0 overruns:0 frame:0
            TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes :0 (0.0 b)   TX Bytes:0 (0.0 b)




route -n
Kernel IP routing table
Destination         Gateway          Genmask             Flags     Metric       Ref           Use         Iface
192.168.1.0        0.0.0.0              255.255.255.0     U            0               0              0             eth0
0.0.0.0                 192.168.1.1     0.0.0.0                 UG         0               0              0             eth0

I guess I typed everything correct. Please please help, any hint greatly appreciated.
TIA,
Adrian

---

