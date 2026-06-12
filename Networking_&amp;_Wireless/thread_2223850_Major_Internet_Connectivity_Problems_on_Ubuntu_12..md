---
title: "Major Internet Connectivity Problems on Ubuntu 12.04 LTS"
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by sudo3 on 2014-05-13
I have a HP Pavillion dv6000 notebook with Windows 7 as OS. I had installed Ubuntu 12.04 LTS, making it dual boot. Initially I could not connect to a DSL connection but after trying to connect through pppoeconf and tweaking the Network Manager configuration file, my problem was solved. But one fine day, out of nowhere Ubuntu started getting stuck at boot time. So after trying to fix this issue, I just decided to wipe the installation and reinstall. But even after trying all the fixes I had used earlier, I just can't seem to connect to the internet again. 

I have googled this and have been trying various fixes for the last four days but I am still stuck. 

I can successfully connect to the internet on Windows though. 

I apologize for posting the detailed history, but I am desperate for advice!

Any help would be greatly appreciated!

---

### Post by Iowan on 2014-05-13
A few more details may be in order...
Please post results of: ```
ifconfig -a
```
Depending on results, the following might be helpful:```
sudo lshw -C network
```

---

### Post by sudo3 on 2014-05-14
There you go.. 

```
if config -a
```

eth0      Link encap:Ethernet  HWaddr 00:1b:24:d5:8a:fb  
          inet6 addr: fe80::21b:24ff:fed5:8afb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20585 (20.5 KB)  TX bytes:275301 (275.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1952 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1952 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:150201 (150.2 KB)  TX bytes:150201 (150.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:33:2b:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5647 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11352210 (11.3 MB)  TX bytes:586173 (586.1 KB)


```
sudo lshw -C network
```

 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:33:2b:fa
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.11.0-20-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f4000000-f4000fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:d5:8a:fb
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:c000(size=256) memory:f8200000-f8200fff memory:c4000000-c401ffff

---

