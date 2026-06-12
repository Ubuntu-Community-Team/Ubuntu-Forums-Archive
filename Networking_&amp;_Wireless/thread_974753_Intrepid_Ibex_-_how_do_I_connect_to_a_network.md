---
title: "Intrepid Ibex - how do I connect to a network?"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by Beniamin on 2008-11-07
I know they've made some changes in 8.10 with the way you connect to a network, and I still haven't figured it out.  I have Ubuntu Studio on a Dell laptop, and during installation it wasn't able to configure a network, so I told it that I would set up the network later.  However, I haven't been able to find "Network Manager," and I haven't had any luck at all figuring out how to connect, or whether I did something wrong.

**sudo iwconfig** yields the following:

```

lo     no wireless extensions.

eth0   no wireless extensions.

eth1   unassociated ESSID:off/any
       Mode:Managed Channel=0 Access Point: Not-Associated
       Bit Rate:0 kb/s  Tx-Power=20 dBm  Sensitivity=8/0
       Retry limit:7  RTS thr:off  Fragment thr:off
       Encryption key:off
       Link Quality:0  Signal level:0  Noise level:0
       Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
       Tx excessive retries:0  Invalid misc:0  Missed beacon:0

pan0   no wireless extensions.

```

...and **lshw -C network** yields:

```

WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:e4:de:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:e6:fa:32
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:9b:3d:27:c9:90
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Could anyone give me some pointers, or give me an idea of what is missing here?  I'm really liking Intrepid so far, but I would like to be able to connect to the internet :)

Thanks!

---

