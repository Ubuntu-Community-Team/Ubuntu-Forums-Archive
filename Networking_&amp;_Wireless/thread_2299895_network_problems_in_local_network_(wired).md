---
title: "network problems in local network (wired)"
date: 2015-10-22
forum: Networking &amp; Wireless
---

### Post by andre.werthmann on 2015-10-22
Hello,
I have a network problem in LAN.
IP of the router is 10.0.2.1 (Linux Ubuntu).
(ifconfig:


```

eth0      Link encap:Ethernet  HWaddr 90:e2:ba:98:9c:2b  
          inet addr:10.0.2.1  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::92e2:baff:fe98:9c2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16302086 errors:4 dropped:0 overruns:0 frame:2
          TX packets:17489404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13964006780 (13.9 GB)  TX bytes:16493383298 (16.4 GB)

```


If I ping a wired local machine from the router i get:


```

PING 10.0.2.2 (10.0.2.2) 56(84) bytes of data.
64 bytes from 10.0.2.2: icmp_seq=1 ttl=64 time=41.3 ms
64 bytes from 10.0.2.2: icmp_seq=2 ttl=64 time=37.4 ms
64 bytes from 10.0.2.2: icmp_seq=3 ttl=64 time=35.9 ms
64 bytes from 10.0.2.2: icmp_seq=4 ttl=64 time=34.9 ms
64 bytes from 10.0.2.2: icmp_seq=5 ttl=64 time=33.9 ms
64 bytes from 10.0.2.2: icmp_seq=6 ttl=64 time=32.8 ms
64 bytes from 10.0.2.2: icmp_seq=7 ttl=64 time=31.0 ms
64 bytes from 10.0.2.2: icmp_seq=8 ttl=64 time=29.8 ms
64 bytes from 10.0.2.2: icmp_seq=9 ttl=64 time=27.9 ms
64 bytes from 10.0.2.2: icmp_seq=10 ttl=64 time=26.9 ms
64 bytes from 10.0.2.2: icmp_seq=11 ttl=64 time=25.9 ms
64 bytes from 10.0.2.2: icmp_seq=12 ttl=64 time=24.9 ms
64 bytes from 10.0.2.2: icmp_seq=13 ttl=64 time=26.7 ms
64 bytes from 10.0.2.2: icmp_seq=14 ttl=64 time=22.1 ms
64 bytes from 10.0.2.2: icmp_seq=15 ttl=64 time=20.9 ms
64 bytes from 10.0.2.2: icmp_seq=16 ttl=64 time=18.9 ms
64 bytes from 10.0.2.2: icmp_seq=17 ttl=64 time=17.9 ms
64 bytes from 10.0.2.2: icmp_seq=18 ttl=64 time=15.9 ms
64 bytes from 10.0.2.2: icmp_seq=19 ttl=64 time=14.8 ms
64 bytes from 10.0.2.2: icmp_seq=20 ttl=64 time=12.9 ms
64 bytes from 10.0.2.2: icmp_seq=21 ttl=64 time=11.9 ms
64 bytes from 10.0.2.2: icmp_seq=22 ttl=64 time=12.4 ms
64 bytes from 10.0.2.2: icmp_seq=23 ttl=64 time=11.0 ms
64 bytes from 10.0.2.2: icmp_seq=24 ttl=64 time=9.80 ms
64 bytes from 10.0.2.2: icmp_seq=25 ttl=64 time=7.97 ms
64 bytes from 10.0.2.2: icmp_seq=26 ttl=64 time=6.90 ms
64 bytes from 10.0.2.2: icmp_seq=27 ttl=64 time=4.92 ms
64 bytes from 10.0.2.2: icmp_seq=28 ttl=64 time=2.92 ms
64 bytes from 10.0.2.2: icmp_seq=29 ttl=64 time=98.4 ms
64 bytes from 10.0.2.2: icmp_seq=30 ttl=64 time=97.5 ms
64 bytes from 10.0.2.2: icmp_seq=31 ttl=64 time=98.4 ms
64 bytes from 10.0.2.2: icmp_seq=32 ttl=64 time=94.2 ms
64 bytes from 10.0.2.2: icmp_seq=33 ttl=64 time=93.0 ms
64 bytes from 10.0.2.2: icmp_seq=34 ttl=64 time=92.0 ms
64 bytes from 10.0.2.2: icmp_seq=35 ttl=64 time=90.9 ms
64 bytes from 10.0.2.2: icmp_seq=36 ttl=64 time=90.0 ms
64 bytes from 10.0.2.2: icmp_seq=37 ttl=64 time=89.0 ms
64 bytes from 10.0.2.2: icmp_seq=38 ttl=64 time=88.0 ms
64 bytes from 10.0.2.2: icmp_seq=39 ttl=64 time=87.0 ms
64 bytes from 10.0.2.2: icmp_seq=40 ttl=64 time=86.0 ms
64 bytes from 10.0.2.2: icmp_seq=41 ttl=64 time=84.9 ms
64 bytes from 10.0.2.2: icmp_seq=42 ttl=64 time=83.9 ms
64 bytes from 10.0.2.2: icmp_seq=43 ttl=64 time=83.0 ms
64 bytes from 10.0.2.2: icmp_seq=44 ttl=64 time=82.0 ms
64 bytes from 10.0.2.2: icmp_seq=45 ttl=64 time=83.5 ms
64 bytes from 10.0.2.2: icmp_seq=46 ttl=64 time=79.5 ms
64 bytes from 10.0.2.2: icmp_seq=47 ttl=64 time=78.0 ms
64 bytes from 10.0.2.2: icmp_seq=48 ttl=64 time=76.9 ms
64 bytes from 10.0.2.2: icmp_seq=49 ttl=64 time=75.0 ms
64 bytes from 10.0.2.2: icmp_seq=50 ttl=64 time=74.0 ms
64 bytes from 10.0.2.2: icmp_seq=51 ttl=64 time=72.9 ms
64 bytes from 10.0.2.2: icmp_seq=52 ttl=64 time=71.0 ms
64 bytes from 10.0.2.2: icmp_seq=53 ttl=64 time=72.5 ms
64 bytes from 10.0.2.2: icmp_seq=54 ttl=64 time=70.8 ms
64 bytes from 10.0.2.2: icmp_seq=55 ttl=64 time=66.4 ms
64 bytes from 10.0.2.2: icmp_seq=56 ttl=64 time=64.9 ms
64 bytes from 10.0.2.2: icmp_seq=57 ttl=64 time=65.5 ms
64 bytes from 10.0.2.2: icmp_seq=58 ttl=64 time=63.8 ms
64 bytes from 10.0.2.2: icmp_seq=59 ttl=64 time=60.0 ms
64 bytes from 10.0.2.2: icmp_seq=60 ttl=64 time=58.9 ms
64 bytes from 10.0.2.2: icmp_seq=61 ttl=64 time=57.9 ms
64 bytes from 10.0.2.2: icmp_seq=62 ttl=64 time=56.9 ms
64 bytes from 10.0.2.2: icmp_seq=63 ttl=64 time=58.4 ms
64 bytes from 10.0.2.2: icmp_seq=64 ttl=64 time=54.4 ms
64 bytes from 10.0.2.2: icmp_seq=65 ttl=64 time=53.0 ms
64 bytes from 10.0.2.2: icmp_seq=66 ttl=64 time=51.8 ms
64 bytes from 10.0.2.2: icmp_seq=67 ttl=64 time=50.0 ms
64 bytes from 10.0.2.2: icmp_seq=68 ttl=64 time=48.8 ms
64 bytes from 10.0.2.2: icmp_seq=69 ttl=64 time=46.9 ms
64 bytes from 10.0.2.2: icmp_seq=70 ttl=64 time=45.9 ms
64 bytes from 10.0.2.2: icmp_seq=71 ttl=64 time=43.9 ms
64 bytes from 10.0.2.2: icmp_seq=72 ttl=64 time=42.9 ms
64 bytes from 10.0.2.2: icmp_seq=73 ttl=64 time=41.9 ms
64 bytes from 10.0.2.2: icmp_seq=74 ttl=64 time=40.9 ms
64 bytes from 10.0.2.2: icmp_seq=75 ttl=64 time=42.4 ms
64 bytes from 10.0.2.2: icmp_seq=76 ttl=64 time=38.4 ms
64 bytes from 10.0.2.2: icmp_seq=77 ttl=64 time=36.9 ms
64 bytes from 10.0.2.2: icmp_seq=78 ttl=64 time=35.9 ms
64 bytes from 10.0.2.2: icmp_seq=79 ttl=64 time=34.7 ms
64 bytes from 10.0.2.2: icmp_seq=80 ttl=64 time=32.9 ms
64 bytes from 10.0.2.2: icmp_seq=81 ttl=64 time=31.9 ms
64 bytes from 10.0.2.2: icmp_seq=82 ttl=64 time=30.9 ms
64 bytes from 10.0.2.2: icmp_seq=83 ttl=64 time=30.0 ms
64 bytes from 10.0.2.2: icmp_seq=84 ttl=64 time=31.4 ms
64 bytes from 10.0.2.2: icmp_seq=85 ttl=64 time=27.4 ms
64 bytes from 10.0.2.2: icmp_seq=86 ttl=64 time=25.8 ms
64 bytes from 10.0.2.2: icmp_seq=87 ttl=64 time=23.9 ms
64 bytes from 10.0.2.2: icmp_seq=88 ttl=64 time=22.8 ms
64 bytes from 10.0.2.2: icmp_seq=89 ttl=64 time=20.9 ms
64 bytes from 10.0.2.2: icmp_seq=90 ttl=64 time=20.1 ms
64 bytes from 10.0.2.2: icmp_seq=91 ttl=64 time=18.8 ms
64 bytes from 10.0.2.2: icmp_seq=92 ttl=64 time=16.9 ms
64 bytes from 10.0.2.2: icmp_seq=93 ttl=64 time=17.4 ms
64 bytes from 10.0.2.2: icmp_seq=94 ttl=64 time=15.5 ms
64 bytes from 10.0.2.2: icmp_seq=95 ttl=64 time=11.6 ms
64 bytes from 10.0.2.2: icmp_seq=96 ttl=64 time=12.4 ms
64 bytes from 10.0.2.2: icmp_seq=97 ttl=64 time=10.8 ms
64 bytes from 10.0.2.2: icmp_seq=98 ttl=64 time=8.94 ms

```


As you see there is no packet loss. But the ping latency is way too high (should by < 1ms) and it changes
slowly from 100 ms down to 2 ms and then jumps back to 100 ms .. and it repeats that way.
What can cause this ?


The network switch behind the Router is a new one.
Ping times from a machine to an other machine connected to the switch is alway < 1ms.
Pinging the router gives the high inconistently ping times above.


Please help.

---

### Post by TheFu on 2015-10-22
Welcome to the forums.

Try a different cable.
Try a different port on the switch - swap a faster connection with the one having issues. Did the problem move too or not?
If some clients are faster than others, the issue is likely on the client-side. Right?

It isn't clear if everything is wired or how the "router" is connected. More info about the hardware would help us guess better.  For example, pinging "from" the router seems backwards.

---

### Post by andre.werthmann on 2015-10-23
Everything is wired. Pings between all clients are fast (<1ms).
Only pings from the router to all the clients and pings from all the clients to the router are slow (between 2 and 100ms, stepping down 1ms every second).
I switched the cable and moved the router to an other port on the switch, nothing helps.

But yesterday I have found out something.

Sometimes the kernel prints in syslog:

```

[  525.244297] irq 18: nobody cared (try booting with the "irqpoll" option)
[  525.244705] Pid: 0, comm: swapper Not tainted 2.6.32-34-server #77-Ubuntu
[  525.244708] Call Trace:
[  525.244710]  <IRQ>  [<ffffffff810c82bb>] __report_bad_irq+0x2b/0xa0
[  525.244722]  [<ffffffff810c84bc>] note_interrupt+0x18c/0x1d0
[  525.244726]  [<ffffffff810c8bbd>] handle_fasteoi_irq+0xdd/0x100
[  525.244731]  [<ffffffff81015cd2>] handle_irq+0x22/0x30
[  525.244736]  [<ffffffff815602fc>] do_IRQ+0x6c/0xf0
[  525.244739]  [<ffffffff81013ad3>] ret_from_intr+0x0/0x11
[  525.244741]  <EOI>  [<ffffffff813120f5>] ? acpi_idle_enter_bm+0x296/0x2ca
[  525.244750]  [<ffffffff813120ee>] ? acpi_idle_enter_bm+0x28f/0x2ca
[  525.244756]  [<ffffffff81451aa7>] ? cpuidle_idle_call+0xa7/0x140
[  525.244761]  [<ffffffff81011e43>] ? cpu_idle+0xb3/0x110
[  525.244766]  [<ffffffff81552f1a>] ? start_secondary+0xa8/0xaa
[  525.244768] handlers:
[  525.244991] [<ffffffffa003a9d0>] (e1000_intr+0x0/0x120 [e1000])
[  525.245601] Disabling IRQ #18

```


Then the latency and throughput is very bad.
After rebooting the router it is good for some minutes / hours (depending on network load).

Now I'm trying the linux kernel boot option "irqpoll". Fingers crossed the latency is good now since 13 hours.

But I would like to know what is the root cause of this problem...

---

### Post by TheFu on 2015-10-23
$ sudo lshw -C network
please.

---

### Post by andre.werthmann on 2015-10-26
```

*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 10
       serial: b0:48:7a:84:78:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:e000(size=256) memory:fe680000-fe6800ff memory:fe660000-fe67ffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: 82541PI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:03:01.0
       logical name: eth0
       version: 05
       serial: 90:e2:ba:93:77:ce
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=10.0.2.1 latency=32 link=yes mingnt=255 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:18 memory:fe640000-fe65ffff memory:fe620000-fe63ffff ioport:e100(size=64) memory:fe600000-fe61ffff(prefetchable)

```

---

### Post by TheFu on 2015-10-26
[https://stackoverflow.com/questions/13861282/understanding-kernel-message-nobody-cared-try-booting-with-the-irqpoll-optio](https://stackoverflow.com/questions/13861282/understanding-kernel-message-nobody-cared-try-booting-with-the-irqpoll-optio)

Could the Intel PRO/1000 card be failing?  Reseat it. Move it to a different slot. Replace it.  Try in that order.

---

