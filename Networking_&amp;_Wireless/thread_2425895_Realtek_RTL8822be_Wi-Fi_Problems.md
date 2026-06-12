---
title: "Realtek RTL8822be Wi-Fi Problems"
date: 2019-09-01
forum: Networking &amp; Wireless
---

### Post by squeegene on 2019-09-01
Hi guys,

I've been through I think almost all the threads trying to get this RTL8822be card working on my Asus X510QA. Secure Boot is disabled, and the funny thing is that the card was working with the Live USB version but now doesn't work when Ubuntu 19.04 is installed. The card appears, but it is unable to find any networks. 

Some other posts have recommended that I:

[LIST]
[*]Disable Secure Boot [done] 
[*]Blacklist r882be [tried, didn't work] 
[*]Install drivers from synthtc/rtlwifi-next [failed with errors] 
[/LIST]

I was pretty sure some posts had mentioned that this card was supposed to work out of the box in 18.04 ([https://askubuntu.com/questions/994150/ubuntu-16-04-on-hp-envy-ae000-wifi-problems](https://askubuntu.com/questions/994150/ubuntu-16-04-on-hp-envy-ae000-wifi-problems)), but I tried both 18.04 and 19.04 and the card doesn't work with either.

So now I'm lost and was wondering if I could get any help!

Here's some relevant info:

```
lshw -C network
```

```
  *-network                 
       description: Wireless interface
       product: RTL8822BE 802.11a/b/g/n/ac WiFi adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 00
       serial: dc:f5:05:da:a0:25
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_pci driverversion=5.0.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:25 ioport:e000(size=256) memory:fea00000-fea0ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:4
       logical name: wlxc46e1f2551ce
       serial: c4:6e:1f:25:51:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=5.0.0-25-generic firmware=N/A ip=192.168.1.14 link=yes multicast=yes wireless=IEEE 802.11
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

```
lspci
```

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) I/O Memory Management Unit
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wani [Radeon R5/R6/R7 Graphics] (rev c8)
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1578
00:09.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 157d
00:09.2 Audio device: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Audio Controller
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 20)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 49)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 49)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 4a)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 5
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter

```

Anything else I can do here?

---

### Post by bilbatez on 2019-09-01
You can try to follow this [thread]("https://ubuntuforums.org/showthread.php?t=370108") and provide the full diagnostic. There's a log for the kernel module using the dmesg command maybe it will show something

---

### Post by squeegene on 2019-09-01
Thanks for the suggestion! Here's the output of wireless-info. One thing to note is I have a USB TP-Link Wifi adapter plugged in at the moment as an alternative - I believe that's the RTL8192 chip

[https://paste.ubuntu.com/p/7J6Gxf67wd/](https://paste.ubuntu.com/p/7J6Gxf67wd/)

---

