---
title: "Problem with SMC WPCI-G"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by cenourinha on 2008-05-01
Hello,

Today i just updated Ubuntu 7 for Ubuntu 8.0.4 but i got a little problem, my wireless card isnt detected.

Im currently runing on Ubuntu Live CD 7.0.4 and the wireless card is detected

```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1E:8C:45:82:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:F7:3A:90:E4  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:f7ff:fe3a:90e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7158 errors:24 dropped:28 overruns:0 frame:0
          TX packets:6579 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6955701 (6.6 MB)  TX bytes:1033811 (1009.5 KB)
          Interrupt:17 Memory:f8a2ac00-f8a2ad00 

```


and

```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1e:8c:45:82:01
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 firmware=N/A latency=0 link=no module=atl1 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wlan0
       version: 20
       serial: 00:13:f7:3a:90:e4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.2.100 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g linked

```

This results are from live cd.

Can you help me...

---

### Post by Jeztastic on 2008-06-09
Hi, I also have the same problem - the networks card is not recognised.

Sorry, my bad it's there identified as an ethernet card.

---

