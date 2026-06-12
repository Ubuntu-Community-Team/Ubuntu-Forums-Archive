---
title: "Gateway T6321, can't figure out what wifi card it has"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by Queue29 on 2008-09-22
So after having guessed wrongly on a bunch of possible drivers, I was hoping someone could tell me what a Gateway T6321 has for a wireless card. Even better, if you could help me getting it to work. 

All I know is this: 


seth@SLinux:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)


.. and I'm not sure what that means.

---

### Post by prshah on 2008-09-22
> **Queue29 said:**
> 
 I was hoping someone could tell me what a Gateway T6321 has for a wireless card.

As per the model number, you have a Realtek 8187b wireless card. It's not visible in the lspci, though, can't figure why.

Let's try the following commands to see if we can tease it out:```

lspci -vvv | grep -i -A 7 -B 1 -E wireless\|realtek\|network
sudo lshw -C network
iwconfig

```

The third command is on the off-chance that it is actually detected and working!

Post back the outputs for further troubleshooting.

---

### Post by Queue29 on 2008-09-22
First command: 

lspci -vvv | grep -i -A 7 -B 1 -E wireless\|realtek\|network

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Gateway 2000 Unknown device 0560
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 221
	Region 0: I/O ports at 2000 [size=256]
	Region 2: Memory at f0000000 (64-bit, non-prefetchable) [size=4K]




Second: 

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:4b:89:4d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.147 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s


Third: 

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.




 I don't see it :confused:

---

### Post by prshah on 2008-09-22
> **Queue29 said:**
> 
 I don't see it :confused:

Neither do I... are you sure it's present / working? Try a Windows Live CD (BartPE) or some other distro. I have my doubts as to whether the device actually is working.

Could there be some BIOS setting disabling it? (Clutching at straws).

---

### Post by Queue29 on 2008-09-22
Ahh, after searching that card, I found: [http://ubuntuforums.org/showthread.php?t=571046&highlight=Realtek+8187B&page=2](http://ubuntuforums.org/showthread.php?t=571046&highlight=Realtek+8187B&page=2)

Which seems to be exactly what I need

---

