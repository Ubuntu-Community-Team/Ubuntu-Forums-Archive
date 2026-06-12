---
title: "Ubuntu 20.04 : ethernet does not work"
date: 2021-04-24
forum: Networking &amp; Wireless
---

### Post by maketopsite on 2021-04-24
I've tried commands here: [URL="https://serverfault.com/questions/880950/network-issue-ifup-says-unknown-interface"]https://serverfault.com/questions/880950/network-issue-ifup-says-unknown-interface


[/URL]```
ping -c3 8.8.8.8
ping: connect: Network is unreachable

```

```
ip link ls
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether [some valid address] brd ff:ff:ff:ff:ff:ff
3: wlp5s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether [some valid address] brd ff:ff:ff:ff:ff:ff

```

```
ip address
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether [some valid address] brd ff:ff:ff:ff:ff:ff
    inet6 [some valid address]/64 scope global dynamic mngtmpaddr 
       valid_lft 86382sec preferred_lft 3582sec
    inet6 [some valid address]/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp5s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether [some valid address] brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.33/24 brd 10.0.0.255 scope global dynamic noprefixroute wlp5s0
       valid_lft 85676sec preferred_lft 85676sec

```

```
03:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 13)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Killer E220x Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7d00000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at c000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [c0] MSI: Enable- Count=1/16 Maskable+ 64bit+
    Capabilities: [d8] MSI-X: Enable+ Count=16 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ...
    Kernel driver in use: alx
    Kernel modules: alx

```

---

### Post by TheFu on 2021-04-24
some valid address?
IP addresses aren't secrets. Hard to help when we can't see basic information.
If you don't want to show the exact IP .... put in one that is similar.

And probably need to disable the wifi adapter. In my settings, wired ethernet has priority, but only 1 (wired or wifi) will be enabled at a time to avoid complex situations.

20.04 doesn't use ifup/down. That was deprecated. Use **ip a** and **ip route|column -t** For example:
```
$ ip route|column -t
default         via  172.22.22.1  dev    ens3    proto  static
10.168.29.0/24  dev  mpqemubr0    proto  kernel  scope  link    src  10.168.29.1  linkdown
172.17.0.0/16   dev  docker0      proto  kernel  scope  link    src  172.17.0.1   linkdown
172.22.22.0/24  dev  ens3         proto  kernel  scope  link    src  172.22.22.3
```
Nothing super secret in there.

[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
has troubleshooting steps IN ORDER to be completed.  Do those.  IN ORDER, please and report back.

---

### Post by slickymaster on 2021-04-26
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2021-04-26
> some valid address?
IP addresses aren't secrets. Hard to help when we can't see basic information.That's the redacted MAC address, not an IP address, and I recommend that it be obscured.

Here is a slightly less obscured example from my machine:

```
2: enp0s25: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether [COLOR="#FF0000"]xx:f7:28:ae:83:xx[/COLOR] brd ff:ff:ff:ff:ff:ff
```

---

### Post by TheFu on 2021-04-26
Most of my systems are VMs, so I set the MAC last few characters to map to the IP on the subnet for human convenience.
xx:f7:28:ae:83:11  ---> 172.17.0.11
For real hardware, I might change a few parts to aa:bb .... so others know it is a MAC without having to memorize every typical line output.

Anyways, would love to see the troubleshooting steps from the OP.  Can't tell if it is a computer, switch, router, ISP issue based on 1 internet ping attempt.

---

### Post by maketopsite on 2021-05-07
It was solved after```
 dhclient enp3s0
```

---

