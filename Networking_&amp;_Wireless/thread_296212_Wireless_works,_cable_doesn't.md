---
title: "Wireless works, cable doesn't?????"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by T.K. on 2006-11-09
Hi!
I installed Ubuntu 6.10 a week or so ago on my Laptop (FSC Lifebook C 1320D) using the alternate installation CD (Desktop CD repeatedly hung up during installation). Up to now apart from minor things (USB-Headset) I had not much  trouble, amazing.
For installation I configured my Wireless-Card, since I did it in my living-room :-), worked without any problem. Now I wanted to switch to cable (Broadcom Onboard-Chip), but after deactivating eth1 (wireless) and activating eth0 (cable) nothing worked. I tried both static and DHCP, under WinXP the cable works, my router is set up properly... 

Here' my lspci:
tom@tom-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
06:03.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:03.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:03.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

and the ifconfig (wlan active):
eth0      Protokoll:Ethernet  Hardware Adresse 00:0B:5D:9A:1F:68
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177

eth1      Protokoll:Ethernet  Hardware Adresse 00:13:CE:F2:54:10
          inet Adresse:192.168.0.14  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::213:ceff:fef2:5410/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9736 errors:0 dropped:2 overruns:0 frame:0
          TX packets:6661 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:27843320 (26.5 MiB)  TX bytes:2299730 (2.1 MiB)
          Interrupt:209 Basisadresse:0xc000 Speicher:b0208000-b0208fff

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:4420 (4.3 KiB)  TX bytes:4420 (4.3 KiB)

and ifconfig (lan active)
tom@tom-laptop:~$ ifconfig
eth0      Protokoll:Ethernet  Hardware Adresse 00:0B:5D:9A:1F:68
          inet Adresse:192.168.0.16  Bcast:192.168.0.255  Maske:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:2836 (2.7 KiB)  TX bytes:2836 (2.7 KiB)
Any ideas?
Best regards, T.K.

---

### Post by FrodoB on 2006-11-09
Could you post an iwconfig and a dmesg as well please?

---

### Post by T.K. on 2006-11-09
OK, here we go:
Since I'm quite new to linux, I actually have no idea what you are looking for, but I hope it will help! Thx

alltag@tom-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"rostweb"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:0F:3D:48:BE:48   
          Bit Rate:48 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-39 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

