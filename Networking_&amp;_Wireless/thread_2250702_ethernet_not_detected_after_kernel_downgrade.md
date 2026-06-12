---
title: "ethernet not detected after kernel downgrade"
date: 2014-10-30
forum: Networking &amp; Wireless
---

### Post by nan3 on 2014-10-30
Hello,

I installed Ubuntu 12.04.2 LTS on a SBC and everything was working fine, however the kernel was 3.5.0-23-generic and I need 3.2.0-45-generic for some hardware that I am adding to the board. I did the installation through synaptic package manager and booted up the using the older kernel but the two Ethernet adapters are no longer being detected. What would be the best way to fix this issue and sticking to the 3.2.0-45 kernel? Thanks!

ifconfig -a:
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14880 (14.8 KB)  TX bytes:14880 (14.8 KB)

```

lshw -c NET:
```

  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:90500000-9057ffff ioport:2000(size=32) memory:90580000-90583fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:90400000-9047ffff ioport:1000(size=32) memory:90480000-90483fff

```

lspci:
```

00:00.0 Host bridge: Intel Corporation Device 0f00 (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Device 0f31 (rev 0c)
00:10.0 SD Host controller: Intel Corporation Device 0f14 (rev 0c)
00:11.0 SD Host controller: Intel Corporation Device 0f15 (rev 0c)
00:12.0 SD Host controller: Intel Corporation Device 0f16 (rev 0c)
00:13.0 SATA controller: Intel Corporation Device 0f23 (rev 0c)
00:1a.0 Encryption controller: Intel Corporation Device 0f18 (rev 0c)
00:1b.0 Audio device: Intel Corporation Device 0f04 (rev 0c)
00:1c.0 PCI bridge: Intel Corporation Device 0f48 (rev 0c)
00:1c.1 PCI bridge: Intel Corporation Device 0f4a (rev 0c)
00:1c.2 PCI bridge: Intel Corporation Device 0f4c (rev 0c)
00:1c.3 PCI bridge: Intel Corporation Device 0f4e (rev 0c)
00:1d.0 USB controller: Intel Corporation Device 0f34 (rev 0c)
00:1f.0 ISA bridge: Intel Corporation Device 0f1c (rev 0c)
00:1f.3 SMBus: Intel Corporation Device 0f12 (rev 0c)
03:00.0 Ethernet controller: Intel Corporation Device 1533 (rev 03)
04:00.0 Ethernet controller: Intel Corporation Device 1533 (rev 03)

```

---

