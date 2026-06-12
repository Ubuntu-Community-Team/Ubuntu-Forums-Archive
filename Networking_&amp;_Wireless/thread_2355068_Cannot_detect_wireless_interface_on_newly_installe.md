---
title: "Cannot detect wireless interface on newly installed Ubuntu 14.04 LTS"
date: 2017-03-09
forum: Networking &amp; Wireless
---

### Post by daniellej on 2017-03-09
Hi,
I've newly installed Ubuntu 14.04 LTS on my Minnowboard Turbot board.
It has Intel Ultimate N 5300 wireless network card attached to it,
but the system cannot detect any wireless interface.

lspci command:
```

00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 11)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 11)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series USB xHCI (rev 11)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 11)
00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 11)
00:1c.0 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 1 (rev 11)
00:1c.2 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 3 (rev 11)
00:1c.3 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 4 (rev 11)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 11)
00:1f.3 SMBus: Intel Corporation Atom Processor E3800 Series SMBus Controller (rev 11)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)

```

iwconfig command:
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

ifconfig command:
```

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:255.255.255.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11653834 (11.6 MB)  TX bytes:1207351 (1.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:175173 (175.1 KB)  TX bytes:175173 (175.1 KB)

```

lshw -C network command:
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 0c
       serial: xx:xx:xx:xx:xx:xx
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=141.223.83.23 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:265 ioport:1000(size=256) memory:90500000-90500fff memory:90400000-90403fff

```

lsmod | grep iwlwifi command:
(I've entered the command modeprobe iwlwifi and modeporbe iwldvm)
```

iwlwifi               196608  1 iwldvm
cfg80211              561152  3 iwlwifi,mac80211,iwldvm

```



I've also tried to switch the wireless card with another working wireless card (that is well detected by another board)
to check if the problem is with the hardware, but this board still couldn't detect it,
so I assume that the problem is not with the hardware itself.

Can anyone help me how to make the system recognize the wireless interface?

---

### Post by jeremy31 on 2017-03-09
I would go into BIOS and reset to defaults and see if WLAN/wifi has a setting there to enable/disable.  I know if i disable wifi in BIOS on my Lenovo the card doesn't get detected

---

### Post by daniellej on 2017-03-16
I found what the problem was.
It was the hardware problem.
The attached expansion board (silverjaw lure) seems to be broken,
so the network card attached to it was not recognized by the board.

But thank you for your advises!!

---

