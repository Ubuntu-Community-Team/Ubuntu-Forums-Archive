---
title: "Realtek driver install fails."
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by ag93ds on 2008-08-06
I'm trying to install the driver for my Biostar TA780G M2+'s onboard ethernet card - Realtek RLT8111C. [ftp://66.104.77.130/cn/nic/r8168-8.008.00.tar.bz2](ftp://66.104.77.130/cn/nic/r8168-8.008.00.tar.bz2)

Here's what I've done:

matt@matt-desktop:~$ cd /home/matt/Desktop/r8168-8.008.00

matt@matt-desktop:~/Desktop/r8168-8.008.00$ ./configure
bash: ./configure: No such file or directory

matt@matt-desktop:~/Desktop/r8168-8.008.00$ sudo make install
make -C src/ install
make[1]: Entering directory `/home/matt/Desktop/r8168-8.008.00/src'
install -m 744 -c r8168.ko /lib/modules/2.6.24-16-generic/kernel/drivers/net/
install: cannot stat `r8168.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/matt/Desktop/r8168-8.008.00/src'
make: *** [install] Error 2
matt@matt-desktop:~/Desktop/r8168-8.008.00$ 
matt@matt-desktop:~/Desktop/r8168-8.008.00$ 

What am I doing wrong here?

---

### Post by pytheas22 on 2008-08-06
You probably don't need to install the driver at all--it's probably already in the kernel; there's just some bug preventing it from loading properly.  Please post the output of these commands so that we can better figure out what's going on:
```

ifconfig
lshw -C Network
lspci -nn
```

It's extremely rare that you would need to compile an ethernet driver, especially for a realtek card.  And anyway the drivers that you find for these things online, which claim to support Linux, are usually a mess and won't really compile unless you sit down with the source code for a long time cleaning it up.

---

### Post by ag93ds on 2008-08-07
matt@matt-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:89:7b:54  
          inet6 addr: fe80::2e0:4dff:fe89:7b54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:1067602164 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1380 (1.3 KB)  TX bytes:7047 (6.8 KB)
          Interrupt:222 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76492 (74.6 KB)  TX bytes:76492 (74.6 KB)

matt@matt-desktop:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4d:89:7b:54
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

matt@matt-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3200 Graphics [1002:9610]
01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
matt@matt-desktop:~$

---

### Post by pytheas22 on 2008-08-08
Your ethernet card already looks like it's up and running fine, according to the output you posted--you don't need to install any drivers for it.  Are you having trouble connecting?  If so please describe the problem and maybe we can figure it out.  You could also try this command to get an IP address from the command-line:
```

sudo dhclient eth0
```

---

### Post by ag93ds on 2008-08-08
Well I booted it up today and the internet works fine. Not sure why, but if it works, it works. Thanks for all your help.

---

