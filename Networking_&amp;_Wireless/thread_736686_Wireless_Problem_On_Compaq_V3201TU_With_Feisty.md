---
title: "Wireless Problem On Compaq V3201TU With Feisty"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by Suhendri on 2008-03-26
I have follow the tutorial to setup my wireless connection, and the network connection written my wireless connected to access point..

If the connection said that i connected to the network, i can't browse the network. even i tried to ping the gateway it said unreachable..

I'm using the static ip, and the access point has a security key. When i setup the network security key using hex mode, my notebook hang. But if i'm using the ascii mode is fine.

I've tried to connected to free hotspot, and after that my notebook hung..:confused:

I don't know what i have to do to solve my problem...

here are the result of
**sudo lshw -C network**
```

 *-network
      description: Wireless interface
      product: PRO/Wireless 3945ABG Network Connection
      vendor: Intel Corporation
      physical id: 0
      bus info: pci@05:00.0
      logical name: eth1
      version: 02
      serial: 00:19:d2:24:7d:50
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=ipw3945
driverversion=1.2.0mp firmware=13.0 1:0 () ip=192.168.2.232 latency=0
link=yes multicast=yes wireless=IEEE 802.11g
      resources: iomemory:d4000000-d4000fff irq:18
 *-network
      description: Ethernet interface
      product: PRO/100 VE Network Connection
      vendor: Intel Corporation
      physical id: 8
      bus info: pci@08:08.0
      logical name: eth0
      version: 02
      serial: 00:16:d3:1c:d3:0c
      size: 10MB/s
      capacity: 100MB/s
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master cap_list ethernet physical tp mii 10bt
10bt-fd 100bt 100bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=e100
driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=66
link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
      resources: iomemory:d4100000-d4100fff ioport:3000-303f irq:22

```

**lsmod | grep ipw**
```

ipw3945               118816  1
ieee80211              51052  1 ipw3945

```

**dmesg | grep 3945**
```

[   20.652000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection
driver for Linux, 1.2.0mp
[   20.652000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   20.656000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network
Connection
[   22.576000] ipw3945: Detected geography ABG (11 802.11bg channels,
13 802.11a channels)

```

** iwconfig**
```

eth1      IEEE 802.11g  ESSID:"XXXXXXXXXXXXXX"
         Mode:Managed  Frequency:2.462 GHz  Access Point:
00:12:17:74:E7:A4
         Bit Rate:24 Mb/s   Tx-Power:14 dBm
         Retry limit:15   RTS thr:off   Fragment thr:off
         Power Management:off
         Link Quality=76/100  Signal level=-61 dBm  Noise level=-62
dBm
         Rx invalid nwid:0  Rx invalid crypt:6341  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:15   Missed beacon:0

```

---

