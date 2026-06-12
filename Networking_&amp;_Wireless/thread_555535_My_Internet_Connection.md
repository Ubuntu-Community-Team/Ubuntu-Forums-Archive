---
title: "My Internet Connection???"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by fletcham on 2007-09-20
Hello.

I have just built my first pc and after solving a few problems using this site (thanks a lot) I have installed ubuntu. The computer seems to be running fine and is set up next to my brothers pc which runs xp. I switched the internet cable from his pc to mine and tried to connect to the internet but could not.

Is there more to it than simply switching the cable over?

Thanks for your help!!

P.S. As you can probably tell I am no whizz on computers so any help would be greatly appreciated.

---

### Post by buzzmandt on 2007-09-20
post the output of these
> lspci
> ifconfig
also turn your computer on after you switch the cable and then run these two commands i've listed

---

### Post by fletcham on 2007-09-20
These are the results:

lspci:
0000:00:00.0 RAM memory: nvidia corporation: Unknown device 03ea (reva1)
0000:00:01.0 ISA Bridge: nvidia corporation: Unknown device 03e0 (reva2)
0000:00:01.1 SMBus: nvidia corporation: Unknown device 03eb (reva2)
0000:00:01.2 RAM memory: nvidia corporation: Unknown device 03f5 (reva2)
0000:00:02.0 USB Controller: nvidia corporation: Unknown device 03f1 (reva2)
0000:00:02.1 USB Controller: nvidia corporation: Unknown device 03f2 (reva2)
0000:00:04.0 PCI Bridge: nvidia corporation: Unknown device 03f3 (reva1)
0000:00:05.0 0403: nvidia corporation: Unknown device 03f0 (reva2)
0000:00:06.0 IDE interface: nvidia corporation: Unknown device 03ec (reva2)
0000:00:07.0 Bridge: nvidia corporation: Unknown device 03ef (reva2)
0000:00:08.0 IDE interface: nvidia corporation: Unknown device 03f6 (reva2)
0000:00:08.1 IDE interface: nvidia corporation: Unknown device 03f6 (reva2)
0000:00:09.0 PCI Bridge: nvidia corporation: Unknown device 03e8 (reva2)
0000:00:0b.0 PCI Bridge: nvidia corporation: Unknown device 03e9(reva2)
0000:00:0c.0 PCI Bridge: nvidia corporation: Unknown device 03e9 (reva2)
0000:00:0d.0 VGA Compatible controller: nvidia corporation: Unknown device 03d0 (reva2)
0000:00:18.0 Host Bridge: Advanced Micro Devices (AMD) k8 (Athlon 64 / Opteron) Hyper transport technology configuration
0000:00:18.1 Host Bridge: Advanced Micro Devices (AMD) k8 (Athlon 64 / Opteron) Address Map
0000:00:18.2 Host Bridge: Advanced Micro Devices (AMD) k8 (Athlon 64 / Opteron) DRAM Controller
0000:00:18.3 Host Bridge: Advanced Micro Devices (AMD) k8 (Athlon 64 / Opteron) Miscellaneous Control


ifconfig:
Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0
inet6 addr: :: 1/128 Scope : Host
UP LOOPBACK RUNNING MTU : 16436 Metric : 1
RX Packets: 651 errors: 0 dropped:0 overruns:0 frame:0 
TX packets: 651 errors: 0 dropped:0 overruns:0 carrier: 0 collisions: 0 txqueuelen: 0
RX bytes: 32572 (31.8KiB) TX bytes: 32572 (31.8KiB)


Thanks again for helping!!

---

### Post by noob12 on 2007-09-20
I don't see any ethernet device there.  But clearly you've plugged an ethernet cable into the back, so this suggests that you have some fundamental PCI routing issues at boot.  Posting your whole
```

dmesg

```
might provide clues.

Also, are you running the regular desktop edition of Ubuntu 7.04 (Feisty) or a different release?  Can you post what **uname -a** says?

Some suggestions:

You should try booting from the hard drive with the **pci=noacpi** boot flag and seeing if that helps.

Did you try the LiveCD before installing?  Was networking working when you booted the LiveCD?

---

### Post by mips on 2007-09-20
What is an "internet cable" is it a USB cable or an Ethernet cable ?

---

### Post by fletcham on 2007-09-21
Hi, sorry to ask simple questions like this but i really dont know much about computers.

How do I boot with the pci=noacpi boot flag?

Cheers guys!!!

---

### Post by fletcham on 2007-09-21
p.s. and yes when i said internet cable I meant ethernet cable. :confused:

---

### Post by noob12 on 2007-09-21
How about posting the output of **dmesg**?  as we've got nothing really diagnostic so far.

---

### Post by fletcham on 2007-09-22
lspci:

