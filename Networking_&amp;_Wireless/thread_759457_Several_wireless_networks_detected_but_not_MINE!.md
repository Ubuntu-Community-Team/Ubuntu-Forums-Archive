---
title: "Several wireless networks detected but not MINE!"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by PatsyPoo on 2008-04-19
Hello all!
There's a very similar [thread ]("http://ubuntuforums.org/showthread.php?t=390980")describing the same problem I'm having but it doesn't seem to be too active anymore so I decided to start a new one.
I was having trouble with my WiFi card but yesterday I did a completely new install of Ubuntu 7.10 and followed a howto for the bcm4311. It's perfect now: my WiFi card does actually work.
However, several networks are detected apart from mine. I did check my router settings and it IS set to broadcast SSID (is there a difference between SSID and ESSID, btw?)
My router is a Huawei Echo Life and I've never had any problems with it while using Vista or XP.
I've only had Ubuntu for a few days so I still don't really know what I'm doing - any help would be much appreciated!
BTW, I don't know if it's relevant, but I've no problem using a wired network on Linux connected to the same router...

---

### Post by itix on 2008-04-19
Can you access your router from the browser??

---

### Post by PatsyPoo on 2008-04-19
If I'm on the wired network, yes! Is that good? - I hope so!

---

### Post by itix on 2008-04-19
no, but I mean (at least this is the procedure with my belkin G), if you just power the router up, you can still access the router.

Mine is at 192.168.2.1, but the most common is 192.168.0.1. Try entering that ip with your router powered up.

---

### Post by kevdog on 2008-04-19
Ok here is what I want you to post

lspci -nn
lshw -C network
iwlist scan
ifconfig

I know its a lot however it will tell the whole story.  Do you need to run wired and wireless at the same time?

---

### Post by PatsyPoo on 2008-04-19
Thanks kevdog!
I'll do that later on because right now it's a bit awkward - have to get the kids fed, bathed, etc...
What do you mean do I need wired and wireless at the same time? I only want wireless, if what you're asking is what my preference is...
For me to use the wired connection I have to set up my computer in my entrance hall, which is why I need the wireless to be up and running as soon as we can!
I'll post those results when I can set this baby up downstairs... Hopefully it won't take too long!

---

### Post by itix on 2008-04-19
You don't need wired and wireless at the same time. I just wanted to check that your computer could find the router. If you can access 192.168.0.1 or 192.168.1.1 or any similar address and get an interface like the one I attached it means that the computer can find the router, but I just realized that doing so won't help you because I can tell from here that you won't find it. I hope *kevdog* can help you.

It can be handy in the future though :p
You can manage all sorts of things from that interface.

---

### Post by PatsyPoo on 2008-04-19
Here are my results:

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1e:4c:8c:fd:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,03/23/2006, 4.40.1 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:b6:0c:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.1.2 latency=64 module=b44 multicast=yes

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:F6:99:7E:F7
                    ESSID:"BTHomeHub-BED1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1D:68:08:44:03
                    ESSID:"BTHomeHub-9F28"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:17:3F:DC:DA:FF
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:0D:88:87:4E:75
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:18:F6:76:BD:13
                    ESSID:"BTHomeHub-DFBB"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:09:B6:0C:59  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feb6:c59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:933 errors:0 dropped:0 overruns:0 frame:0
          TX packets:883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:936067 (914.1 KB)  TX bytes:139053 (135.7 KB)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:1E:4C:8C:FD:5B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:efdfc000-efe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


By the way, in case you need to know, my network SSID is TalkTalk95c9j.
Thanks for trying!

---

### Post by PatsyPoo on 2008-04-19
Hey itix!
Thanks anyway!
I can access the 192.168.1.1 for my modem. I'd been on that to try and see if anything screamed at me but... nothing!
I hope kevdog can get me out of this one too!...

---

### Post by kevdog on 2008-04-19
Hold on

The output of iwlist scan -- your essid doesn't even show up?  Is that correct?

