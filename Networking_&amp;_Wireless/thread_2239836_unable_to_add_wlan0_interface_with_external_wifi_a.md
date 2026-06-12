---
title: "unable to add wlan0 interface with external wifi adapter"
date: 2014-08-16
forum: Networking &amp; Wireless
---

### Post by anand_roshan on 2014-08-16
Hello everyone. This is my first thread on ubuntu forums.
I have a lenova laptop without internet wifi card. I was using a external wifi adapter which was working fine without any drivers. But a few days back I purchased a new wifi adapter but It is not working. I tried to install drivers given in the CD but it throws error while compiling. I'm not able to see wlan0 in anywhere. Please help me out of this situation.

result for *ifconfig*
```
eth0      Link encap:Ethernet  HWaddr f0:de:f1:c4:23:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:710480 (710.4 KB)  TX bytes:710480 (710.4 KB)

usb0      Link encap:Ethernet  HWaddr 32:c4:a9:eb:5a:67  
          inet addr:192.168.42.82  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::30c4:a9ff:feeb:5a67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2198 errors:2 dropped:0 overruns:0 frame:2
          TX packets:2184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1451245 (1.4 MB)  TX bytes:476317 (476.3 KB)


```

result for *iwconfig*
```
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.


```

result for *lsusb*
```
Bus 002 Device 033: ID 0bb4:0003 HTC (High Tech Computer Corp.) 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:7601 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

result for *lspci*
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```

Please ask me any info if needed.
Thanks in advance.

---

### Post by praseodym on 2014-08-16
Hi,

have you tried this:

[http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation)

---