0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 03ea (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 03e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 03eb (rev a2)
0000:00:01.2 RAM memory: nVidia Corporation: Unknown device 03f5 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 03f1 (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 03f2 (rev a2)
0000:00:04.0 PCI bridge: nVidia Corporation: Unknown device 03f3 (rev a1)
0000:00:05.0 0403: nVidia Corporation: Unknown device 03f0 (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 03ec (rev a2)
0000:00:07.0 Bridge: nVidia Corporation: Unknown device 03ef (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 03f6 (rev a2)
0000:00:08.1 IDE interface: nVidia Corporation: Unknown device 03f6 (rev a2)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 03e8 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2)
0000:00:0d.0 VGA compatible controller: nVidia Corporation: Unknown device 03d0 (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

ifconfig:

Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:34572 (33.7 KiB)  TX bytes:34572 (33.7 KiB)

dmesg:

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000077fc0000 (usable)
[17179569.184000]  BIOS-e820: 0000000077fc0000 - 0000000077fce000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000077fce000 - 0000000077ff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000077ff0000 - 0000000078000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[17179569.184000] 1023MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 491456
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 262080 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fb840
[17179569.184000] ACPI: RSDT (v001 _ASUS_ Notebook 0x05000728 MSFT 0x00000097) @ 0x77fc0000
[17179569.184000] ACPI: FADT (v002 A_M_I_ OEMFACP  0x05000728 MSFT 0x00000097) @ 0x77fc0200
[17179569.184000] ACPI: MADT (v001 A_M_I_ OEMAPIC  0x05000728 MSFT 0x00000097) @ 0x77fc0390
[17179569.184000] ACPI: MCFG (v001 A_M_I_ OEMMCFG  0x05000728 MSFT 0x00000097) @ 0x77fc0400
[17179569.184000] ACPI: SLIC (v001 _ASUS_ Notebook 0x05000728 MSFT 0x00000097) @ 0x77fc0440
[17179569.184000] ACPI: OEMB (v001 A_M_I_ AMI_OEM  0x05000728 MSFT 0x00000097) @ 0x77fce040
[17179569.184000] ACPI: HPET (v001 A_M_I_ OEMHPET0 0x05000728 MSFT 0x00000097) @ 0x77fc53d0
[17179569.184000] ACPI: DSDT (v001  A0557 A0557000 0x00000000 INTL 0x20051117) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x508
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:11 APIC version 16
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:11 APIC version 16
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[17179569.184000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[17179569.184000] Using ACPI for processor (LAPIC) configuration information
[17179569.184000] Intel MultiProcessor Specification v1.4
[17179569.184000]     Virtual Wire compatibility mode.
[17179569.184000] OEM ID: TEMPLATE Product ID:  APIC at: 0xFEE00000
[17179569.184000] I/O APIC #2 Version 17 at 0xFEC00000.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Processors: 1
[17179569.184000] Allocating PCI resources starting at 80000000 (gap: 78000000:86c00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash noapic
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] spurious 8259A interrupt: IRQ7.
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179569.184000] Memory: 1938352k/1965824k available (1976k kernel code, 26332k reserved, 606k data, 288k init, 1048320k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 31
[17179569.184000] hpet0: 3 32-bit timers, 25000000 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 2310.665 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 4625.67 BogoMIPS (lpj=9251354)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[17179569.268000] CPU: After vendor identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[17179569.268000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.268000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.268000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[17179569.268000] mtrr: v2.0 (20020519)
[17179569.268000] CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 01
[17179569.268000] Enabling fast FPU save and restore... done.
[17179569.268000] Enabling unmasked SIMD FPU exception support... done.
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] checking if image is initramfs... it is
[17179569.724000] Freeing initrd memory: 6840k freed
[17179569.728000] ACPI: Looking for DSDT ... not found!
[17179569.728000] ACPI: setting ELCR to 0200 (from 8c20)
[17179569.836000] NET: Registered protocol family 16
[17179569.836000] EISA bus registered
[17179569.836000] ACPI: bus type pci registered
[17179569.836000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[17179569.836000] PCI: Using MMCONFIG
[17179569.836000] ACPI: Subsystem revision 20051216
[17179569.840000] ACPI: Interpreter enabled
[17179569.840000] ACPI: Using PIC for interrupt routing
[17179569.840000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179569.840000] PCI: Probing PCI hardware (bus 00)
[17179569.844000] Boot video device is 0000:00:0d.0
[17179569.844000] PCI: Transparent bridge - 0000:00:04.0
[17179569.844000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179569.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179569.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[17179569.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[17179569.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[17179569.860000] ACPI: PCI Interrupt Link [LNKA] (IRQs 7 10 11 14) *0, disabled.
[17179569.860000] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 10 11 14) *0, disabled.
[17179569.860000] ACPI: PCI Interrupt Link [LNKC] (IRQs 7 10 11 14) *0, disabled.
[17179569.860000] ACPI: PCI Interrupt Link [LNKD] (IRQs 7 10 11 14) *0, disabled.
[17179569.860000] ACPI: PCI Interrupt Link [LNEA] (IRQs 7 10 11 14) *0, disabled.
[17179569.860000] ACPI: PCI Interrupt Link [LNEB] (IRQs 7 10 11 14) *0, disabled.
[17179569.860000] ACPI: PCI Interrupt Link [LNEC] (IRQs 7 10 11 14) *0, disabled.
[17179569.860000] ACPI: PCI Interrupt Link [LNED] (IRQs 7 10 11 14) *0, disabled.
[17179569.860000] ACPI: PCI Interrupt Link [LUB0] (IRQs 7 10 *11 14)
[17179569.864000] ACPI: PCI Interrupt Link [LUB2] (IRQs 7 *10 11 14)
[17179569.864000] ACPI: PCI Interrupt Link [LMAC] (IRQs 7 10 *11 14)
[17179569.864000] ACPI: PCI Interrupt Link [LAZA] (IRQs 7 10 *11 14)
[17179569.864000] ACPI: PCI Interrupt Link [LACI] (IRQs 7 10 11 14) *0, disabled.
[17179569.864000] ACPI: PCI Interrupt Link [LMC9] (IRQs 7 10 *11 14)
[17179569.864000] ACPI: PCI Interrupt Link [LSMB] (IRQs 7 *10 11 14)
[17179569.864000] ACPI: PCI Interrupt Link [LPMU] (IRQs 7 10 11 14) *0, disabled.
[17179569.864000] ACPI: PCI Interrupt Link [LSA0] (IRQs *15)
[17179569.864000] ACPI: PCI Interrupt Link [LSA1] (IRQs *5)
[17179569.864000] ACPI: PCI Interrupt Link [LATA] (IRQs 7 10 11 14) *0, disabled.
[17179569.864000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179569.864000] pnp: PnP ACPI init
[17179569.872000] pnp: PnP ACPI: found 15 devices
[17179569.872000] PnPBIOS: Disabled by ACPI PNP
[17179569.872000] PCI: Using ACPI for IRQ routing
[17179569.872000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179569.880000] pnp: 00:0b: ioport range 0x230-0x23f has been reserved
[17179569.880000] pnp: 00:0b: ioport range 0x290-0x29f has been reserved
[17179569.880000] pnp: 00:0b: ioport range 0xa00-0xa0f has been reserved
[17179569.880000] pnp: 00:0b: ioport range 0xa10-0xa1f has been reserved
[17179569.880000] PCI: Bridge: 0000:00:04.0
[17179569.880000]   IO window: disabled.
[17179569.880000]   MEM window: disabled.
[17179569.880000]   PREFETCH window: disabled.
[17179569.880000] PCI: Bridge: 0000:00:09.0
[17179569.880000]   IO window: disabled.
[17179569.880000]   MEM window: disabled.
[17179569.880000]   PREFETCH window: disabled.
[17179569.880000] PCI: Bridge: 0000:00:0b.0
[17179569.880000]   IO window: disabled.
[17179569.880000]   MEM window: disabled.
[17179569.880000]   PREFETCH window: disabled.
[17179569.880000] PCI: Bridge: 0000:00:0c.0
[17179569.880000]   IO window: disabled.
[17179569.880000]   MEM window: disabled.
[17179569.880000]   PREFETCH window: disabled.
[17179569.880000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179569.880000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[17179569.880000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179569.880000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179569.880000] audit: initializing netlink socket (disabled)
[17179569.880000] audit(1190483745.880:1): initialized
[17179569.880000] highmem bounce pool size: 64 pages
[17179569.880000] VFS: Disk quotas dquot_6.5.1
[17179569.880000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179569.880000] Initializing Cryptographic API
[17179569.880000] io scheduler noop registered
[17179569.880000] io scheduler anticipatory registered
[17179569.880000] io scheduler deadline registered
[17179569.880000] io scheduler cfq registered
[17179577.880000] 0000:00:02.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[17179577.880000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[17179577.880000] pcie_portdrv_probe->Dev[03e8:10de] has invalid IRQ. Check vendor BIOS
[17179577.880000] assign_interrupt_mode Found MSI capability
[17179577.880000] Allocate Port Service[pcie00]
[17179577.880000] Allocate Port Service[pcie03]
[17179577.880000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179577.880000] pcie_portdrv_probe->Dev[03e9:10de] has invalid IRQ. Check vendor BIOS
[17179577.880000] assign_interrupt_mode Found MSI capability
[17179577.880000] Allocate Port Service[pcie00]
[17179577.880000] Allocate Port Service[pcie03]
[17179577.880000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179577.880000] pcie_portdrv_probe->Dev[03e9:10de] has invalid IRQ. Check vendor BIOS
[17179577.880000] assign_interrupt_mode Found MSI capability
[17179577.880000] Allocate Port Service[pcie00]
[17179577.880000] Allocate Port Service[pcie03]
[17179577.880000] isapnp: Scanning for PnP cards...
[17179578.236000] isapnp: No Plug & Play device found
[17179578.244000] hpet_resources: 0xfed00000 is busy
[17179578.244000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179578.244000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179578.244000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179578.244000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179578.244000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179578.244000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179578.244000] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179578.244000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179578.244000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179578.244000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179578.244000] mice: PS/2 mouse device common for all mice
[17179578.244000] EISA: Probing bus 0 at eisa.0
[17179578.244000] Cannot allocate resource for EISA slot 2
[17179578.244000] EISA: Detected 0 cards.
[17179578.244000] NET: Registered protocol family 2
[17179578.280000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179578.280000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179578.280000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179578.280000] TCP: Hash tables configured (established 262144 bind 65536)
[17179578.280000] TCP reno registered
[17179578.280000] TCP bic registered
[17179578.280000] NET: Registered protocol family 1
[17179578.280000] NET: Registered protocol family 8
[17179578.280000] NET: Registered protocol family 20
[17179578.280000] Using IPI Shortcut mode
[17179578.280000] ACPI wakeup devices:
[17179578.280000] PS2K UAR1 USB0 USB2 P0P1 HDAC P0P2 BR11 NMAC NSMB PWRB
[17179578.280000] ACPI: (supports S0 S1 S3 S4 S5)
[17179578.280000] Freeing unused kernel memory: 288k freed
[17179578.304000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179578.316000] vga16fb: initializing
[17179578.316000] vga16fb: mapped to 0xc00a0000
[17179578.512000] Console: switching to colour frame buffer device 80x25
[17179578.512000] fb0: VGA16 VGA frame buffer device
[17179579.580000] Capability LSM initialized
[17179580.140000] SCSI subsystem initialized
[17179580.144000] ACPI: bus type scsi registered
[17179580.144000] libata version 1.20 loaded.
[17179580.144000] sata_nv 0000:00:08.0: version 0.8
[17179580.144000] **** SET: Misaligned resource pointer: dfe77b02 Type 07 Len 0
[17179580.144000] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 15
[17179580.144000] PCI: setting IRQ 15 as level-triggered
[17179580.144000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LSA0] -> GSI 15 (level, low) -> IRQ 15
[17179580.144000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179580.144000] ata1: SATA max UDMA/133 cmd 0xE400 ctl 0xE082 bmdma 0xD880 irq 15
[17179580.144000] ata2: SATA max UDMA/133 cmd 0xE000 ctl 0xDC02 bmdma 0xD888 irq 15
[17179580.528000] ata1: dev 0 cfg 00:0040 49:2f00 82:746b 83:7f01 84:4123 85:7469 86:bc01 87:4123 88:40ff 93:0000
[17179580.528000] ata1: dev 0 ATA-8, max UDMA7, 976773168 sectors: LBA48
[17179580.528000] sata_get_dev_handle: SATA dev addr=0x80000, handle=0xdffe7900
[17179580.532000] ata1: dev 0 configured for UDMA/133
[17179580.532000] sata_get_dev_handle: SATA dev addr=0x80000, handle=0xdffe7900
[17179580.540000] scsi0 : sata_nv
[17179580.744000] ata2: no device found (phy stat 00000000)
[17179580.744000] scsi1 : sata_nv
[17179580.744000]   Vendor: ATA       Model: SAMSUNG HD501LJ   Rev: CR10
[17179580.744000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179580.744000] **** SET: Misaligned resource pointer: dfe77902 Type 07 Len 0
[17179580.744000] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 5
[17179580.744000] PCI: setting IRQ 5 as level-triggered
[17179580.744000] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [LSA1] -> GSI 5 (level, low) -> IRQ 5
[17179580.744000] PCI: Setting latency timer of device 0000:00:08.1 to 64
[17179580.744000] ata3: SATA max UDMA/133 cmd 0xD800 ctl 0xD482 bmdma 0xD000 irq 5
[17179580.744000] ata4: SATA max UDMA/133 cmd 0xD400 ctl 0xD082 bmdma 0xD008 irq 5
[17179580.748000] Driver 'sd' needs updating - please use bus_type methods
[17179580.748000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[17179580.748000] SCSI device sda: drive cache: write back
[17179580.748000] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[17179580.748000] SCSI device sda: drive cache: write back
[17179580.748000]  sda: sda1 sda2 < sda5 >
[17179580.836000] sd 0:0:0:0: Attached scsi disk sda
[17179580.948000] ata3: no device found (phy stat 00000000)
[17179580.948000] scsi2 : sata_nv
[17179581.152000] ata4: no device found (phy stat 00000000)
[17179581.152000] scsi3 : sata_nv
[17179581.276000] usbcore: registered new driver usbfs
[17179581.276000] usbcore: registered new driver hub
[17179581.276000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179581.276000] **** SET: Misaligned resource pointer: dfe77402 Type 07 Len 0
[17179581.276000] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 11
[17179581.276000] PCI: setting IRQ 11 as level-triggered
[17179581.276000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUB0] -> GSI 11 (level, low) -> IRQ 11
[17179581.276000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179581.276000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179581.800000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179581.800000] ohci_hcd 0000:00:02.0: irq 11, io mem 0xdffff000
[17179581.856000] hub 1-0:1.0: USB hub found
[17179581.856000] hub 1-0:1.0: 10 ports detected
[17179581.960000] **** SET: Misaligned resource pointer: dfe77102 Type 07 Len 0
[17179581.960000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 10
[17179581.960000] PCI: setting IRQ 10 as level-triggered
[17179581.960000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 10 (level, low) -> IRQ 10
[17179581.960000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179581.960000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[17179581.960000] ehci_hcd 0000:00:02.1: debug port 1
[17179581.960000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[17179581.960000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179581.960000] ehci_hcd 0000:00:02.1: irq 10, io mem 0xdfffec00
[17179581.960000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179581.960000] hub 2-0:1.0: USB hub found
[17179581.960000] hub 2-0:1.0: 10 ports detected
[17179582.088000] Probing IDE interface ide0...
[17179582.304000] ohci_hcd 0000:00:02.0: wakeup
[17179582.688000] usb 1-1: new low speed USB device using ohci_hcd and address 2[17179582.908000] usbcore: registered new driver hiddev
[17179582.920000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
[17179582.920000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-1
[17179582.920000] usbcore: registered new driver usbhid
[17179582.920000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179582.952000] hda: TSSTcorpCD/DVDW SH-S182M, ATAPI CD/DVD-ROM drive
[17179583.624000] Probing IDE interface ide1...
[17179584.184000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179584.192000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[17179584.192000] Uniform CD-ROM driver Revision: 3.20
[17179584.228000] Attempting manual resume
[17179584.260000] EXT3-fs: mounted filesystem with ordered data mode.
[17179584.276000] kjournald starting.  Commit interval 5 seconds
[17179589.800000] ts: Compaq touchscreen protocol output
[17179589.944000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179591.380000] input: PC Speaker as /class/input/input2
[17179591.740000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.752000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.780000] parport: PnPBIOS parport detected.
[17179591.780000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179591.808000] Real Time Clock Driver v1.12
[17179591.820000] Floppy drive(s): fd0 is 1.44M
[17179591.824000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.836000] nvidia: module license 'NVIDIA' taints kernel.
[17179591.840000] **** SET: Misaligned resource pointer: f780e7c2 Type 07 Len 0
[17179591.840000] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 11
[17179591.840000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LMC9] -> GSI 11 (level, low) -> IRQ 11
[17179591.840000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179591.840000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179591.876000] FDC 0 is a post-1991 82077
[17179597.416000] lp0: using parport0 (interrupt-driven).
[17179597.456000] Adding 5703032k swap on /dev/sda5.  Priority:-1 extents:1 across:5703032k
[17179597.592000] EXT3 FS on sda1, internal journal
[17179597.704000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179597.704000] md: bitmap version 4.39
[17179598.092000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179598.620000] cdrom: open failed.
[17179600.376000] NET: Registered protocol family 17
[17179605.324000] ACPI: Power Button (FF) [PWRF]
[17179605.324000] ACPI: Power Button (CM) [PWRB]
[17179605.396000] ibm_acpi: ec object not found
[17179605.420000] pcc_acpi: loading...
[17179605.816000] powernow-k8: Processor cpuid 60fb1 not supported
[17179609.052000] ppdev: user-space parallel port driver
[17179609.280000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179609.280000] apm: overridden by ACPI.
[17179611.812000] Bluetooth: Core ver 2.8
[17179611.812000] NET: Registered protocol family 31
[17179611.812000] Bluetooth: HCI device and connection manager initialized
[17179611.812000] Bluetooth: HCI socket layer initialized
[17179611.832000] Bluetooth: L2CAP ver 2.8
[17179611.832000] Bluetooth: L2CAP socket layer initialized
[17179611.848000] Bluetooth: RFCOMM socket layer initialized
[17179611.848000] Bluetooth: RFCOMM TTY layer initialized
[17179611.848000] Bluetooth: RFCOMM ver 1.7
[17179645.556000] NET: Registered protocol family 10
[17179645.556000] lo: Disabled Privacy Extensions
[17179645.556000] IPv6 over IPv4 tunneling driver

:confused:

These are the results.
Thanks again guys, its good of you to help!!! :)

Buy the way I use zen broadband for my internet.

---

### Post by noob12 on 2007-09-22
I notice you're already booting with a nonstandard kernel command line.  At what point did you add the noapic into the command line?  Had you experienced other problems that led to that?  
```

[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash noapic

```

What release and edition of Ubuntu are you running?  You're  running a pretty old kernel 2.6.15-26-386 kernel on AMD 64 and a lot of nvidia devices on the motherboard.  If this is a new installation of Ubuntu, I'd really suggest going up to Feisty and 2.6.20-16-generic (the LiveCD comes with 2.6.20-15-generic and you'll get upgraded when you pull network updates); Feisty's kernel is likely to know about many more of these devices.

If you have some reason to stay back on 2.6.15 then here are more diagnostic suggestions.

I'm not seeing the device detected, and I am seeing a lot of IRQs disabled.  Assuming you have a PCI-based ethernet card, it isn't getting in there.

You can try adding the boot flags to disable ACPI-based routing.  First try adding **pci=noacpi**  Then try adding **noacpi**  or **acpi=off** instead.  Note that **noapic** is not the same as **noacpi**.  They're both meaningful and control different things.    I don't suggest you run with acpi totally disabled except as a last resort.  It will be diagnostic to boot this way.  Boot with each of those and use **lspci -nn** to see if any network devices show up.  

Here's how to set boot flags for a single boot:

**Instructions for one-time boot flag entry**

When booting you'll normally see grub flash a menu of boot options up for a little while.  While it is up   with the default selection highlighted, press **e**, then use arrow keys to navigate to the line that starts with **kernel** and hit **e** again to edit it.  Put the flags at the end of the line, separated from each other and from prior material on that line by space or spaces.  Hit Enter to accept, then b to boot.

To confirm you got the flags entered properly, you should see them if you type
```

dmesg | grep 'Kernel command line'

```
after you boot.

The flags will only apply to that one boot.

---

### Post by raghuramos1987 on 2007-09-22
hey...a different kinda problem in my case..can u help me out here...i did everythin u had said in the previous posts...and these are the results...its  the same comp on which i'm able to browse if i'm on windows but not on feisty...

srinivasan@srinivasan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
srinivasan@srinivasan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:24:C0:01  
          inet6 addr: fe80::219:66ff:fe24:c001/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11042 (10.7 KiB)  TX bytes:14782 (14.4 KiB)
          Interrupt:19 Base address:0x8c00 

eth0:avah Link encap:Ethernet  HWaddr 00:19:66:24:C0:01  
          inet addr:169.254.4.87  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:488 (488.0 b)  TX bytes:488 (488.0 b)

srinivasan@srinivasan-desktop:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f640000 end: 000000001f740000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001f740000 size: 0000000000010000 end: 000000001f750000 type: 3
[    0.000000] copy_e820_map() start: 000000001f750000 size: 00000000000b0000 end: 000000001f800000 type: 4
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff380000 size: 0000000000c80000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f740000 (usable)
[    0.000000]  BIOS-e820: 000000001f740000 - 000000001f750000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f750000 - 000000001f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 128832) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128832
[    0.000000]   HighMem    128832 ->   128832
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128832
[    0.000000] On node 0 totalpages: 128832
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 974 pages used for memmap
[    0.000000]   Normal zone: 123762 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fa3e0
[    0.000000] ACPI: RSDT (v001 A_M_I  OEMRSDT  0x03000720 MSFT 0x00000097) @ 0x1f740000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x12000601 MSFT 0x00000097) @ 0x1f740200
[    0.000000] ACPI: MADT (v001 A_M_I  OEMAPIC  0x03000720 MSFT 0x00000097) @ 0x1f740300
[    0.000000] ACPI: OEMB (v001 A_M_I  OEMBIOS  0x03000720 MSFT 0x00000097) @ 0x1f750040
[    0.000000] ACPI: DSDT (v001  75i6G 75i6G292 0x00000292 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:df500000)
[    0.000000] Detected 2999.990 MHz processor.
[   17.984745] Built 1 zonelists.  Total pages: 127826
[   17.984750] Kernel command line: root=UUID=d5f08b5d-fecd-47d4-bd9c-6e4cb62bf450 ro quiet splash
[   17.984914] mapped APIC to ffffd000 (fee00000)
[   17.984917] mapped IOAPIC to ffffc000 (fec00000)
[   17.984920] Enabling fast FPU save and restore... done.
[   17.984923] Enabling unmasked SIMD FPU exception support... done.
[   17.984936] Initializing CPU#0
[   17.985015] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   17.986424] Console: colour VGA+ 80x25
[   17.986747] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.986992] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.995782] Memory: 499520k/515328k available (1992k kernel code, 15160k reserved, 893k data, 328k init, 0k highmem)
[   17.995793] virtual kernel memory layout:
[   17.995795]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   17.995796]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.995797]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   17.995798]     lowmem  : 0xc0000000 - 0xdf740000   ( 503 MB)
[   17.995799]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   17.995800]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   17.995801]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   17.995804] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.072929] Calibrating delay using timer specific routine.. 6003.94 BogoMIPS (lpj=12007891)
[   18.072972] Security Framework v1.0.0 initialized
[   18.072978] SELinux:  Disabled at boot.
[   18.072995] Mount-cache hash table entries: 512
[   18.073135] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e59d 00000000 00000001
[   18.073144] monitor/mwait feature present.
[   18.073145] using mwait in idle threads.
[   18.073152] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   18.073155] CPU: L2 cache: 2048K
[   18.073158] CPU: Physical Processor ID: 0
[   18.073160] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003180 0000e59d 00000000 00000001
[   18.073171] Compat vDSO mapped to ffffe000.
[   18.073175] Remapping vsyscall page to ffffe000
[   18.073191] Checking 'hlt' instruction... OK.
[   18.089007] SMP alternatives: switching to UP code
[   18.089376] Early unpacking initramfs... done
[   18.371274] ACPI: Core revision 20060707
[   18.371439] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.373477] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[   18.373503] SMP alternatives: switching to SMP code
[   18.373679] Booting processor 1/1 eip 3000
[   18.384272] Initializing CPU#1
[   18.464523] Calibrating delay using timer specific routine.. 5999.78 BogoMIPS (lpj=11999566)
[   18.464534] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e59d 00000000 00000001
[   18.464542] monitor/mwait feature present.
[   18.464549] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   18.464552] CPU: L2 cache: 2048K
[   18.464555] CPU: Physical Processor ID: 0
[   18.464557] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003180 0000e59d 00000000 00000001
[   18.465116] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 05
[   18.465161] Total of 2 processors activated (12003.72 BogoMIPS).
[   18.465292] ENABLING IO-APIC IRQs
[   18.465476] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.612377] checking TSC synchronization across 2 CPUs: passed.
[    0.003996] Brought up 2 CPUs
[    0.397252] migration_cost=167
[    0.397584] Booting paravirtualized kernel on bare hardware
[    0.397672] Time: 23:55:54  Date: 08/22/107
[    0.397706] NET: Registered protocol family 16
[    0.397810] EISA bus registered
[    0.397817] ACPI: bus type pci registered
[    0.397889] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.397891] PCI: Using configuration type 1
[    0.397893] Setting up standard PCI resources
[    0.410197] ACPI: Interpreter enabled
[    0.410201] ACPI: Using IOAPIC for interrupt routing
[    0.410750] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.410758] PCI: Probing PCI hardware (bus 00)
[    0.411064] Boot video device is 0000:00:02.0
[    0.411423] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.411427] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.411746] PCI: Transparent bridge - 0000:00:1e.0
[    0.411769] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.413674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.420629] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.420878] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.421130] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.421379] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.421627] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.421877] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.422125] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.422380] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.422530] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.422544] pnp: PnP ACPI init
[    0.426979] pnp: PnP ACPI: found 14 devices
[    0.426985] PnPBIOS: Disabled by ACPI PNP
[    0.427040] PCI: Using ACPI for IRQ routing
[    0.427043] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.429908] NET: Registered protocol family 8
[    0.429911] NET: Registered protocol family 20
[    0.430601] pnp: 00:0c: ioport range 0x290-0x29f has been reserved
[    0.430956] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.430965] PCI: Bridge: 0000:00:1e.0
[    0.430968]   IO window: b000-bfff
[    0.430974]   MEM window: ff000000-ff0fffff
[    0.430978]   PREFETCH window: disabled.
[    0.430991] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.431019] NET: Registered protocol family 2
[    0.475599] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.475689] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.475764] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.475807] TCP: Hash tables configured (established 16384 bind 8192)
[    0.475810] TCP reno registered
[    0.487652] checking if image is initramfs... it is
[    1.046001] Freeing initrd memory: 7007k freed
[    1.046759] audit: initializing netlink socket (disabled)
[    1.046779] audit(1190505354.752:1): initialized
[    1.046983] VFS: Disk quotas dquot_6.5.1
[    1.047007] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.047068] io scheduler noop registered
[    1.047071] io scheduler anticipatory registered
[    1.047073] io scheduler deadline registered
[    1.047087] io scheduler cfq registered (default)
[    1.047402] isapnp: Scanning for PnP cards...
[    1.398792] isapnp: No Plug & Play device found
[    1.427065] Real Time Clock Driver v1.12ac
[    1.427130] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.427258] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.427393] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.428041] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.428239] mice: PS/2 mouse device common for all mice
[    1.428933] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.429113] input: Macintosh mouse button emulation as /class/input/input0
[    1.429158] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.429163] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.429414] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.432233] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.432240] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.432360] EISA: Probing bus 0 at eisa.0
[    1.432399] EISA: Detected 0 cards.
[    1.462472] TCP cubic registered
[    1.462484] NET: Registered protocol family 1
[    1.462513] Starting balanced_irq
[    1.462520] Using IPI No-Shortcut mode
[    1.462615] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.462711] ACPI: (supports S0 S1 S3 S4 S5)
[    1.462770]   Magic number: 7:5:960
[    1.462784]   hash matches device ttyb1
[    1.463234] Freeing unused kernel memory: 328k freed
[    1.466477] Time: tsc clocksource has been installed.
[    2.663946] Capability LSM initialized
[    2.701666] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.701979] ACPI: Processor [CPU2] (supports 8 throttling states)
[    2.701988] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.701997] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.097951] usbcore: registered new interface driver usbfs
[    3.097991] usbcore: registered new interface driver hub
[    3.098025] usbcore: registered new device driver usb
[    3.099223] USB Universal Host Controller Interface driver v3.0
[    3.099320] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.099341] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.099349] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.099577] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.099613] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000dc00
[    3.099807] usb usb1: configuration #1 chosen from 1 choice
[    3.099860] hub 1-0:1.0: USB hub found
[    3.099871] hub 1-0:1.0: 2 ports detected
[    3.121724] 8139too Fast Ethernet driver 0.9.28
[    3.201114] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[    3.201139] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.201147] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.201185] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.201224] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e000
[    3.201357] usb usb2: configuration #1 chosen from 1 choice
[    3.201406] hub 2-0:1.0: USB hub found
[    3.201415] hub 2-0:1.0: 2 ports detected
[    3.304885] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.304905] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.304911] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.304947] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.304979] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[    3.305145] usb usb3: configuration #1 chosen from 1 choice
[    3.305190] hub 3-0:1.0: USB hub found
[    3.305200] hub 3-0:1.0: 2 ports detected
[    3.408708] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[    3.408721] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.408727] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.408759] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.408783] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e800
[    3.408915] usb usb4: configuration #1 chosen from 1 choice
[    3.408961] hub 4-0:1.0: USB hub found
[    3.408971] hub 4-0:1.0: 2 ports detected
[    3.512772] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 22 (level, low) -> IRQ 19
[    3.513129] eth0: RealTek RTL8139 at 0xe0058c00, 00:19:66:24:c0:01, IRQ 19
[    3.513133] eth0:  Identified 8139 chip type 'RTL-8101'
[    3.516934] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.526197] SCSI subsystem initialized
[    3.534188] libata version 2.20 loaded.
[    3.536211] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.536235] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    3.536264] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.536354] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fc00 irq 14
[    3.536404] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fc08 irq 15
[    3.536436] scsi0 : ata_piix
[    3.692378] scsi1 : ata_piix
[    4.012230] ata2.00: ATAPI, max UDMA/33
[    4.176053] ata2.00: configured for UDMA/33
[    4.177005] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182F SB02 PQ: 0 ANSI: 5
[    4.177183] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    4.177207] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[    4.177232] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.177278] ata3: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001cc02 bmdma 0x0001c000 irq 18
[    4.177317] ata4: SATA max UDMA/133 cmd 0x0001c800 ctl 0x0001c402 bmdma 0x0001c008 irq 18
[    4.177330] scsi2 : ata_piix
[    4.341819] ATA: abnormal status 0x7F on port 0x0001d007
[    4.341837] scsi3 : ata_piix
[    4.547174] ata4.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.547181] ata4.00: ATA-7: ST380215AS, 3.AAD, max UDMA/133
[    4.547184] ata4.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.613732] ata4.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.613737] ata4.00: configured for UDMA/133
[    4.613866] scsi 3:0:0:0: Direct-Access     ATA      ST380215AS       3.AA PQ: 0 ANSI: 5
[    4.614218] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[    4.614235] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.614241] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.614417] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.614457] ehci_hcd 0000:00:1d.7: debug port 1
[    4.614465] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    4.614477] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xff27fc00
[    4.618374] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.620727] usb usb5: configuration #1 chosen from 1 choice
[    4.620774] hub 5-0:1.0: USB hub found
[    4.620784] hub 5-0:1.0: 8 ports detected
[    4.743793] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.743803] Uniform CD-ROM driver Revision: 3.20
[    4.743890] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.745082] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.745103] sda: Write Protect is off
[    4.745109] sda: Mode Sense: 00 3a 00 00
[    4.745137] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.745217] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.745234] sda: Write Protect is off
[    4.745238] sda: Mode Sense: 00 3a 00 00
[    4.745264] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.745271]  sda:<5>sr 1:0:0:0: Attached scsi generic sg0 type 5
[    4.749810] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    4.761538]  sda1 sda2 < sda5 sda6 sda7 sda8 >
[    4.820287] sd 3:0:0:0: Attached scsi disk sda
[    5.144580] Attempting manual resume
[    5.144585] swsusp: Resume From Partition 8:8
[    5.144587] PM: Checking swsusp image.
[    5.154711] PM: Resume from disk failed.
[    5.196241] kjournald starting.  Commit interval 5 seconds
[    5.196249] EXT3-fs: mounted filesystem with ordered data mode.
[   12.046328] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   12.243613] NET: Registered protocol family 10
[   12.243759] lo: Disabled Privacy Extensions
[   13.360121] Linux agpgart interface v0.102 (c) Dave Jones
[   13.416705] agpgart: Detected an Intel 865 Chipset.
[   13.417459] agpgart: Detected 8060K stolen memory.
[   13.431231] agpgart: AGP aperture is 128M @ 0xf0000000
[   13.654599] intel_rng: FWH not detected
[   13.686652] parport: PnPBIOS parport detected.
[   13.686707] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   13.791780] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.810971] irda_init()
[   13.810986] NET: Registered protocol family 23
[   13.867902] input: PC Speaker as /class/input/input2
[   13.894229] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.905099] iTCO_vendor_support: vendor-support=0
[   13.906463] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   14.194448] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   14.194487] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   14.509523] intel8x0_measure_ac97_clock: measured 55812 usecs
[   14.509527] intel8x0: clocking to 48000
[   14.827999] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   14.830503] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   14.830550] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.000008] fuse init (API version 7.8)
[   15.019359] lp0: using parport0 (interrupt-driven).
[   15.047338] Adding 1156640k swap on /dev/disk/by-uuid/8e0ad4a7-d283-457c-83d8-125ef91f98cd.  Priority:-1 extents:1 across:1156640k
[   15.261886] EXT3 FS on sda7, internal journal
[   22.773283] eth0: no IPv6 routers present
[   27.221848] NET: Registered protocol family 17
[   30.016976] input: Power Button (FF) as /class/input/input4
[   30.017015] ACPI: Power Button (FF) [PWRF]
[   30.017109] input: Power Button (CM) as /class/input/input5
[   30.017138] ACPI: Power Button (CM) [PWRB]
[   30.081902] ibm_acpi: ec object not found
[   30.132422] Using specific hotkey driver
[   30.193547] No dock devices found.
[   30.231896] pcc_acpi: loading...
[   34.890513] [drm] Initialized drm 1.1.0 20060810
[   34.894133] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.894614] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   35.589731] ppdev: user-space parallel port driver
[   36.157818] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   36.157826] apm: disabled - APM is not SMP safe.
[   36.318026] Bluetooth: Core ver 2.11
[   36.318130] NET: Registered protocol family 31
[   36.318133] Bluetooth: HCI device and connection manager initialized
[   36.318138] Bluetooth: HCI socket layer initialized
[   36.337509] Bluetooth: L2CAP ver 2.8
[   36.337516] Bluetooth: L2CAP socket layer initialized
[   36.504177] Bluetooth: RFCOMM socket layer initialized
[   36.504204] Bluetooth: RFCOMM TTY layer initialized
[   36.504208] Bluetooth: RFCOMM ver 1.8
[  261.538024] eth0: link down
[  308.085974] eth0: link down
[  308.086770] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  357.127160] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  357.127588] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  362.411787] eth0: link down
[  364.092195] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  367.857045] eth0: no IPv6 routers present
srinivasan@srinivasan-desktop:~$

---

### Post by noob12 on 2007-09-22
Actually, raghuramos1987 you have some different problem.  Many connectivity issues might look alike superficially.  You're probably better off on your own thread.  Readers will help.

---

### Post by raghuramos1987 on 2007-09-23
k thanks...will strt a new thread then...

---

