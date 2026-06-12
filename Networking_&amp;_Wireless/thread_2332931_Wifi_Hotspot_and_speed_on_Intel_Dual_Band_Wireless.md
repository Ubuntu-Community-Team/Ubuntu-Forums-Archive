---
title: "Wifi Hotspot and speed on Intel Dual Band Wireless AC 8260"
date: 2016-08-05
forum: Networking &amp; Wireless
---

### Post by petwri on 2016-08-05
I am using ubuntu 16.04 and created a wifi hotspot using the network manager applet. It worked fine so far, however, it doesn't run on 802.11ac, just n-mode. But the adapter should support it. Any ideas where to start speeding my connection up? Can provide more infos if required. Thanks!

A little more information on the setup:

```

dmesg | grep iwlwifi
[    9.036493] iwlwifi 0000:05:00.0: Unsupported splx structure
[    9.038757] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-8000C-19.ucode failed with error -2
[    9.038908] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-8000C-18.ucode failed with error -2
[    9.038923] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-8000C-17.ucode failed with error -2
[    9.053871] iwlwifi 0000:05:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    9.088318] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[    9.088370] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled
[    9.088638] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled
[    9.471761] iwlwifi 0000:05:00.0 wlp5s0: renamed from wlan0
[   98.840716] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled
[   98.840961] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled
[   98.985108] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled
[   98.985354] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled
```

```

uname -a
Linux htpc 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

```

ifconfig
enp0s31f6 Link encap:Ethernet  HWaddr 40:8d:5c:51:32:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:df300000-df320000 


enp4s0    Link encap:Ethernet  HWaddr 40:8d:5c:51:32:3a  
          inet addr:192.168.178.21  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::6934:d878:1a43:6f6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:187023981 (187.0 MB)  TX bytes:6681730 (6.6 MB)
          Memory:df100000-df11ffff 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2615 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2615 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:476983 (476.9 KB)  TX bytes:476983 (476.9 KB)


wlp5s0    Link encap:Ethernet  HWaddr a4:34:d9:09:44:30  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a634:d9ff:fe09:4430/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6112 errors:0 dropped:4 overruns:0 frame:0
          TX packets:6994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1018573 (1.0 MB)  TX bytes:3389096 (3.3 MB)



```

```

lshw -C network
  *-network               
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 03
       serial: 40:8d:5c:51:32:3a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.3.0-k duplex=full firmware=0. 6-1 ip=192.168.178.21 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:df100000-df11ffff ioport:e000(size=32) memory:df120000-df123fff
  *-network
       description: Wireless interface
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlp5s0
       version: 3a
       serial: a4:34:d9:09:44:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-31-generic firmware=16.242414.0 ip=10.42.0.1 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:137 memory:df000000-df001fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (2) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 31
       serial: 40:8d:5c:51:32:38
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.8-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:135 memory:df300000-df31ffff

```

```

 lsmod | grep iwl
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm



```

---

