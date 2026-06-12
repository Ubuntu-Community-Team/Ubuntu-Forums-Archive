---
title: "Ubuntu 16.04 / Eth0, Eth1 not found in ifconfig / no network connection"
date: 2018-01-12
forum: Networking &amp; Wireless
---

### Post by Biscarri on 2018-01-12
Hi,

My PC Ubuntu 16.04 has lost ethernet connection.

The listing of **ifconfig** is:

```
lo    Link encap:Local Loopback
      inet addr:127.0.0.1    Mask:255.0.0.0
      UP LOOPBACK RUNNING  MTU:65536   Metric:1
      RX packets:8890 errors:0 dropped:0 overruns:0 frame:0
      TX packets:8890 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1
      RX bytes:659644 (659.6 KB)   TX bytes:659644 (659.6 KB)
```

I could solve this recurrent problem in the past with the commands that follow, but now they don't fix it.

```
[INDENT][FONT=arial][SIZE=2][COLOR=#000000]echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf[/COLOR][/SIZE][/FONT][/INDENT]
[INDENT][FONT=arial][SIZE=2][COLOR=#000000]sudo /etc/init.d/networking restart[/COLOR][/SIZE][/FONT][/INDENT]

```
or...

[SIZE=1][COLOR=#000000][FONT=Consolas]```
[SIZE=2][FONT=arial]sudo dpkg-reconfigure network-manager[/FONT][/SIZE]
```[/FONT][/COLOR][/SIZE]

and after that rebooting the PC.

Any help will be welcome!
Lluis

---

### Post by Biscarri on 2018-01-12
Additional information:

The listing of **lspci **...

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Juniper XT [Radeon HD 5770]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Juniper HDMI Audio [Radeon HD 5700 Series]

```

The ethernet controller doesn't appear either.

---

