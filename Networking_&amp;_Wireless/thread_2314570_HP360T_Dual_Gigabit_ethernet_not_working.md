---
title: "HP360T Dual Gigabit ethernet not working"
date: 2016-02-22
forum: Networking &amp; Wireless
---

### Post by thomas_h2 on 2016-02-22
Hello! Now I hate going onto forms and just asking for help, however I have had no choice this time and I would like to say sorry for that!

I'm on Ubuntu 14.04LTS

So my problem. I have looked and looked and found things about modprobe e1000e this rm e1000e that. Download the driver from Intel as its not downloadable from HP this has been a real nightmare! as it is only available for redhat and SUSE

My big issue is that the onboard realtek is showing but the HP360 is not showing at all! I have tried everything in my power however it refuses to function.

I know there isn't a lot of to go by but I would really appreciate some help. I'm not fantastic at using linux in general so baby step instructions if you can.

Thank you,

```
root@router-MS-7865:/home/router/Downloads/e1000e-3.1.0.2/src# lsmod | grep "e1000"
e1000                 131072  0[CODE]

[CODE]router@router-MS-7865:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr d8:cb:8a:5c:b4:d0  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::dacb:8aff:fe5c:b4d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25654 errors:0 dropped:1 overruns:0 frame:0
          TX packets:21487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23475965 (23.4 MB)  TX bytes:2732837 (2.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3584 (3.5 KB)  TX bytes:3584 (3.5 KB)

```

```
router@router-MS-7865:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8240 / R3 Series]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
```

---

### Post by praseodym on 2016-02-22
Is it a real BIOS (not an UEFI!)? If yes, try resetting it to default. Maybe the hardware is not on the BIOS whitelist, here a BIOS upgrade could help

---

