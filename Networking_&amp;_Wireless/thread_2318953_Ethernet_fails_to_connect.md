---
title: "Ethernet fails to connect"
date: 2016-03-30
forum: Networking &amp; Wireless
---

### Post by jean-pierre3 on 2016-03-30
I'm completely new to Linux and am running a newly installed version of ubuntu 5.10.  After running the software update however I could no longer connect to my router via the ethernet and only via Wi-Fi (when using the wired connection it would try to connect for a while and then simply say 'disconnected').  Help would very much be appreciated.

sudo lshw - C network
```

  *-network               
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 01
       serial: 28:c2:dd:27:ff:7f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.2.0-34-generic firmware=N/A ip=192.168.0.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:04:00.1
       logical name: enp4s0f1
       version: 12
       serial: 14:dd:a9:04:19:f4
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:33 ioport:d000(size=256) memory:f7814000-f7814fff memory:f7810000-f7813fff

```

lspci | grep Ethernet
```

04:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)

```

ifconfig
```

enp4s0f1  Link encap:Ethernet  HWaddr 14:dd:a9:04:19:f4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:94 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:54746 (54.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:193109 (193.1 KB)  TX bytes:193109 (193.1 KB)

wlp3s0    Link encap:Ethernet  HWaddr 28:c2:dd:27:ff:7f  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2ac2:ddff:fe27:ff7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14021 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12145742 (12.1 MB)  TX bytes:1507317 (1.5 MB)

```

---

### Post by $yl9pAR%t on 2016-03-30
In Network Manager, try disconnect wireless connection and next try to connect ethernet, I suspect they cannot work together at the same time.

---

### Post by jean-pierre3 on 2016-04-09
Thanks Mefisto but I fortunately found the solution to the problem.  After some digging around the web I found out that the issue is with the driver for the Realtek RTL8111/8168/8411 series of network interface cards.  The solution was simple - uninstall the driver shipped with Ubuntu and install the latest official release from their site here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false).  Hopefully others with the same NIC will happen upon this thread.  Thanks again for trying to help as it is much appreciated.

---

