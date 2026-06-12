---
title: "Connected to wifi but no internet"
date: 2015-06-04
forum: Networking &amp; Wireless
---

### Post by nt.2 on 2015-06-04
I have a laptop with dualboot win7 and elementary os (both 64x). If im on eos it can connect to local wifi but it cant reach the internet i can't even access the router administration, if im using win7 everything works fine.

im a linuxnewbie but i guess these logs could be useful:
```
fs@fs-ThinkPad-E520:~$ uname -a
Linux fs-ThinkPad-E520 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 
```

```
fs@fs-ThinkPad-E520:~$ lspci -nnk00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
    Subsystem: Lenovo Device [17aa:21e2]
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
    Kernel driver in use: pcieport
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Lenovo Device [17aa:21e3]
    Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
    Kernel driver in use: pcieport
00:1c.7 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 [8086:1c1e] (rev b4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
    Subsystem: Lenovo Device [17aa:21e2]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M] [1002:6741] (rev ff)
    Kernel driver in use: radeon
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: r8169
04:00.0 System peripheral [0880]: Ricoh Co Ltd PCIe SDXC/MMC Host Controller [1180:e823] (rev 07)
    Subsystem: Lenovo Device [17aa:21e2]
    Kernel driver in use: sdhci-pci
09:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlwifi
```

```


fs@fs-ThinkPad-E520:~$ iwconfig
eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Internet12569"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:02:CF:AB:EC:88   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:57   Missed beacon:0


lo        no wireless extensions.



```

```
fs@fs-ThinkPad-E520:~$ lsmod | grep ^rtl- returns nothing

```

```
fs@fs-ThinkPad-E520:~$ ifconfigeth0      Link encap:Ethernet  HWaddr f0:de:f1:83:41:82  
          inet6 addr: fe80::f2de:f1ff:fe83:4182/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:780 errors:0 dropped:0 overruns:0 frame:0
          TX packets:441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74061 (74.0 KB)  TX bytes:45131 (45.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:181145 (181.1 KB)  TX bytes:181145 (181.1 KB)


wlan0     Link encap:Ethernet  HWaddr 74:e5:0b:19:b9:22  
          inet addr:10.42.1.1  Bcast:10.42.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76e5:bff:fe19:b922/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4533 (4.5 KB)  TX bytes:50580 (50.5 KB)
```

```
fs@fs-ThinkPad-E520:~$ route -nKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.1.0       0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

i've read similar topics here but so far nothing helped me.

---

### Post by TheFu on 2015-06-04
The default gateway isn't set correctly. Fix that. I don't use a GUI, so cannot help, sorry. If the system is using DHCP, then the DHCP server isn't working correctly. If it has a static IP, the GATEWAY setting is missing.  

If you are using /etc/network/interfaces to manage it, I can definitely help. Don't touch that file if you want to use a GUI, however.

---

### Post by oldos2er on 2015-06-04
Moved to Networking & Wireless.

---

