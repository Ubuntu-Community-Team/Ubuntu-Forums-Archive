---
title: "Slow LAN Transfer - Fast Internet Transfer"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by UnresponsiveBeeVictim on 2007-12-10
Kinda weird here, I've got two computers both on wireless.

Dell 1705 - WinXP - Intel 3945ABG
AMD 64 3000+ - Ubuntu - Linksys WMP54GS
Netgear WNR845T Router no encryption

I'm able to download at 2mb/s on each from various sites on the internet no issue.  If I try to transfer from one to the other I get anywhere between 160-400k/s based on the method of transfer.  I've tried vsftpd, apache2, sftp, and bittorrent.  What kind of issues am I looking at here, it's obviously not limited by the wirless speed or link quality and I know the WinXP computer is not at fault because I've transferred to it at 11mb/s when I had my old slackware box.  There are no collisions on either computer.

---

### Post by Lostincyberspace on 2007-12-10
Make sure the mtu's are the same.

---

### Post by UnresponsiveBeeVictim on 2007-12-10
> **Lostincyberspace said:**
> Make sure the mtu's are the same.Both are 1500.
```

mars@universe:~/archive$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:39:08:B6:33
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:39ff:fe08:b633/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6654395 errors:0 dropped:1136457 overruns:0 frame:0
          TX packets:5528249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1290542131 (1.2 GB)  TX bytes:4046553088 (3.7 GB)
          Interrupt:10 Base address:0xc000
```

---

### Post by Lostincyberspace on 2007-12-10
ping the boxes from each other and see if their is an unusual pause from either. If one has a major delay then that will be the one with the problem. Otherwise we will have to try some thing else.

---

### Post by UnresponsiveBeeVictim on 2007-12-10
Windows to Linux:
```
C:\Documents and Settings\Jxxx Bxxx>ping 192.168.1.10 -n 10

Pinging 192.168.1.10 with 32 bytes of data:

Reply from 192.168.1.10: bytes=32 time=2ms TTL=64
Reply from 192.168.1.10: bytes=32 time=10ms TTL=64
Reply from 192.168.1.10: bytes=32 time=4ms TTL=64
Reply from 192.168.1.10: bytes=32 time=2ms TTL=64
Reply from 192.168.1.10: bytes=32 time=3ms TTL=64
Reply from 192.168.1.10: bytes=32 time=5ms TTL=64
Reply from 192.168.1.10: bytes=32 time<1ms TTL=64
Reply from 192.168.1.10: bytes=32 time=3ms TTL=64
Reply from 192.168.1.10: bytes=32 time=2ms TTL=64
Reply from 192.168.1.10: bytes=32 time=2ms TTL=64

Ping statistics for 192.168.1.10:
    Packets: Sent = 10, Received = 10, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 10ms, Average = 3ms
```
Windows to Router
```
C:\Documents and Settings\Jxxx Bxxx>ping 192.168.1.1

Pinging 192.168.1.1 with 32 bytes of data:

Reply from 192.168.1.1: bytes=32 time=3ms TTL=64
Reply from 192.168.1.1: bytes=32 time=2ms TTL=64
Reply from 192.168.1.1: bytes=32 time=2ms TTL=64
Reply from 192.168.1.1: bytes=32 time=3ms TTL=64

Ping statistics for 192.168.1.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 2ms, Maximum = 3ms, Average = 2ms
```


Linux to Windows
```
mars@universe:~/archive$ ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=128 time=1.27 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=128 time=73.7 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=128 time=0.876 ms
64 bytes from 192.168.1.3: icmp_seq=4 ttl=128 time=19.4 ms
64 bytes from 192.168.1.3: icmp_seq=5 ttl=128 time=43.4 ms
64 bytes from 192.168.1.3: icmp_seq=6 ttl=128 time=67.5 ms
64 bytes from 192.168.1.3: icmp_seq=7 ttl=128 time=91.5 ms
64 bytes from 192.168.1.3: icmp_seq=8 ttl=128 time=13.2 ms
64 bytes from 192.168.1.3: icmp_seq=9 ttl=128 time=37.4 ms
64 bytes from 192.168.1.3: icmp_seq=10 ttl=128 time=61.2 ms

--- 192.168.1.3 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9098ms
rtt min/avg/max/mdev = 0.876/40.974/91.578/30.304 ms

```
Linux to Router
```
mars@universe:~/archive$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.17 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.608 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.594 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.23 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.594/1.154/2.179/0.646 ms

```

---

### Post by UnresponsiveBeeVictim on 2007-12-11
There has to be an issue with the Linksys drivers.  I'm getting huge dropped packet counts.
```
 RX packets:7238466 errors:0 dropped:1193504 overruns:0 frame:0

```
```
mars@universe:~$ iwlist eth0 scanning
eth0      Scan completed :
          Cell 01 - Address: 00:18:4D:24:0B:7D
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=79/100  Signal level=-60 dBm  Noise level=-64 dBm
                    Extra: Last beacon: 156ms ago


```
```

mars@universe:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 02
       serial: 00:18:39:08:b6:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.1.10 latency=32 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```

---

### Post by UnresponsiveBeeVictim on 2007-12-11
Problem completely solved by moving to NDISWrapper.

---

### Post by Lostincyberspace on 2007-12-11
> **UnresponsiveBeeVictim said:**
> Problem completely solved by moving to NDISWrapper.
Well that is good I was just going to suggest trying it when I came back and you said all was fine.

---