---

### Post by PatsyPoo on 2008-04-19
That seems to be right. I've just gone over it again and couldn't find TalkTalk95c9j.
Is that really bad?

---

### Post by kevdog on 2008-04-19
If your router isn't listed, its going to be hard to connect to it.  Do you control your router?  What type is it?  Is it broadcasting on g mode only?  Does your card support g mode?

---

### Post by PatsyPoo on 2008-04-20
I don't know what g mode is. Is there a way of finding out?
The router is a Huawei EchoLife. I can access its settings through [http://192.168.1.1](http://192.168.1.1) but I don't think that's what you mean by "control it", is it?
Would it make any difference if I told you that I connect to the same router with the same card when I'm using windows vista? And I've never had a problem...

---

### Post by kevdog on 2008-04-20
Move as close as you can to the router and see what comes up with iwlist scan.

If nothing can you post dmesg.

Also where did you get your bcmwl5 driver?

---

### Post by PatsyPoo on 2008-04-20
The iwlist scan didn't show my router again - every time I'm online using Ubuntu I have to be very close to the router anyway because my wire is only about 3ft long.
If I got this driver you're talking about it was not voluntarily. The only thing I've done so far was to follow this [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").
Here's the output I got for dmesg:

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d3400 (usable)
[    0.000000]  BIOS-e820: 000000003f6d3400 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 259795) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259795
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259795
[    0.000000] On node 0 totalpages: 259795
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30182 pages, LIFO batch:7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
[    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 3F6D3D56, 0044 (r1 DELL    M07     27D7060D ASL        61)
[    0.000000] ACPI: FACP 3F6D4800, 0074 (r1 DELL    M07     27D7060D ASL        61)
[    0.000000] ACPI: DSDT 3F6D5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 3F6E3C00, 0040
[    0.000000] ACPI: HPET 3F6D4F00, 0038 (r1 DELL    M07            1 ASL        61)
[    0.000000] ACPI: APIC 3F6D5000, 0068 (r1 DELL    M07     27D7060D ASL        47)
[    0.000000] ACPI: MCFG 3F6D4FC0, 003E (r16 DELL    M07     27D7060D ASL        61)
[    0.000000] ACPI: SLIC 3F6D509C, 0176 (r1 DELL    M07     27D7060D ASL        61)
[    0.000000] ACPI: BOOT 3F6D4BC0, 0028 (r1 DELL    M07     27D7060D ASL        61)
[    0.000000] ACPI: SSDT 3F6D4276, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6D3D9A, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] Built 1 zonelists.  Total pages: 257766
[    0.000000] Kernel command line: root=UUID=36664382-e3ef-4f28-8712-a38e33a04a67 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.083 MHz processor.
[    4.449099] Console: colour VGA+ 80x25
[    4.449421] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    4.449739] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    4.473965] Memory: 1018556k/1039180k available (2015k kernel code, 19864k reserved, 915k data, 364k init, 121676k highmem)
[    4.473974] virtual kernel memory layout:
[    4.473975]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    4.473976]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    4.473978]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    4.473979]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    4.473980]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    4.473981]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[    4.473982]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[    4.473985] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    4.474023] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    4.474175] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    4.474180] hpet0: 3 64-bit timers, 14318180 Hz
[    4.555124] Calibrating delay using timer specific routine.. 3195.60 BogoMIPS (lpj=6391200)
[    4.555147] Security Framework v1.0.0 initialized
[    4.555156] SELinux:  Disabled at boot.
[    4.555169] Mount-cache hash table entries: 512
[    4.555315] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001
[    4.555323] monitor/mwait feature present.
[    4.555324] using mwait in idle threads.
[    4.555330] CPU: L1 I cache: 32K, L1 D cache: 32K
[    4.555332] CPU: L2 cache: 1024K
[    4.555335] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001
[    4.555346] Compat vDSO mapped to ffffe000.
[    4.555361] Checking 'hlt' instruction... OK.
[    4.571232] SMP alternatives: switching to UP code
[    4.571456] Freeing SMP alternatives: 11k freed
[    4.571731] Early unpacking initramfs... done
[    4.916845] ACPI: Core revision 20070126
[    4.916891] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    4.919513] CPU0: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz stepping 06
[    4.919540] Total of 1 processors activated (3195.60 BogoMIPS).
[    4.919735] ENABLING IO-APIC IRQs
[    4.919932] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    5.066673] Brought up 1 CPUs
[    5.066773] Booting paravirtualized kernel on bare hardware
[    5.066847] Time: 17:15:11  Date: 03/20/108
[    5.066866] NET: Registered protocol family 16
[    5.066940] EISA bus registered
[    5.066945] ACPI: bus type pci registered
[    5.095579] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
[    5.095581] PCI: Using configuration type 1
[    5.095583] Setting up standard PCI resources
[    5.101106] ACPI: EC: Look up EC in DSDT
[    5.105853] ACPI: Interpreter enabled
[    5.105858] ACPI: (supports S0 S3 S4 S5)
[    5.105873] ACPI: Using IOAPIC for interrupt routing
[    5.121084] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    5.121100] PCI: Probing PCI hardware (bus 00)
[    5.121866] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    5.121871] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    5.123038] PCI: Transparent bridge - 0000:00:1e.0
[    5.123104] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    5.123524] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    5.123654] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    5.123774] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    5.131900] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    5.132013] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
[    5.132122] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    5.132231] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    5.132340] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    5.132450] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    5.132561] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    5.132671] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    5.132782] Linux Plug and Play Support v0.97 (c) Adam Belay
[    5.132795] pnp: PnP ACPI init
[    5.132802] ACPI: bus type pnp registered
[    5.162716] pnp: PnP ACPI: found 12 devices
[    5.162719] ACPI: ACPI bus type pnp unregistered
[    5.162723] PnPBIOS: Disabled by ACPI PNP
[    5.162768] PCI: Using ACPI for IRQ routing
[    5.162771] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    5.213008] NET: Registered protocol family 8
[    5.213010] NET: Registered protocol family 20
[    5.213066] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
[    5.213069] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    5.213072] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    5.213075] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    5.213080] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    5.213083] pnp: 00:02: ioport range 0x1000-0x1005 has been reserved
[    5.213086] pnp: 00:02: ioport range 0x1008-0x100f has been reserved
[    5.213091] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    5.213094] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    5.213096] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[    5.213099] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    5.213102] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    5.213105] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    5.213111] pnp: 00:08: ioport range 0xc80-0xcff could not be reserved
[    5.213114] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[    5.213116] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[    5.213119] pnp: 00:08: ioport range 0xcb0-0xcbf has been reserved
[    5.213121] pnp: 00:08: ioport range 0x930-0x97f has been reserved
[    5.213128] pnp: 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    5.214500] Time: tsc clocksource has been installed.
[    5.214516] Switched to high resolution mode on CPU 0
[    5.243384] PCI: Bridge: 0000:00:1c.0
[    5.243386]   IO window: disabled.
[    5.243393]   MEM window: efd00000-efdfffff
[    5.243397]   PREFETCH window: disabled.
[    5.243403] PCI: Bridge: 0000:00:1c.3
[    5.243406]   IO window: d000-dfff
[    5.243413]   MEM window: efa00000-efcfffff
[    5.243418]   PREFETCH window: e0000000-e01fffff
[    5.243424] PCI: Bridge: 0000:00:1e.0
[    5.243426]   IO window: disabled.
[    5.243432]   MEM window: ef900000-ef9fffff
[    5.243436]   PREFETCH window: disabled.
[    5.243469] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    5.243477] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    5.243502] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[    5.243508] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    5.243523] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    5.243536] NET: Registered protocol family 2
[    5.282435] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    5.282508] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    5.283510] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    5.283907] TCP: Hash tables configured (established 131072 bind 65536)
[    5.283910] TCP reno registered
[    5.294550] checking if image is initramfs... it is
[    5.968102] Freeing initrd memory: 7059k freed
[    5.968232] Simple Boot Flag at 0x79 set to 0x1
[    5.968564] audit: initializing netlink socket (disabled)
[    5.968578] audit(1208711711.132:1): initialized
[    5.968649] highmem bounce pool size: 64 pages
[    5.970360] VFS: Disk quotas dquot_6.5.1
[    5.970407] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.970495] io scheduler noop registered
[    5.970497] io scheduler anticipatory registered
[    5.970499] io scheduler deadline registered
[    5.970514] io scheduler cfq registered (default)
[    5.970528] Boot video device is 0000:00:02.0
[    5.970695] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    5.970757] assign_interrupt_mode Found MSI capability
[    5.970760] Allocate Port Service[0000:00:1c.0:pcie00]
[    5.970789] Allocate Port Service[0000:00:1c.0:pcie02]
[    5.970889] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    5.970950] assign_interrupt_mode Found MSI capability
[    5.970952] Allocate Port Service[0000:00:1c.3:pcie00]
[    5.970981] Allocate Port Service[0000:00:1c.3:pcie02]
[    5.971137] isapnp: Scanning for PnP cards...
[    6.325141] isapnp: No Plug & Play device found
[    6.346416] Real Time Clock Driver v1.12ac
[    6.346565] hpet_resources: 0xfed00000 is busy
[    6.346607] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    6.347662] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    6.347841] input: Macintosh mouse button emulation as /class/input/input0
[    6.347917] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    6.351561] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.351567] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.351733] mice: PS/2 mouse device common for all mice
[    6.351837] EISA: Probing bus 0 at eisa.0
[    6.351901] EISA: Mainboard WG_FFFF detected.
[    6.351932] Cannot allocate resource for EISA slot 1
[    6.351962] EISA: Detected 0 cards.
[    6.352058] TCP cubic registered
[    6.352072] NET: Registered protocol family 1
[    6.352097] Using IPI No-Shortcut mode
[    6.352261]   Magic number: 4:14:290
[    6.352282]   hash matches device ttyz4
[    6.352354]   hash matches device tty23
[    6.352534] Freeing unused kernel memory: 364k freed
[    6.393445] input: AT Translated Set 2 keyboard as /class/input/input1
[    7.559362] AppArmor: AppArmor initialized<5>audit(1208711712.632:2):  type=1505 info="AppArmor initialized" pid=1241
[    7.565624] fuse init (API version 7.8)
[    7.570105] Failure registering capabilities with primary security module.
[    7.584202] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    7.584208] ACPI: Processor [CPU0] (supports 8 throttling states)
[    7.584221] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[    7.589118] ACPI: Thermal Zone [THM] (46 C)
[    8.100237] usbcore: registered new interface driver usbfs
[    8.100259] usbcore: registered new interface driver hub
[    8.100278] usbcore: registered new device driver usb
[    8.101021] USB Universal Host Controller Interface driver v3.0
[    8.101086] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[    8.101097] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    8.101102] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    8.101241] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    8.101275] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
[    8.101383] usb usb1: configuration #1 chosen from 1 choice
[    8.101406] hub 1-0:1.0: USB hub found
[    8.101412] hub 1-0:1.0: 2 ports detected
[    8.203832] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
[    8.203845] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    8.203849] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    8.203872] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    8.203906] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf60
[    8.204000] usb usb2: configuration #1 chosen from 1 choice
[    8.204023] hub 2-0:1.0: USB hub found
[    8.204029] hub 2-0:1.0: 2 ports detected
[    8.258817] SCSI subsystem initialized
[    8.263916] libata version 2.21 loaded.
[    8.307717] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
[    8.307729] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    8.307734] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    8.307761] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    8.307797] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000bf40
[    8.307888] usb usb3: configuration #1 chosen from 1 choice
[    8.307917] hub 3-0:1.0: USB hub found
[    8.307923] hub 3-0:1.0: 2 ports detected
[    8.411613] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
[    8.411626] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    8.411630] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    8.411656] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    8.411690] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000bf20
[    8.411785] usb usb4: configuration #1 chosen from 1 choice
[    8.411809] hub 4-0:1.0: USB hub found
[    8.411815] hub 4-0:1.0: 2 ports detected
[    3.920000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.924000] Time: hpet clocksource has been installed.
[    3.936000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[    3.936000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.936000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.936000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.936000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.936000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.936000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
[    3.940000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.940000] usb usb5: configuration #1 chosen from 1 choice
[    3.940000] hub 5-0:1.0: USB hub found
[    3.940000] hub 5-0:1.0: 8 ports detected
[    4.044000] b44.c:v1.01 (Jun 16, 2006)
[    4.044000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
[    4.044000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:1d:09:b6:0c:59
[    4.048000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
[    4.112000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.116000] ata_piix 0000:00:1f.2: version 2.11
[    4.116000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.116000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
[    4.116000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.116000] scsi0 : ata_piix
[    4.116000] scsi1 : ata_piix
[    4.120000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    4.120000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    4.284000] ata1.00: ATA-8: TOSHIBA MK1246GSX, LB212D, max UDMA/100
[    4.284000] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    4.292000] ata1.00: configured for UDMA/100
[    4.612000] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T21N, A102, max UDMA/33
[    4.784000] ata2.00: configured for UDMA/33
[    4.784000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1246GS LB21 PQ: 0 ANSI: 5
[    4.788000] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T21N A102 PQ: 0 ANSI: 5
[    4.804000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.804000] sd 0:0:0:0: [sda] Write Protect is off
[    4.804000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.804000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.804000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.804000] sd 0:0:0:0: [sda] Write Protect is off
[    4.804000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.804000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.804000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    4.872000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.876000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.876000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.904000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.904000] Uniform CD-ROM driver Revision: 3.20
[    4.904000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.352000] Attempting manual resume
[    5.352000] swsusp: Resume From Partition 8:6
[    5.352000] PM: Checking swsusp image.
[    5.352000] PM: Resume from disk failed.
[    5.388000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[324fc0000fecac70]
[    5.392000] kjournald starting.  Commit interval 5 seconds
[    5.392000] EXT3-fs: mounted filesystem with ordered data mode.
[   12.828000] Linux agpgart interface v0.102 (c) Dave Jones
[   12.868000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.880000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.900000] agpgart: Detected an Intel 945GM Chipset.
[   12.900000] agpgart: Detected 7932K stolen memory.
[   12.916000] agpgart: AGP aperture is 256M @ 0xd0000000
[   13.572000] iTCO_vendor_support: vendor-support=0
[   13.604000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   13.604000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   13.604000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.632000] intel_rng: FWH not detected
[   14.064000] input: PC Speaker as /class/input/input2
[   14.096000] sdhci: Secure Digital Host Controller Interface driver
[   14.096000] sdhci: Copyright(c) Pierre Ossman
[   14.096000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
[   14.096000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
[   14.096000] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
[   14.412000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
[   14.412000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   14.636000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   14.672000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   15.144000] lp: driver loaded but no devices found
[   15.220000] ndiswrapper version 1.45 loaded (smp=yes)
[   15.300000] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   15.300000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.300000] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   15.308000] ndiswrapper: using IRQ 16
[   15.680000] wlan0: ethernet device 00:1e:4c:8c:fd:5b using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
[   15.680000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   15.684000] usbcore: registered new interface driver ndiswrapper
[   15.708000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   15.740000] Adding 497972k swap on /dev/sda6.  Priority:-1 extents:1 across:497972k
[   16.120000] EXT3 FS on sda5, internal journal
[   17.240000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   17.248000] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   17.248000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   17.280000] ACPI: Battery Slot [BAT0] (battery present)
[   17.324000] ACPI: AC Adapter [AC] (on-line)
[   17.340000] No dock devices found.
[   17.456000] input: Lid Switch as /class/input/input4
[   17.460000] ACPI: Lid Switch [LID]
[   17.492000] input: Power Button (CM) as /class/input/input5
[   17.496000] ACPI: Power Button (CM) [PBTN]
[   17.532000] input: Sleep Button (CM) as /class/input/input6
[   17.532000] ACPI: Sleep Button (CM) [SBTN]
[   18.616000] Failure registering capabilities with primary security module.
[   18.964000] ppdev: user-space parallel port driver
[   19.296000] audit(1208708129.126:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4921 profile="/usr/sbin/cupsd"
[   19.364000] apm: BIOS not found.
[   19.972000] Bluetooth: Core ver 2.11
[   19.972000] NET: Registered protocol family 31
[   19.972000] Bluetooth: HCI device and connection manager initialized
[   19.972000] Bluetooth: HCI socket layer initialized
[   19.996000] Bluetooth: L2CAP ver 2.8
[   19.996000] Bluetooth: L2CAP socket layer initialized
[   20.084000] Bluetooth: RFCOMM socket layer initialized
[   20.084000] Bluetooth: RFCOMM TTY layer initialized
[   20.084000] Bluetooth: RFCOMM ver 1.8
[   21.900000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   21.900000] b44: eth0: Flow control is off for TX and off for RX.
[   23.408000] [drm] Initialized drm 1.1.0 20060810
[   23.412000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.412000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   24.100000] NET: Registered protocol family 17
[   27.748000] NET: Registered protocol family 10
[   27.748000] lo: Disabled Privacy Extensions
[   27.748000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   38.608000] eth0: no IPv6 routers present
[  399.128000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  402.560000] eth0: no IPv6 routers present

---

### Post by kevdog on 2008-04-20
Ok, lets try this -- all we are trying to do is to see your network

sudo ifconfig eth1 down
sudo ifconfig eth0 down
sudo modprobe -r b44 
sudo modprobe -r ndiswrapper

sudo depmod -a  (Wait awhile and make sure no errors occur)

sudo modprobe ndiswrapper

sudo ifconfig eth1 up

iwlist scan

If nothing shows then to reactivate the wired connection
sudo modprobe b44 
sudo ifconfig eth1 down
sudo ifconfig eth0 up
sudo dhclient eth0

If nothing worked then post
lspci -nn  or if a usb wireless device lsusb -v

---

### Post by PatsyPoo on 2008-04-27
Sorry it's taken me so long. I've been away and since we got back I've been in bed, really really ill... I hope to be well enough to try all these tomorrow.
I'll let you know how I get on! Thanks for trying!

---

### Post by phildem on 2008-04-27
I just upgraded to Hardy Heron 8.04 from Gutsy 7.10.

Wireless worked smoothly in Gutsy, but is flaky in Heron.

Currently, (in Heron)...

I can see my own wireless (linksys), and neighbors (netgear), I can connect to my neighbors wireless network, and browse the internet, but cannot connect to my own wireless (linksys).

Have tried with and without WEP, 64 bit shared key (which worked in Gutsy)

Have tried with and without WICD/Network Manager. (which worked in Gutsy)

Obviously the network card/drivers work since I'm browsing and posting while piggybacked onto neighbors signal.

I can see and connect to neighbor using Network Manager, and WICD.
I can see but not connect to own wireless using Network Manager, and WICD.

Although I can see my own network, and connect to it by booting into windows, I can't connect in Ubuntu, Hardy Har Heron...

Any chance M$ had a hand in the network programming side of Heron...*grin*

Can't create own thread for this, so adding to this one, since its close to the problem I'm having, and searching the forums is somewhat busted...can only search 1 keyword at a time, which nets a huge number of hits when searching on such terms as heron, wireless, or linksys...

---

### Post by PatsyPoo on 2008-04-30
I've tried all those things you asked me to and it still doesn't work. Here's the output for lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

Thanks one more time!

---

