---
title: "After Upgrade to 18.04 - BAD DNS CONFIG CHECK DNS SETTINGS, No Internet Connection"
date: 2019-01-28
forum: Networking &amp; Wireless
---

### Post by Rick St. George on 2019-01-28
Found this Link somewhat useful, and the Links embedded therein;
[https://ubuntuforums.org/showthread.php?t=2409858](https://ubuntuforums.org/showthread.php?t=2409858)

But does not address my issue. I get the following Error in web broswer, and NO internet connection but have an IP address! 
Error: 
DNS_PROBE_FINISHED_BAD_CONFIG
Check your DNS settings

-----------------------

> 
lshw
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
Vender: RealTek Semiconductor
logical name: eth0


Upgraded today (28 Jan 2019) to v18.04 and Kernel is 4.15.0-44-lowlatency

I looked here;
[https://medium.com/@lgobinath/no-ethernet-connection-in-ubuntu-16-04-linux-mint-18-with-realtek-rtl8111-8168-8411-7ae2779dc9b8](https://medium.com/@lgobinath/no-ethernet-connection-in-ubuntu-16-04-linux-mint-18-with-realtek-rtl8111-8168-8411-7ae2779dc9b8)
And here;
[https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/](https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/)
and here;
[https://unix.stackexchange.com/questions/280264/no-dns-resolution-after-upgrade-from-ubuntu-14-04-to-16-04](https://unix.stackexchange.com/questions/280264/no-dns-resolution-after-upgrade-from-ubuntu-14-04-to-16-04)

Any Help would be appreciated ... Thanks!

---

### Post by Rick St. George on 2019-01-29
I've looked across the  net for answers to this problem. It seems due to some new "network config" by Ubuntu, it no longer works for anyone using RealTek interfaces. Here is some printouts on my system. 
```

$ uname -a
Linux stephen-evo-5723 4.15.0-44-lowlatency #47-Ubuntu SMP PREEMPT Mon Jan 14 12:16:46 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 44:8a:5b:97:f6:c1 brd ff:ff:ff:ff:ff:ff
    inet 192.168.20.53/24 brd 192.168.20.255 scope global dynamic noprefixroute eth0
       valid_lft 86060sec preferred_lft 86060sec
    inet6 fe80::468a:5bff:fe97:f6c1/64 scope link 
       valid_lft forever preferred_lft forever



$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.20.1    0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.20.0    0.0.0.0         255.255.255.0   U     100    0        0 eth0



$ sudo lshw -c network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 44:8a:5b:97:f6:c1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.20.53 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:38 ioport:e000(size=256) memory:fe204000-fe204fff memory:fe200000-fe203fff


$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RD9x0/RX980 Host Bridge [1002:5a14] (rev 02)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RD9x0/RX980 Host Bridge [1462:7640]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD/ATI] RD890S/RD990 I/O Memory Management Unit (IOMMU) [1002:5a23]
    Subsystem: Micro-Star International Co., Ltd. [MSI] RD890S/RD990 I/O Memory Management Unit (IOMMU) [1462:7640]
00:05.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 1) [1002:5a19]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:07.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 3) [1002:5a1b]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0b.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD990 PCI to PCI bridge (PCI Express GFX2 port 0) [1002:5a1f]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390] (rev 40)
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1462:7640]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1462:7640]
    Kernel driver in use: ohci-pci
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1462:7640]
    Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1462:7640]
    Kernel driver in use: ohci-pci
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1462:7640]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
    Subsystem: Micro-Star International Co., Ltd. [MSI] SBx00 SMBus Controller [1462:7640]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 IDE Controller [1462:7640]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp, pata_acpi
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Micro-Star International Co., Ltd. [MSI] SBx00 Azalia (Intel HDA) [1462:f640]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 LPC host controller [1462:7640]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1462:7640]
    Kernel driver in use: ohci-pci
00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1462:7640]
    Kernel driver in use: ohci-pci
00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: Micro-Star International Co., Ltd. [MSI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1462:7640]
    Kernel driver in use: ehci-pci
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0 [1022:1600]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1 [1022:1601]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2 [1022:1602]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3 [1022:1603]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4 [1022:1604]
    Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5 [1022:1605]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7640]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
    Subsystem: Micro-Star International Co., Ltd. [MSI] uPD720200 USB 3.0 Host Controller [1462:7640]
    Kernel driver in use: xhci_hcd
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119 [GeForce GT 610] [10de:104a] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GF119 [GeForce GT 610] [1043:8496]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
03:00.1 Audio device [0403]: NVIDIA Corporation GF119 HDMI Audio Controller [10de:0e08] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GF119 HDMI Audio Controller [1043:8496]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


$ sudo ethtool -i eth0
driver: r8169
version: 2.3LK-NAPI
firmware-version: rtl8168e-3_0.0.4 03/27/12
expansion-rom-version: 
bus-info: 0000:01:00.0
supports-statistics: yes
supports-test: no
supports-eeprom-access: no
supports-register-dump: yes
supports-priv-flags: no

```

I believe the appropriate file located on this page;
[https://www.realtek.com/zh-tw/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software](https://www.realtek.com/zh-tw/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software)

According to this page;
[https://www.linuxquestions.org/questions/linux-hardware-18/realtek-rtl8111-8168-8411-ethernet-controller-r8168-driver-install-r8169-driver-doesn%27t-work-4175641982/](https://www.linuxquestions.org/questions/linux-hardware-18/realtek-rtl8111-8168-8411-ethernet-controller-r8168-driver-install-r8169-driver-doesn%27t-work-4175641982/)

But the link expires quickly, and Opera doesn't connect at all from my laptop (different machine). Seems it only sends the download to an email ONCE. Will try again tomorrow and post results. 
As a side note, I noticed an update on my laptop for Network under a strange heading (don't remember what ... but it wasn't Network). 

Trying to follow advice from this informative "how to" post;
[https://www.unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://www.unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/)

Any help would be appreciated ... Thanks!

---

### Post by Rick St. George on 2019-01-30
Found Driver r8168 here;
[https://launchpad.net/ubuntu/bionic/amd64/r8168-dkms/8.045.08-2](https://launchpad.net/ubuntu/bionic/amd64/r8168-dkms/8.045.08-2)

After using DEB Pkg installer, still no working Net Access, but does show IP address ?!?!?   Says Driver is currently installed !!!
Still stumped ... Now Wireless USB adapter does not obtain IP address (previously it showed an IP address but would not connect either).
Upon Reboot get "Systemd Journald: failed to write entry, Ignoring Read Only File System."

Any suggestions? Could I rebuild Network Manager with a 18.04 CD downloaded on another computer?

---

### Post by Rick St. George on 2019-01-31
Since after several days, no one seems interested in helping ... I decided to Restore back to 16.04. FYI - used [https://malwaretips.com/threads/acronis-true-image-2017-bootcd.77984/](https://malwaretips.com/threads/acronis-true-image-2017-bootcd.77984/)
Just not worth the hassle and headache to try and figure out what Canoniacal did, or did not do, to the Network Manager, Resolve Conf and DNS routines, etc.
Don't know where RealTek is based out of ... maybe its political why we can't seem to get the correct drivers, or why the correct drivers don't work. Bottom line is, it broke the OS since it can't go online.

Case is not closed ... so if somone has a final answer - please post for the benefit of anyone else who ventures on to this Thread.

---

