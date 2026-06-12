---
title: "Lots of collisions, very little traffic"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by editrix on 2008-11-22
I've got a Kubuntu Hardy box connected to an old Win98 box with a crossover cable. I transfer files between the two with FTP. The IP addresses are static, manually assigned.

The connection is horribly slow. I know it should be much faster, because it was when I had the same setup, except with a Dapper box (different computer). That one was set up for me by someone who's no longer around to help, so I've been bumbling around on my own and not getting very far. Everything I've found assumes a shared internet connection, but I don't have that. I'm on dialup on the Hardy box.

My ifconfig shows a lot of collisions for a few small file transfers:

```
eth0      Link encap:Ethernet  HWaddr 00:40:ca:3b:c5:5b
          inet addr:192.168.0.130  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe3b:c55b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1081 errors:0 dropped:0 overruns:0 carrier:0
          collisions:203 txqueuelen:1000
          RX bytes:48884 (47.7 KB)  TX bytes:882674 (861.9 KB)
          Interrupt:17 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50358 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:31184077 (29.7 MB)  TX bytes:31184077 (29.7 MB)
```
It strikes me there shouldn't be any collisions, since the only traffic is between the 2 computers, but I don't even know if that's really the problem. If it's any help in diagnosing, after I disconnected I looked at dmesg and found:
```

[101393.938846] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[101393.939371] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[101404.468814] eth0: no IPv6 routers present
```
and  lspci -v (with eth0 up) returns:

```
01:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9050
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at c800 [size=256]
        Memory at ec011000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at ec000000 [disabled] [size=64K]
        Capabilities: [50] Power Management version 2
```

In searching, I've learned about possible problems with these Realtek cards, and possible bugs in Hardy's networking, and something about changing half-duplex to duplex, but I don't understand any of it, and have no idea how to change the duplexing.

Any help will be much appreciated.

---

### Post by editrix on 2008-11-30
Well, I installed a server on the Win98 box and used Konqueror as the FTP client, and everything was as fast as it should be. But I'd still like to know what's causing the collisions on the Linux side.

---

