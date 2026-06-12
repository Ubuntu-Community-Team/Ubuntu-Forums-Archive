---
title: "Firefox on 16.04 does not connect to internet"
date: 2017-09-23
forum: Networking &amp; Wireless
---

### Post by Mike_Brown on 2017-09-23
Firefox on my Ubuntu 16.04LTS computer connects to my router but Firefox gives a 'Server not found' error for every website. I logged on to my router as Administrator, so I know that my NIC, cables & router are working. 

My 2 Windows computers, 1 Ipad, 1 Iphone & 1 Android phone all connect to any site I attempt.

Thanks for any assistance.

Below are returns from lshw -c network, ifconfig & iwconfig requests:

```

mike@Myth:~$ sudo lshw -c network
[sudo] password for mike:
  *-network              
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 04
       serial: ac:16:2d:10:a8:94
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-4 ip=192.168.1.201 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:26 memory:f7f00000-f7f1ffff memory:f7f39000-f7f39fff ioport:f040(size=32)
 
mike@Myth:~$ ifconfig
eno1      Link encap:Ethernet  HWaddr ac:16:2d:10:a8:94 
          inet addr:192.168.1.201  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7d9b:49cd:350a:8753/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11936 (11.9 KB)  TX bytes:9145 (9.1 KB)
          Interrupt:20 Memory:f7f00000-f7f20000
 
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:367220 (367.2 KB)  TX bytes:367220 (367.2 KB)
 
mike@Myth:~$ iwconfig
lo        no wireless extensions.
 
eno1      no wireless extensions.

```

---

### Post by ajgreeny on 2017-09-23
Duplicate of [https://ubuntuforums.org/showthread.php?t=2372132&p=13689321#post13689321](https://ubuntuforums.org/showthread.php?t=2372132&p=13689321#post13689321)

Thread closed.
**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help.

---

