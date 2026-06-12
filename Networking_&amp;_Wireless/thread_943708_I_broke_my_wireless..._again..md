---
title: "I broke my wireless... again."
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by EcthelionGenesis on 2008-10-10
Evening all. Was mucking around with ifconfig... I was curious! Anyway, I ended up changing the MAC address on my Wireless card. Now I can't connect to anything. Surprise surprise.

Help, please! Even *you* must have done this kind of thing at least once!

Outputs:

```
ecthelion@Ubu-XPSM1330:~$ **ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:1d:09:4d:af:d5  
          inet addr:19.6.199.3  Bcast:19.6.199.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe4d:afd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3534701 (3.3 MB)  TX bytes:773470 (755.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2834 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141700 (138.3 KB)  TX bytes:141700 (138.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:99:0f:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-99-0F-13-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ecthelion@Ubu-XPSM1330:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ecthelion@Ubu-XPSM1330:~$ **sudo lshw -C network**
[sudo] password for ecthelion: 
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:99:0f:13
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:4d:af:d5
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=19.6.199.3 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
```

Anything else you might need, just ask.
Tried changing it back, but I can't remember what it was originally.

Thanks in advance!

---