sit0      no wireless extensions.

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003f690000 (usable)
[17179569.184000]  BIOS-e820: 000000003f690000 - 000000003f697000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003f697000 - 000000003f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0010000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 118MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 259728
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 30352 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 FUJ                                   ) @ 0x000f58f0
[17179569.184000] ACPI: RSDT (v001 FUJ    FJNB1A1  0x01070000 FUJ  0x00000100) @ 0x3f690507
[17179569.184000] ACPI: FADT (v001 FUJ    FJNB1A1  0x01070000 FUJ  0x00000100) @ 0x3f696f8c
[17179569.184000] ACPI: MADT (v001 FUJ    FJNB1A1  0x01070000 FUJ  0x00000100) @ 0x3f69663c
[17179569.184000] ACPI: SSDT (v001 FUJ    FJNB1A1  0x01070000 INTL 0x20030522) @ 0x3f696696
[17179569.184000] ACPI: SSDT (v001 FUJ    FJNB1A1  0x01070000 INTL 0x20030522) @ 0x3f696adb
[17179569.184000] ACPI: SSDT (v001 FUJ    FJNB1A1  0x01070000 INTL 0x20030522) @ 0x3f696cb7
[17179569.184000] ACPI: SSDT (v001 FUJ    FJNB1A1  0x01070000 MSFT 0x0100000e) @ 0x3f696ede
[17179569.184000] ACPI: MCFG (v001 FUJ    FJNB1A1  0x01070000 FUJ  0x00000100) @ 0x3f696f28
[17179569.184000] ACPI: BOOT (v001 FUJ    FJNB1A1  0x01070000 FUJ  0x00000100) @ 0x3f696f64
[17179569.184000] ACPI: DSDT (v001 FUJ    FJNB1A1  0x01070000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1729.271 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.132000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.132000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.164000] Memory: 1019932k/1038912k available (1910k kernel code, 18268k reserved, 1070k data, 308k init, 121408k highmem)
[17179571.164000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.244000] Calibrating delay using timer specific routine.. 3463.35 BogoMIPS (lpj=6926700)
[17179571.244000] Security Framework v1.0.0 initialized
[17179571.244000] SELinux:  Disabled at boot.
[17179571.244000] Mount-cache hash table entries: 512
[17179571.244000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179571.244000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179571.244000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179571.244000] CPU: L2 cache: 2048K
[17179571.244000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000180 00000000 00000000
[17179571.244000] Checking 'hlt' instruction... OK.
[17179571.260000] SMP alternatives: switching to UP code
[17179571.260000] Freeing SMP alternatives: 16k freed
[17179571.260000] checking if image is initramfs... it is
[17179571.792000] Freeing initrd memory: 5563k freed
[17179571.792000] ACPI: Core revision 20060707
[17179571.792000] ACPI: Looking for DSDT ... not found!
[17179571.796000] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[17179571.796000] Total of 1 processors activated (3463.35 BogoMIPS).
[17179571.796000] ENABLING IO-APIC IRQs
[17179571.796000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179571.940000] Brought up 1 CPUs
[17179571.940000] migration_cost=0
[17179571.940000] NET: Registered protocol family 16
[17179571.940000] EISA bus registered
[17179571.940000] ACPI: bus type pci registered
[17179571.940000] PCI: Using MMCONFIG
[17179571.940000] Setting up standard PCI resources
[17179571.944000] ACPI: Interpreter enabled
[17179571.944000] ACPI: Using IOAPIC for interrupt routing
[17179571.944000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.944000] PCI: Probing PCI hardware (bus 00)
[17179571.948000] Boot video device is 0000:00:02.0
[17179571.948000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179571.948000] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[17179571.948000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.952000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.952000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[17179571.952000] Please report the result to linux-kernel to fix this permanently
[17179571.952000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.956000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179571.956000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179571.960000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179571.960000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179571.960000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179571.960000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[17179571.960000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179571.960000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[17179571.960000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[17179571.960000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[17179571.960000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[17179571.960000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.960000] pnp: PnP ACPI init
[17179571.968000] pnp: PnP ACPI: found 11 devices
[17179571.968000] PnPBIOS: Disabled by ACPI PNP
[17179571.968000] PCI: Using ACPI for IRQ routing
[17179571.968000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.968000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179571.968000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179571.968000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179571.968000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.968000] PCI: Bridge: 0000:00:1c.0
[17179571.968000]   IO window: disabled.
[17179571.968000]   MEM window: b0100000-b01fffff
[17179571.968000]   PREFETCH window: disabled.
[17179571.968000] PCI: Bridge: 0000:00:1c.1
[17179571.968000]   IO window: disabled.
[17179571.968000]   MEM window: disabled.
[17179571.968000]   PREFETCH window: disabled.
[17179571.968000] PCI: Bus 7, cardbus bridge: 0000:06:03.0
[17179571.968000]   IO window: 00002000-000020ff
[17179571.968000]   IO window: 00002400-000024ff
[17179571.968000]   PREFETCH window: 50000000-51ffffff
[17179571.968000]   MEM window: 54000000-55ffffff
[17179571.968000] PCI: Bridge: 0000:00:1e.0
[17179571.968000]   IO window: 2000-2fff
[17179571.968000]   MEM window: b0200000-b02fffff
[17179571.968000]   PREFETCH window: 50000000-51ffffff
[17179571.968000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179571.968000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179571.968000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179571.968000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179571.968000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.968000] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179571.968000] NET: Registered protocol family 2
[17179572.008000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.008000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179572.008000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179572.008000] TCP: Hash tables configured (established 131072 bind 65536)
[17179572.008000] TCP reno registered
[17179572.008000] Simple Boot Flag at 0x7f set to 0x1
[17179572.008000] audit: initializing netlink socket (disabled)
[17179572.008000] audit(1163064912.008:1): initialized
[17179572.008000] highmem bounce pool size: 64 pages
[17179572.008000] VFS: Disk quotas dquot_6.5.1
[17179572.008000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.008000] Initializing Cryptographic API
[17179572.008000] io scheduler noop registered
[17179572.008000] io scheduler anticipatory registered
[17179572.008000] io scheduler deadline registered
[17179572.008000] io scheduler cfq registered (default)
[17179572.008000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179572.008000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179572.008000] assign_interrupt_mode Found MSI capability
[17179572.008000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179572.008000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179572.008000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179572.008000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 177
[17179572.008000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[17179572.008000] assign_interrupt_mode Found MSI capability
[17179572.008000] Allocate Port Service[0000:00:1c.1:pcie00]
[17179572.008000] Allocate Port Service[0000:00:1c.1:pcie02]
[17179572.008000] Allocate Port Service[0000:00:1c.1:pcie03]
[17179572.008000] isapnp: Scanning for PnP cards...
[17179572.364000] isapnp: No Plug & Play device found
[17179572.384000] Real Time Clock Driver v1.12ac
[17179572.384000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.384000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.388000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.388000] mice: PS/2 mouse device common for all mice
[17179572.388000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.388000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.388000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.388000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179572.400000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179572.400000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179572.404000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179572.404000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179572.404000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179572.404000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.404000] EISA: Probing bus 0 at eisa.0
[17179572.404000] Cannot allocate resource for EISA slot 1
[17179572.404000] Cannot allocate resource for EISA slot 2
[17179572.404000] EISA: Detected 0 cards.
[17179572.404000] TCP bic registered
[17179572.404000] NET: Registered protocol family 1
[17179572.404000] NET: Registered protocol family 8
[17179572.404000] NET: Registered protocol family 20
[17179572.404000] Using IPI No-Shortcut mode
[17179572.404000] ACPI: (supports S0 S3 S4 S5)
[17179572.404000] Freeing unused kernel memory: 308k freed
[17179572.568000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.536000] Capability LSM initialized
[17179573.564000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.840000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179573.840000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 209
[17179573.840000] ICH6: chipset revision 4
[17179573.840000] ICH6: not 100% native mode: will probe irqs later
[17179573.840000]     ide0: BM-DMA at 0x1410-0x1417, BIOS settings: hda:DMA, hdb:pio
[17179573.840000] Probing IDE interface ide0...
[17179574.576000] hda: _NEC DVD+/-RW ND-6650A, ATAPI CD/DVD-ROM drive
[17179575.248000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.264000] hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.264000] Uniform CD-ROM driver Revision: 3.20
[17179575.368000] SCSI subsystem initialized
[17179575.372000] libata version 1.20 loaded.
[17179575.372000] ahci 0000:00:1f.2: version 1.2
[17179575.372000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 217
[17179581.192000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179581.192000] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[17179581.192000] ahci 0000:00:1f.2: flags: 64bit ncq pm led slum part 
[17179581.192000] ata1: SATA max UDMA/133 cmd 0xF884A500 ctl 0x0 bmdma 0x0 irq 217
[17179581.192000] ata2: SATA max UDMA/133 cmd 0xF884A580 ctl 0x0 bmdma 0x0 irq 217
[17179581.192000] ata3: SATA max UDMA/133 cmd 0xF884A600 ctl 0x0 bmdma 0x0 irq 217
[17179581.192000] ata4: SATA max UDMA/133 cmd 0xF884A680 ctl 0x0 bmdma 0x0 irq 217
[17179581.568000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179581.568000] ata1: dev 0 cfg 49:2f00 82:346b 83:7f09 84:6063 85:3469 86:bf09 87:6063 88:203f
[17179581.568000] ata1: dev 0 ATA-7, max UDMA/100, 78140160 sectors: LBA48
[17179581.568000] ata1: dev 0 configured for UDMA/100
[17179581.568000] scsi0 : ahci
[17179581.936000] ata2: SATA link down (SStatus 0)
[17179581.936000] scsi1 : ahci
[17179582.856000] ata3: SATA link down (SStatus 0)
[17179582.856000] scsi2 : ahci
[17179583.224000] ata4: SATA link down (SStatus 0)
[17179583.224000] scsi3 : ahci
[17179583.224000]   Vendor: ATA       Model: FUJITSU MHV2040B  Rev: 0000
[17179583.224000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179583.232000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[17179583.232000] sda: Write Protect is off
[17179583.232000] sda: Mode Sense: 00 3a 00 00
[17179583.232000] SCSI device sda: drive cache: write back
[17179583.232000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[17179583.232000] sda: Write Protect is off
[17179583.232000] sda: Mode Sense: 00 3a 00 00
[17179583.232000] SCSI device sda: drive cache: write back
[17179583.232000]  sda: sda1 sda2 sda3
[17179583.660000] sd 0:0:0:0: Attached scsi disk sda
[17179583.996000] Probing IDE interface ide1...
[17179584.028000] usbcore: registered new driver usbfs
[17179584.028000] usbcore: registered new driver hub
[17179584.028000] USB Universal Host Controller Interface driver v3.0
[17179584.028000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 225
[17179584.028000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179584.028000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179584.032000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179584.032000] uhci_hcd 0000:00:1d.0: irq 225, io base 0x00001420
[17179584.032000] usb usb1: configuration #1 chosen from 1 choice
[17179584.032000] hub 1-0:1.0: USB hub found
[17179584.032000] hub 1-0:1.0: 2 ports detected
[17179584.096000] ieee1394: Initialized config rom entry `ip1394'
[17179584.136000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 217
[17179584.136000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179584.136000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179584.136000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179584.136000] uhci_hcd 0000:00:1d.1: irq 217, io base 0x00001440
[17179584.136000] usb usb2: configuration #1 chosen from 1 choice
[17179584.136000] hub 2-0:1.0: USB hub found
[17179584.136000] hub 2-0:1.0: 2 ports detected
[17179584.240000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[17179584.240000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179584.240000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179584.240000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179584.240000] uhci_hcd 0000:00:1d.2: irq 209, io base 0x00001460
[17179584.240000] usb usb3: configuration #1 chosen from 1 choice
[17179584.240000] hub 3-0:1.0: USB hub found
[17179584.240000] hub 3-0:1.0: 2 ports detected
[17179584.344000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 177
[17179584.344000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179584.344000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179584.344000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179584.344000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x00001480
[17179584.344000] usb usb4: configuration #1 chosen from 1 choice
[17179584.344000] hub 4-0:1.0: USB hub found
[17179584.344000] hub 4-0:1.0: 2 ports detected
[17179584.376000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[17179584.448000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 225
[17179584.448000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179584.448000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179584.448000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179584.448000] ehci_hcd 0000:00:1d.7: debug port 1
[17179584.448000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179584.448000] ehci_hcd 0000:00:1d.7: irq 225, io mem 0xb0004000
[17179584.452000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179584.452000] usb usb5: configuration #1 chosen from 1 choice
[17179584.452000] hub 5-0:1.0: USB hub found
[17179584.452000] hub 5-0:1.0: 8 ports detected
[17179584.556000] ACPI: PCI Interrupt 0000:06:03.2[C] -> GSI 16 (level, low) -> IRQ 177
[17179584.604000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[b0206000-b02067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179584.664000] Attempting manual resume
[17179584.692000] kjournald starting.  Commit interval 5 seconds
[17179584.692000] EXT3-fs: mounted filesystem with ordered data mode.
[17179584.900000] usb 1-2: device not accepting address 2, error -71
[17179585.692000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[17179585.876000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000e10036216e1]
[17179585.920000] usb 1-2: configuration #1 chosen from 1 choice
[17179586.164000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[17179586.316000] usb 2-2: configuration #1 chosen from 1 choice
[17179595.496000] input: PC Speaker as /class/input/input1
[17179595.612000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179595.648000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.768000] parport: PnPBIOS parport detected.
[17179595.768000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179595.800000] hw_random: RNG not detected
[17179596.396000] tg3.c:v3.59.1 (August 25, 2006)
[17179596.396000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179596.396000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179596.440000] Linux agpgart interface v0.101 (c) Dave Jones
[17179596.444000] agpgart: Detected an Intel 915GM Chipset.
[17179596.444000] agpgart: Detected 7932K stolen memory.
[17179596.464000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179596.648000] eth0: Tigon3 [partno(BCM95751M) rev 4101 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:0b:5d:9a:1f:68
[17179596.648000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[17179596.648000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[17179596.752000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xf8eb1, caps: 0xa04793/0x102000
[17179596.752000] serio: Synaptics pass-through port at isa0060/serio4/input0
[17179596.792000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179596.940000] usbcore: registered new driver hiddev
[17179596.964000] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179596.964000] Yenta: CardBus bridge found at 0000:06:03.0 [10cf:12d2]
[17179596.964000] Yenta: Enabling burst memory read transactions
[17179596.964000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179596.964000] Yenta: Routing CardBus interrupts to PCI
[17179596.964000] Yenta TI: socket 0000:06:03.0, mfunc 0x01c01b22, devctl 0x65
[17179596.988000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179596.988000] sdhci: Copyright(c) Pierre Ossman
[17179597.028000] ieee80211_crypt: registered algorithm 'NULL'
[17179597.036000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179597.036000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179597.056000] input: Plantronics Plantronics Headset as /class/input/input3
[17179597.056000] input: USB HID v1.00 Device [Plantronics Plantronics Headset] on usb-0000:00:1d.0-2
[17179597.064000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179597.064000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179597.064000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179597.104000] input: HID 062a:0000 as /class/input/input4
[17179597.104000] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.1-2
[17179597.104000] usbcore: registered new driver usbhid
[17179597.104000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179597.304000] Yenta: ISA IRQ mask 0x0c78, PCI irq 177
[17179597.304000] Socket status: 30000006
[17179597.304000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[17179597.304000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179597.304000] cs: IO port probe 0x2000-0x2fff: clean.
[17179597.304000] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[17179597.304000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
[17179597.304000] ACPI: PCI Interrupt 0000:06:03.3[B] -> GSI 17 (level, low) -> IRQ 169
[17179597.304000] sdhci: SDHCI controller found at 0000:06:03.4 [104c:8034] (rev 0)
[17179597.304000] ACPI: PCI Interrupt 0000:06:03.4[B] -> GSI 17 (level, low) -> IRQ 169
[17179597.304000] mmc0: SDHCI at 0xb0207000 irq 169 DMA
[17179597.304000] mmc1: SDHCI at 0xb0206c00 irq 169 DMA
[17179597.304000] mmc2: SDHCI at 0xb0206800 irq 169 DMA
[17179597.304000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179597.304000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179597.440000] ts: Compaq touchscreen protocol output
[17179597.528000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179597.700000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179597.700000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179597.820000] usbcore: registered new driver snd-usb-audio
[17179597.940000] cs: IO port probe 0x100-0x3af: clean.
[17179597.940000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179597.940000] cs: IO port probe 0x820-0x8ff: clean.
[17179597.940000] cs: IO port probe 0xc00-0xcf7: clean.
[17179597.948000] cs: IO port probe 0xa00-0xaff: clean.
[17179598.216000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[17179598.260000] ieee80211_crypt: registered algorithm 'WEP'
[17179598.956000] hda_intel: azx_get_response timeout, switching to single_cmd mode...
[17179599.288000] NET: Registered protocol family 17
[17179601.176000] input: PS/2 Generic Mouse as /class/input/input5
[17179602.152000] NET: Registered protocol family 10
[17179602.152000] lo: Disabled Privacy Extensions
[17179602.152000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179602.152000] IPv6 over IPv4 tunneling driver
[17179606.104000] lp0: using parport0 (interrupt-driven).
[17179606.124000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179606.124000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179606.144000] Adding 361452k swap on /dev/disk/by-uuid/60ec4223-c80d-451c-a01d-5a5079ec54d7.  Priority:-1 extents:1 across:361452k
[17179606.232000] EXT3 FS on sda2, internal journal
[17179606.472000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179606.524000] NTFS volume version 3.1.
[17179611.204000] ACPI: AC Adapter [AC] (on-line)
[17179611.240000] ACPI: Battery Slot [CMB1] (battery present)
[17179611.240000] ACPI: Battery Slot [CMB2] (battery absent)
[17179611.256000] ACPI: Power Button (FF) [PWRF]
[17179611.256000] ACPI: Lid Switch [LID]
[17179611.256000] ACPI: Power Button (CM) [PWRB]
[17179611.428000] ibm_acpi: ec object not found
[17179611.452000] pcc_acpi: loading...
[17179611.576000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[17179612.192000] eth1: no IPv6 routers present
[17179614.424000] [drm] Initialized drm 1.0.1 20051102
[17179614.428000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179614.428000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179615.580000] apm: BIOS not found.
[17179620.488000] Bluetooth: Core ver 2.8
[17179620.488000] NET: Registered protocol family 31
[17179620.488000] Bluetooth: HCI device and connection manager initialized
[17179620.488000] Bluetooth: HCI socket layer initialized
[17179620.520000] Bluetooth: L2CAP ver 2.8
[17179620.520000] Bluetooth: L2CAP socket layer initialized
[17179620.548000] Bluetooth: RFCOMM socket layer initialized
[17179620.548000] Bluetooth: RFCOMM TTY layer initialized
[17179620.548000] Bluetooth: RFCOMM ver 1.7
[17183612.528000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17183663.336000] eth1: no IPv6 routers present
[17183738.912000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17183786.728000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17198025.692000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17198601.372000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17200369.888000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17200510.744000] eth1: no IPv6 routers present
[17200543.960000] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by FrodoB on 2006-11-09
Well when the local lan is active you are getting an IP address, was that static or from dhcp?

Have you tired opening a terminal window and starting dhclinet to get another one from dhcp?

$ sudo dhclient

Maybe you should run:

$ sudo netstat -rn 

both before and after.  You should see something like:

user@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 rausb0
0.0.0.0         192.168.1.3     0.0.0.0         UG        0 0          0 rausb0

It almost sounds like you don't have a gateway out of your lan to a router on the net.

---

### Post by T.K. on 2006-11-10
The IP is static, I don't even get a connection to my router for DHCP.
dhclient repeatedly tries to "dhcpdiscover" but that's it.
With my wlan active it gets a connection immediately...

netstat wlan active:
Ziel            Router          Genmask         Flags   MSS Fenster irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth1

wlan off, eth0 on:
Ziel            Router          Genmask         Flags   MSS Fenster irtt Iface

So the Gateway is missing, right? But why, I did configure both wlan/lan the same. I used the gnome default installed Network Configuration tool.
Thanks for your help so far! Maybe you have any idea...?

---

### Post by FrodoB on 2006-11-10
See if this works temporarily from a terminal window:

$ sudo route add default gw 192.168.0.1

Then do a netstat -rn to see if it took it:

$ netstat -rn

If it looks good then try to ping the gateway or maybe be brave and ping [www.redhat.com](www.redhat.com)

---

### Post by T.K. on 2006-11-10
nope, looks good in netstat reply, but ping goes to nirvana... ](*,) 
I will try to boot from a desktop cd I just burned and see, if it works at all...well after all, I've still got the wireless, so I can connect this way for now :rolleyes: 

Thanks for your help so far!

---

### Post by FrodoB on 2006-11-10
Extreme outside shot. Have you looked at this post where a gentleman's new ethernet card did not work:

[http://www.ubuntuforums.org/showthread.php?t=296884](http://www.ubuntuforums.org/showthread.php?t=296884)

Could your problem be related? Not likely but worth a look.

---

### Post by T.K. on 2006-11-11
I don't think so, because my card is being recognised and the tg3 driver is advised, so this part should be OK. 
But maybe it's simply  not possible to use WLAN and LAN on the same computer, even if one is deactivated. What's making me a bit nervous is, that the edubuntu 6.06 and ubuntu 6.10 Boot-CDs show the same problem. I haven't tried other distros, but at time I will give suse a shot. 
On monday I will do a WinXP check at work (my Win config is adapted to my at-hospital constellation and I only have limited admin rights, for data security)to see if it still works there - getting paranoid... 8)

---

### Post by FrodoB on 2006-11-12
They should work together. I have two wireless and one wired connection running on 6.10 at the moment. Did you say that you tried running live with only the wired connection available?

---

### Post by T.K. on 2006-11-13
No, wired doesn't work...
BUT, even worse: today I went to work after two weeks and my WinXP can't connect any more either!!! Before there was nothing wrong, so I'm thinking of any way the linux installation could have messed something up, but actually I can't see why this should be. I didn't change the bios settings and the Win-Partition is untouched. Well, maybe a concidence of defect internal LAN and trying ubuntu...
Bad luck :confused: 

Thank you for trying to help me, but I think I simply need a repair (still guarantee...).

---

