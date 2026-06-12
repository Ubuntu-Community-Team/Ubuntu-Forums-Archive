---
title: "Can't get my second network card to work on ubuntu server"
date: 2016-04-08
forum: Networking &amp; Wireless
---

### Post by Kevin_Goos on 2016-04-08
I am using ubuntu server to setup and use my server, I added an extra network card in the system because the network socket on the motherboard only supports 100mbit.

The pci card I added is the D-Link DQE-528T. But I cannot get the card up in running.

This is some commands I tried to diagnose the problem: (I am not an Ubuntu expert, I am kinda new to Ubuntu server, so I don't understand everything in here so I can't find the problem).

> sudo lshw -C network
```

  *-network
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: NVIDIA Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 90:fb:a6:2f:c9:90
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.193 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:29 memory:efffd000-efffdfff ioport:f600(size=8) memory:efffc000-efffc0ff memory:efffb000-efffb00f

```

Btw the eth0 is my onboard network adapter.
> ifconfig
```

 eth0      Link encap:Ethernet  HWaddr 90:fb:a6:2f:c9:90
          inet addr:192.168.0.193  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::92fb:a6ff:fe2f:c990/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26604 (26.6 KB)  TX bytes:95106 (95.1 KB)
 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2712 (2.7 KB)  TX bytes:2712 (2.7 KB)

```

> dmesg | grep eth0
```

[    2.246672] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 90:fb:a6:2f:c9:90
[    9.021486] init: network-interface (eth0) pre-start process (493) terminated with status 1
[    9.143300] init: network-interface (eth0) post-stop process (518) terminated with status 1
[ 2075.662801] forcedeth 0000:00:0f.0 eth0: MSI enabled

```

> ps aux | grep -i network

```

kevin     1262  0.0  0.0  10468  2228 pts/0    S+   22:40   0:00 grep --color=auto -i network

```

Does anybody have an idea how to get the card working?

---

### Post by slickymaster on 2016-04-08
*Moved to the ***Networking & Wireless*** sub-forum*

---

