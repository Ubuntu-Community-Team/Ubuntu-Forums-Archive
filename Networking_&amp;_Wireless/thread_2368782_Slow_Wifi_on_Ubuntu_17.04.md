---
title: "Slow Wifi on Ubuntu 17.04"
date: 2017-08-15
forum: Networking &amp; Wireless
---

### Post by venumwolf on 2017-08-15
Hello, all!
So, a little background.  I've recently switched over to Ubuntu from Windows 10, ever since my first boot, the wifi has been unusually slow.  I just passed it off as bad or poorly supported drivers and wired in, and everything works fine there.  After further testing the wired connection, I did notice a bit of a drop in performance, but it's still blazingly fast(around 60mb/s as opposed to around 75mb/s on windows), I'm not really bothered by it.  As for the wifi, at first it worked okay, though much, much slower than it should have.  (Only averaging 200kb/s - 300kb/s, as opposed to an average of 45mb/s - 50mb/s on windows.)  After a while, the card would quit and disconnect me constantly, then struggle to work at all.  I found this to be a problem with the default network manager, I have removed it and installed Wicd, and that solved the disconnecting problems, the high ping, and slowness when browsing.  When performing a speed test after installing Wicd, I find that the card averages about 2mb/s with occasional spikes up to 15mb/s or even 20mb/s.  In all practical browsing and downloading from Google Drive, my download speed is quite inconsistent with the speed test results, only around 500kb/s average.
So far, I've ruled out throttling as Google Drive doesn't throttle to <1mb/s (at least in my knowledge/experience), it's not my router or the ISP as all other devices are working as normal. I'm sure I just need drivers for the card, however I'm unsure where to get them. Admittedly, I'm new to Ubuntu and I'm not sure of all the ins and outs of the system, so I could be missing something. Can anyone please help me?  Here is my network adapter info:

```

  *-network                 
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlo1
       version: 01
       serial: ac:d1:b8:3f:0f:22
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=4.10.0-32-generic firmware=N/A ip=192.168.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:51 ioport:4000(size=256) memory:c3100000-c3103fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eno1
       version: 08
       serial: d0:bf:9c:90:b9:ad
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-2_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:48 ioport:3000(size=256) memory:c3004000-c3004fff memory:c3000000-c3003fff

```

Thanks so much!
-Venum

---

