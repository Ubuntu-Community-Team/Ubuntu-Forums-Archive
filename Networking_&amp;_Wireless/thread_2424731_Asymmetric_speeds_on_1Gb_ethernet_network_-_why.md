---
title: "Asymmetric speeds on 1Gb ethernet network - why?"
date: 2019-08-13
forum: Networking &amp; Wireless
---

### Post by Waldo_Nell on 2019-08-13
I have an Ubuntu Linux machine and an iMac Pro.  Ubuntu is 19.04 x64.  Fast i5-7600K and 16GB of RAM, NVMe SSD etc.  Both are connected with Cat 5e to an Ubiquiti switch.  Why am I getting asymmetric results in iperf?  I get the same with iperf3 and also if I change window size to bigger values:

```
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 1.00 MByte (WARNING: requested  512 KByte)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.0.30, TCP port 5001
TCP window size: 1.00 MByte (WARNING: requested  512 KByte)
------------------------------------------------------------
[  5] local 192.168.0.10 port 58770 connected with 192.168.0.30 port 5001
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-10.0 sec   881 MBytes   739 Mbits/sec
[  4] local 192.168.0.10 port 5001 connected with 192.168.0.30 port 60297
[  4]  0.0-10.0 sec  1.09 GBytes   934 Mbits/sec

```

There is a 200Mbps discrepancy.  Why?

When I do the same test between a MacBook Pro and the iMac Pro over wired I get symmetric speeds of 940Mbps.

The ethernet adapter on Linux:

```
Settings for enp0s31f6:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Supported FEC modes: Not reported
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Advertised FEC modes: Not reported
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 2
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: on (auto)
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes



```

Edit: UDP seems to work more symmetrical:

```

------------------------------------------------------------
Server listening on UDP port 5001
Binding to local address 192.168.0.10
Receiving 1470 byte datagrams
UDP buffer size:  208 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.0.30, UDP port 5001
Binding to local address 192.168.0.10
Sending 1470 byte datagrams, IPG target: 1.18 us (kalman adjust)
UDP buffer size:  208 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.10 port 42164 connected with 192.168.0.30 port 5001
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  1.11 GBytes   952 Mbits/sec
[  4] Sent 809725 datagrams
[  4] Server Report:
[  4]  0.0-10.0 sec  1.11 GBytes   952 Mbits/sec  64786.432 ms 2145864389/2146673923 (1e+02%)
[  4] 0.00-10.00 sec  1 datagrams received out-of-order
[  3] local 192.168.0.10 port 5001 connected with 192.168.0.30 port 53980
[  3]  0.0-10.2 sec  1.11 GBytes   927 Mbits/sec  13.666 ms 2145476882/2146284995 (1e+02%)

```

---

### Post by Waldo_Nell on 2019-08-13
I might have just solved it.  I found [this thread]("https://forum.manjaro.org/t/solved-only-half-gigabit-eth-with-intel-i219-lm-v-under-kernel-4-14-to-4-19/58886"), tried disabling tso and gso offloading:

```
ethtool -K enp0s31f6 tso off gso off
```

Did a test again: 
```

------------------------------------------------------------
Server listening on TCP port 5001
Binding to local address 192.168.0.10
TCP window size:  250 KByte (WARNING: requested  125 KByte)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.0.30, TCP port 5001
Binding to local address 192.168.0.10
TCP window size:  250 KByte (WARNING: requested  125 KByte)
------------------------------------------------------------
[  5] local 192.168.0.10 port 36989 connected with 192.168.0.30 port 5001
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-10.0 sec  1.08 GBytes   931 Mbits/sec
[  4] local 192.168.0.10 port 5001 connected with 192.168.0.30 port 53768
[  4]  0.0-10.0 sec  1.08 GBytes   928 Mbits/sec
```

---

### Post by praseodym on 2019-08-14
What hardware is it?
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
```

---

### Post by Waldo_Nell on 2019-08-14
```
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
        Subsystem: ASRock Incorporation Ethernet Connection (2) I219-V [1849:15b8]
        Kernel driver in use: e1000e
        Kernel modules: e1000e
```

```
e1000e                245760  0
```

```
enp0s31f6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.24  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::7285:c2ff:fe3a:ae18  prefixlen 64  scopeid 0x20<link>
        ether 70:85:c2:3a:a2:18  txqueuelen 1000  (Ethernet)
        RX packets 10542930  bytes 9915138005 (9.9 GB)
        RX errors 0  dropped 331  overruns 0  frame 0
        TX packets 13614376  bytes 19449638563 (19.4 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xdc200000-dc220000



```

---

### Post by praseodym on 2019-08-14
```
enp0s31f6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.24  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::7285:c2ff:fe3a:ae18  prefixlen 64  scopeid 0x20<link>
        ether 70:85:c2:3a:a2:18  txqueuelen 1000  (Ethernet)
        RX packets 10542930  bytes 9915138005 (9.9 GB)
        RX errors 0  dropped [COLOR="#FF0000"]331[/COLOR]  overruns 0  frame 0
        TX packets 13614376  bytes 19449638563 (19.4 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xdc200000-dc220000
```
Check the mtu value of your ISP and the nameserver resolution

---

### Post by Waldo_Nell on 2019-08-14
What does my ISP have to do with this?  My issue is with local LAN speed.  I do not use Jumbo frames on the LAN. Nameserver has nothing to do with this as I am performing a speed test using IP addresses.

---

### Post by baijea on 2020-07-02
[QUOTE=Waldo_Nell;13879472]I might have just solved it.  I found [this thread]("https://forum.manjaro.org/t/solved-only-half-gigabit-eth-with-intel-i219-lm-v-under-kernel-4-14-to-4-19/58886"), tried disabling tso and gso offloading:

```
ethtool -K enp0s31f6 tso off gso off
```


Thank you!! This solved the same problem here too.

---

