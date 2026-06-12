---
title: "Wireless network AR5005G 802.11abg NIC"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by phpzer0 on 2006-11-28
Hi,

I have an in built card: AR5005G 802.11abg NIC
Computer: Acer travelmate 2413LMI

How to install? :confused:

Best
William

---

### Post by FrodoB on 2006-11-28
Publish the outputs of:

lspci

iwconfig

Then someone will be able to assist you.

---

### Post by phpzer0 on 2006-11-28
> **FrodoB said:**
> Publish the outputs of:

lspci

iwconfig

Then someone will be able to assist you.
Oki doki ;)

lwilliam@william:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
william@william:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by FrodoB on 2006-11-28
Which version of Ubuntu are you using and was it installed from the Alternate CD perchance?

---

### Post by phpzer0 on 2006-11-28
I use 6.10, alternate cd. ;)

---

### Post by FrodoB on 2006-11-28
1) Have the Alternate CD ready for use.

2) Open a terminal command prompt and type the following:

$ sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

---

### Post by phpzer0 on 2006-11-29
> **FrodoB said:**
> 1) Have the Alternate CD ready for use.

2) Open a terminal command prompt and type the following:

$ sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.
Thank you! It works. But how to show available wireless network?

---

### Post by FrodoB on 2006-11-29
iwlist ath0 scanning

---

### Post by phpzer0 on 2006-11-29
Thank you ;)

---

### Post by auntiem on 2006-12-03
> **FrodoB said:**
> 1) Have the Alternate CD ready for use.

2) Open a terminal command prompt and type the following:

$ sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

I'm afraid I'm having the same problem, and though I tried to follow the same steps, it doesn't quite work.

These are my outputs:
alain@alain-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter
alain@alain-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ppp0      no wireless extensions.

*$ sudo apt-get install linux-restricted-modules-'uname -r'* gave me: Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-uname -r

I have AR5005G 802.11abc NIC as well.

Any kind of help would be great-- I'm really excited about Ubuntu, but it doesn't really serve any purpose if I can't get my wireless to work.  And unfortunately, I don't think I'm in a position to go back to Windows.

---

### Post by FrodoB on 2006-12-03
The single quotes are the backwards ones that are on the same key as ~ on a US keyboard, the key just below the Esc key.

At least that is what your issue looks like. Thanks for pasting the results.

Give it a try.

---

### Post by auntiem on 2006-12-03
> **FrodoB said:**
> The single quotes are the backwards ones that are on the same key as ~ on a US keyboard, the key just below the Esc key.

At least that is what your issue looks like. Thanks for pasting the results.

Give it a try.

That solved, one issue. ;) 
However it gave me this as a result:
[I]alain@alain-laptop:~$ sudo apt-get install linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/I]

I rebooted the system, regardless-- but I still don't have my wireless showing up in *Networking*.

---

### Post by FrodoB on 2006-12-03
Which version of Ubuntu are you using? 

6.06 or 6.10?

---

### Post by FrodoB on 2006-12-03
Also publish the output of dmesg, this should show us what is loading when it tries to bring the Atheros module up.

---

### Post by auntiem on 2006-12-03
> **FrodoB said:**
> Also publish the output of dmesg, this should show us what is loading when it tries to bring the Atheros module up.

Thanks in advance for all your help-- I really appreciate it.

I'm running 6.10-- I got the CD off of the site.

The output is as such:

alain@alain-laptop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000bdf0000 (usable)
[17179569.184000]  BIOS-e820: 000000000bdf0000 - 000000000bdfa000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000bdfa000 - 000000000be00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000be00000 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 189MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f8180
[17179569.184000] On node 0 totalpages: 48624
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 44528 pages, LIFO batch:7
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f8150
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0bdf64c2
[17179569.184000] ACPI: FADT (v001 SiS    661MX    0x06040000 PTL  0x00000001) @ 0x0bdf9f46
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x0bdf9fba
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x0bdf64f2
[17179569.184000] ACPI: DSDT (v001 PTLTD     661MX 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: IRQ11 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 1400.261 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.340000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.340000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.344000] Memory: 182888k/194496k available (1910k kernel code, 11084k reserved, 1070k data, 308k init, 0k highmem)
[17179573.344000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.424000] Calibrating delay using timer specific routine.. 2802.37 BogoMIPS (lpj=5604758)
[17179573.424000] Security Framework v1.0.0 initialized
[17179573.424000] SELinux:  Disabled at boot.
[17179573.424000] Mount-cache hash table entries: 512
[17179573.424000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179573.424000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179573.424000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179573.424000] CPU: L2 cache: 1024K
[17179573.424000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000000 00000000 00000000
[17179573.424000] Checking 'hlt' instruction... OK.
[17179573.440000] SMP alternatives: switching to UP code
[17179573.440000] Freeing SMP alternatives: 16k freed
[17179573.440000] checking if image is initramfs... it is
[17179574.144000] Freeing initrd memory: 5564k freed
[17179574.144000] ACPI: Core revision 20060707
[17179574.148000] ACPI: Looking for DSDT ... not found!
[17179574.152000] CPU0: Intel(R) Celeron(R) M processor         1.40GHz stepping 08
[17179574.152000] Total of 1 processors activated (2802.37 BogoMIPS).
[17179574.152000] ENABLING IO-APIC IRQs
[17179574.152000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179574.296000] Brought up 1 CPUs
[17179574.296000] migration_cost=0
[17179574.296000] NET: Registered protocol family 16
[17179574.296000] EISA bus registered
[17179574.296000] ACPI: bus type pci registered
[17179574.296000] PCI: PCI BIOS revision 2.10 entry at 0xfd786, last bus=1
[17179574.296000] PCI: Using configuration type 1
[17179574.296000] Setting up standard PCI resources
[17179574.328000] ACPI: Interpreter enabled
[17179574.328000] ACPI: Using IOAPIC for interrupt routing
[17179574.328000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.328000] PCI: Probing PCI hardware (bus 00)
[17179574.332000] Uncovering SIS963 that hid as a SIS503 (compatible=0)
[17179574.332000] Enabling SiS 96x SMBus.
[17179574.332000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179574.332000] Boot video device is 0000:01:00.0
[17179574.332000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.340000] ACPI: Embedded Controller [EC0] (gpe 25) interrupt mode.
[17179574.352000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
[17179574.352000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11)
[17179574.352000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[17179574.352000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11)
[17179574.352000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[17179574.352000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[17179574.352000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[17179574.352000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
[17179574.352000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.352000] pnp: PnP ACPI init
[17179574.356000] pnp: PnP ACPI: found 9 devices
[17179574.356000] PnPBIOS: Disabled by ACPI PNP
[17179574.356000] PCI: Using ACPI for IRQ routing
[17179574.356000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.360000] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
[17179574.360000] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
[17179574.360000] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
[17179574.360000] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
[17179574.360000] pnp: 00:04: ioport range 0xfe00-0xfe00 has been reserved
[17179574.360000] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[17179574.360000] PCI: Bridge: 0000:00:01.0
[17179574.360000]   IO window: 9000-9fff
[17179574.360000]   MEM window: e2100000-e21fffff
[17179574.360000]   PREFETCH window: e8000000-efffffff
[17179574.360000] PCI: Bus 2, cardbus bridge: 0000:00:06.0
[17179574.360000]   IO window: 00002400-000024ff
[17179574.360000]   IO window: 00002800-000028ff
[17179574.360000]   PREFETCH window: 20000000-21ffffff
[17179574.360000]   MEM window: 22000000-23ffffff
[17179574.360000] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
[17179574.360000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179574.360000] NET: Registered protocol family 2
[17179574.396000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179574.396000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179574.396000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179574.396000] TCP: Hash tables configured (established 8192 bind 4096)
[17179574.396000] TCP reno registered
[17179574.396000] audit: initializing netlink socket (disabled)
[17179574.396000] audit(1165198840.396:1): initialized
[17179574.396000] VFS: Disk quotas dquot_6.5.1
[17179574.396000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.396000] Initializing Cryptographic API
[17179574.396000] io scheduler noop registered
[17179574.396000] io scheduler anticipatory registered
[17179574.396000] io scheduler deadline registered
[17179574.396000] io scheduler cfq registered (default)
[17179574.396000] isapnp: Scanning for PnP cards...
[17179574.760000] isapnp: No Plug & Play device found
[17179574.792000] Real Time Clock Driver v1.12ac
[17179574.792000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.792000] PCI: Enabling device 0000:00:02.6 (0000 -> 0001)
[17179574.796000] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 185
[17179574.796000] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[17179574.796000] mice: PS/2 mouse device common for all mice
[17179574.796000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.796000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.796000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.796000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.860000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.868000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.896000] EISA: Probing bus 0 at eisa.0
[17179574.896000] Cannot allocate resource for EISA slot 1
[17179574.896000] Cannot allocate resource for EISA slot 2
[17179574.896000] Cannot allocate resource for EISA slot 8
[17179574.896000] EISA: Detected 0 cards.
[17179574.900000] TCP bic registered
[17179574.900000] NET: Registered protocol family 1
[17179574.900000] NET: Registered protocol family 8
[17179574.900000] NET: Registered protocol family 20
[17179574.900000] Using IPI No-Shortcut mode
[17179574.900000] ACPI: (supports S0 S3 S4 S5)
[17179574.900000] Freeing unused kernel memory: 308k freed
[17179574.968000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179576.100000] Capability LSM initialized
[17179576.136000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179576.136000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179576.136000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179576.136000] ACPI: Getting cpuindex for acpiid 0x1
[17179576.136000] ACPI: Thermal Zone [THRM] (40 C)
[17179576.472000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179576.472000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 193
[17179576.472000] SIS5513: chipset revision 0
[17179576.472000] SIS5513: not 100% native mode: will probe irqs later
[17179576.472000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179576.472000]     ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:DMA, hdb:pio
[17179576.472000]     ide1: BM-DMA at 0x1008-0x100f, BIOS settings: hdc:DMA, hdd:pio
[17179576.472000] Probing IDE interface ide0...
[17179576.764000] hda: SAMSUNG MP0402H, ATA DISK drive
[17179577.436000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.528000] Probing IDE interface ide1...
[17179578.264000] hdc: UJDA770 DVD/CDRW, ATAPI CD/DVD-ROM drive
[17179578.600000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.604000] hda: max request size: 512KiB
[17179578.612000] hda: 78242976 sectors (40060 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179578.616000] hda: cache flushes supported
[17179578.616000]  hda: hda1 hda2 < hda5 >
[17179578.740000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.740000] Uniform CD-ROM driver Revision: 3.20
[17179579.984000] usbcore: registered new driver usbfs
[17179579.984000] usbcore: registered new driver hub
[17179579.988000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179579.988000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 201
[17179579.988000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179579.988000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179580.208000] ohci_hcd 0000:00:03.0: irq 201, io mem 0xe2000000
[17179580.264000] usb usb1: configuration #1 chosen from 1 choice
[17179580.264000] hub 1-0:1.0: USB hub found
[17179580.264000] hub 1-0:1.0: 3 ports detected
[17179580.368000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 209
[17179580.368000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179580.368000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179580.588000] ohci_hcd 0000:00:03.1: irq 209, io mem 0xe2001000
[17179580.644000] usb usb2: configuration #1 chosen from 1 choice
[17179580.644000] hub 2-0:1.0: USB hub found
[17179580.644000] hub 2-0:1.0: 3 ports detected
[17179580.748000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 217
[17179580.748000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179580.748000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[17179580.748000] ehci_hcd 0000:00:03.3: irq 217, io mem 0xe2002000
[17179580.748000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.748000] usb usb3: configuration #1 chosen from 1 choice
[17179580.748000] hub 3-0:1.0: USB hub found
[17179580.748000] hub 3-0:1.0: 6 ports detected
[17179580.892000] Attempting manual resume
[17179580.992000] kjournald starting.  Commit interval 5 seconds
[17179580.992000] EXT3-fs: mounted filesystem with ordered data mode.
[17179592.648000] ath_hal: module license 'Proprietary' taints kernel.
[17179592.648000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179592.720000] wlan: 0.8.4.2 (0.9.2)
[17179592.788000] ath_rate_sample: 1.2 (0.9.2)
[17179592.852000] ath_pci: 0.9.4.5 (0.9.2)
[17179592.852000] PCI: Enabling device 0000:00:0b.0 (0010 -> 0012)
[17179592.852000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 225
[17179592.852000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[17179592.852000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
[17179593.024000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179593.024000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0082]
[17179593.024000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179593.024000] Yenta: Routing CardBus interrupts to PCI
[17179593.024000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
[17179593.256000] Yenta: ISA IRQ mask 0x06f8, PCI irq 177
[17179593.256000] Socket status: 30000006
[17179593.268000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.324000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.360000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.360000] agpgart: Detected SiS 661 chipset
[17179593.364000] agpgart: AGP aperture is 32M @ 0xe0000000
[17179593.372000] input: PC Speaker as /class/input/input1
[17179593.408000] sis900.c: v1.08.09 Sep. 19 2005
[17179593.408000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179593.412000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[17179593.420000] 0000:00:04.0: Using transceiver found at address 13 as default
[17179593.420000] eth0: SiS 900 PCI Fast Ethernet at 0x2000, IRQ 177, 00:c0:9f:c4:74:9d.
[17179593.644000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[17179593.684000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179593.876000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 185
[17179594.040000] ts: Compaq touchscreen protocol output
[17179594.108000] eth0: Media Link Off
[17179594.408000] cs: IO port probe 0x100-0x3af: clean.
[17179594.408000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[17179594.412000] cs: IO port probe 0x820-0x8ff: clean.
[17179594.412000] cs: IO port probe 0xc00-0xcf7: clean.
[17179594.412000] cs: IO port probe 0xa00-0xaff: clean.
[17179594.696000] intel8x0_measure_ac97_clock: measured 55382 usecs
[17179594.696000] intel8x0: clocking to 48000
[17179594.696000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[17179594.872000] lp: driver loaded but no devices found
[17179594.896000] Adding 546168k swap on /dev/disk/by-uuid/97362728-638f-4400-b955-e2fe64170d86.  Priority:-1 extents:1 across:546168k
[17179594.936000] EXT3 FS on hda1, internal journal
[17179595.188000] NET: Registered protocol family 17
[17179601.448000] CSLIP: code copyright 1989 Regents of the University of California
[17179601.456000] PPP generic driver version 2.4.2
[17179601.504000] NET: Registered protocol family 10
[17179601.504000] lo: Disabled Privacy Extensions
[17179601.504000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179601.504000] IPv6 over IPv4 tunneling driver
[17179602.360000] ACPI: AC Adapter [ACAD] (on-line)
[17179602.416000] ACPI: Battery Slot [BAT1] (battery present)
[17179602.436000] ACPI: Power Button (FF) [PWRF]
[17179602.436000] ACPI: Lid Switch [LID]
[17179602.436000] ACPI: Power Button (CM) [PWRB]
[17179602.436000] ACPI: Sleep Button (CM) [SLPB]
[17179602.572000] ibm_acpi: ec object not found
[17179602.608000] pcc_acpi: loading...
[17179605.416000] apm: BIOS not found.
[17179610.188000] Bluetooth: Core ver 2.8
[17179610.188000] NET: Registered protocol family 31
[17179610.188000] Bluetooth: HCI device and connection manager initialized
[17179610.188000] Bluetooth: HCI socket layer initialized
[17179610.244000] Bluetooth: L2CAP ver 2.8
[17179610.244000] Bluetooth: L2CAP socket layer initialized
[17179610.316000] Bluetooth: RFCOMM socket layer initialized
[17179610.316000] Bluetooth: RFCOMM TTY layer initialized
[17179610.316000] Bluetooth: RFCOMM ver 1.7
[17179619.004000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179619.200000] ISO 9660 Extensions: RRIP_1991A
[17179655.108000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17179660.108000] eth0: Media Link On 10mbps half-duplex 
[17179665.344000] eth0: no IPv6 routers present
[17179666.780000] NET: Registered protocol family 24
[17179668.092000] ip_tables: (C) 2000-2006 Netfilter Core Team
[17179673.744000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179673.788000] ISO 9660 Extensions: RRIP_1991A

---

### Post by FrodoB on 2006-12-03
Here is the problem, the question is why?

[17179592.648000] ath_hal: module license 'Proprietary' taints kernel.
[17179592.648000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179592.720000] wlan: 0.8.4.2 (0.9.2)
[17179592.788000] ath_rate_sample: 1.2 (0.9.2)
[17179592.852000] ath_pci: 0.9.4.5 (0.9.2)
[17179592.852000] PCI: Enabling device 0000:00:0b.0 (0010 -> 0012)
[17179592.852000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 225
[17179592.852000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[17179592.852000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
[17179593.024000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 177

If you are on Edgy could you try Dapper Drake? I might not work either,  but this seems unlikely, why is this hardware revision not supported? It likely will be at some point in the future. 

It may be now if you look into this on the mAdWiFi site hardware compatibility list.

---

### Post by FrodoB on 2006-12-03
phpzer0;

Could you please publish your dmesg output so we can compare it to this card that is not recognized by the kernel?

Thanks.
[]("http://ubuntuforums.org/member.php?u=200357")

---

### Post by FrodoB on 2006-12-04
OK, our bug is listed on the mAdWiFi site:

[http://madwifi.org/wiki/Compatibility#AtherosAR5005G](http://madwifi.org/wiki/Compatibility#AtherosAR5005G)

Strange this is that I have been working with this thread and it is working, which kind of validates what the madwifi site says:

[http://ubuntuforums.org/showthread.php?t=309333](http://ubuntuforums.org/showthread.php?t=309333)

Also see this site, which the madwifi entry leads to that recommends running a script:

[http://rik.rikva.nl/?q=node/10](http://rik.rikva.nl/?q=node/10)

I don't know if this will help or not, but it is worth a try.

---

### Post by FrodoB on 2006-12-04
I have never had to do this for an Atheros based card, but you could try ndiswrapper if Dapper does not work. Here is the write-up from the ndiswrapper site:

Laptop: Acer Travelmate 2414LMi [LIST]
[*]Chipset: Atheros ar5211, labelled as AR5005G
[*]Driver: Foxconn driver [ftp://ftp.support.acer-euro.com/notebook/travelmate_2410/driver/Wireless%20Lan%2080211bg.zip](ftp://ftp.support.acer-euro.com/notebook/travelmate_2410/driver/Wireless%20Lan%2080211bg.zip)
[*]
[*]Other: Use unshield to extract the group Diskette_Files and use net5211.inf from there, not Driver_Files_NDIS5.
[*]Other: Running on SuSE 10.1, kernel 2.6.16.21-0.13-default, ndiswrapper 1.10-19.[/LIST]

---

### Post by FrodoB on 2006-12-04
Yes, I see others on the web are using ndiswrapper when their atheros card is not supported in the HAL yet.

---

### Post by auntiem on 2006-12-05
> **FrodoB said:**
> OK, our bug is listed on the mAdWiFi site:

[http://madwifi.org/wiki/Compatibility#AtherosAR5005G](http://madwifi.org/wiki/Compatibility#AtherosAR5005G)

Strange this is that I have been working with this thread and it is working, which kind of validates what the madwifi site says:

[http://ubuntuforums.org/showthread.php?t=309333](http://ubuntuforums.org/showthread.php?t=309333)

Also see this site, which the madwifi entry leads to that recommends running a script:

[http://rik.rikva.nl/?q=node/10](http://rik.rikva.nl/?q=node/10)

I don't know if this will help or not, but it is worth a try.

Yes, I saw that script on madwifi-- but didn't know exactly how to go about it.   I guess a little more research is in order.  

As far as the ndiswrapper on Dapper? or Edgy?

---

### Post by FrodoB on 2006-12-05
I would install the latest version from the ndiswrapper site. It is up to at least 1.30 at the moment. I don' t think it matters which version of Ubuntu if you use the latest ndiswrapper.

---

### Post by auntiem on 2006-12-05
> **FrodoB said:**
> I would install the latest version from the ndiswrapper site. It is up to at least 1.30 at the moment. I don' t think it matters which version of Ubuntu if you use the latest ndiswrapper.

Okay.  We're getting somewhere.  I've used ndiswrapper with *i think* the correct driver (I don't have the CD, and therefore had to get it off the net).

I've checked my *Networking*, and my wireless card shows up.

However, I can't seem to connect to my home network.

alain@alain-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:100/100  Signal level:-94 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ppp0      no wireless extensions.

---

### Post by FrodoB on 2006-12-05
Publish what you have in /etc/network/interfaces

---

### Post by FrodoB on 2006-12-05
You should have a record like this:

iface wlan0 inet dhcp
wireless-essid My_Essid
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
auto wlan0


The 23 Xs are a 128bit WEP key.

---

### Post by auntiem on 2006-12-05
> **FrodoB said:**
> Publish what you have in /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid dlink
wireless-key s:


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

---

### Post by FrodoB on 2006-12-05
Assuming that you WEP is correct. Have you tried to control the device:

sudo iwlist wlan0 scanning

sudo ifdown wlan0

sudo ifup wlan0

---

### Post by auntiem on 2006-12-05
> **FrodoB said:**
> Assuming that you WEP is correct. Have you tried to control the device:

sudo iwlist wlan0 scanning

sudo ifdown wlan0

sudo ifup wlan0

alain@alain-ubuntu:~$ iwlist wlan0 scanning
wlan0     No scan results
alain@alain-ubuntu:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6576
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:a4:26:03:53
Sending on   LPF/wlan0/00:14:a4:26:03:53
Sending on   Socket/fallback
alain@alain-ubuntu:~$ sudo ifup wlan0
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "s:".
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:a4:26:03:53
Sending on   LPF/wlan0/00:14:a4:26:03:53
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by FrodoB on 2006-12-05
Did you use the ndis driver file that was recommended in post 19 of this thread, if not remove the current one and install the foxconn driver in the link.

---

### Post by phpzer0 on 2006-12-28
> **FrodoB said:**
> phpzer0;

Could you please publish your dmesg output so we can compare it to this card that is not recognized by the kernel?

Thanks.
[]("http://ubuntuforums.org/member.php?u=200357")

Yep:


[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000f6e0000 (usable)
[17179569.184000]  BIOS-e820: 000000000f6e0000 - 000000000f6ea000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000f6ea000 - 000000000f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000f700000 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 246MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 63200
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 59104 pages, LIFO batch:15
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7a10
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0f6e5e2d
[17179569.184000] ACPI: FADT (v002 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x0f6e9e78
[17179569.184000] ACPI: MADT (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x0f6e9efc
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0f6e9fd8
[17179569.184000] ACPI: MCFG (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x0f6e9f9c
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x0f6e6064
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x0f6e5e69
[17179569.184000] ACPI: DSDT (v001 INTEL  ALVISO   0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:d0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 1496.665 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.496000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.496000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.504000] Memory: 240872k/252800k available (1910k kernel code, 11288k reserved, 1069k data, 308k init, 0k highmem)
[17179572.504000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.584000] Calibrating delay using timer specific routine.. 2997.71 BogoMIPS (lpj=5995433)
[17179572.584000] Security Framework v1.0.0 initialized
[17179572.584000] SELinux:  Disabled at boot.
[17179572.584000] Mount-cache hash table entries: 512
[17179572.584000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179572.584000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179572.584000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.584000] CPU: L2 cache: 1024K
[17179572.584000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000000 00000000 00000000
[17179572.584000] Checking 'hlt' instruction... OK.
[17179572.600000] SMP alternatives: switching to UP code
[17179572.600000] Freeing SMP alternatives: 16k freed
[17179572.600000] checking if image is initramfs... it is
[17179573.192000] Freeing initrd memory: 5321k freed
[17179573.192000] ACPI: Core revision 20060707
[17179573.192000] ACPI: Looking for DSDT ... not found!
[17179573.196000] ACPI: System reset via FADT Reset Register is supported
[17179573.196000] machine_reset = acpi_machine_reset
[17179573.196000] CPU0: Intel(R) Celeron(R) M processor         1.50GHz stepping 08
[17179573.196000] Total of 1 processors activated (2997.71 BogoMIPS).
[17179573.196000] ENABLING IO-APIC IRQs
[17179573.196000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.340000] Brought up 1 CPUs
[17179573.340000] migration_cost=0
[17179573.340000] NET: Registered protocol family 16
[17179573.340000] EISA bus registered
[17179573.340000] ACPI: bus type pci registered
[17179573.340000] PCI: Using MMCONFIG
[17179573.340000] Setting up standard PCI resources
[17179573.348000] ACPI: Interpreter enabled
[17179573.348000] ACPI: Using IOAPIC for interrupt routing
[17179573.352000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.352000] PCI: Probing PCI hardware (bus 00)
[17179573.352000] Boot video device is 0000:00:02.0
[17179573.352000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179573.352000] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[17179573.352000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.352000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.352000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#06) (try 'pci=assign-busses')
[17179573.352000] Please report the result to linux-kernel to fix this permanently
[17179573.356000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.360000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179573.360000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10 11)
[17179573.360000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[17179573.360000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[17179573.360000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
[17179573.360000] ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)
[17179573.360000] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[17179573.360000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179573.364000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[17179573.364000] ACPI: Embedded Controller [EC0] (gpe 23) interrupt mode.
[17179573.400000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.400000] pnp: PnP ACPI init
[17179573.404000] pnp: PnP ACPI: found 8 devices
[17179573.404000] PnPBIOS: Disabled by ACPI PNP
[17179573.404000] PCI: Using ACPI for IRQ routing
[17179573.404000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.404000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179573.404000] PCI: Bus 7, cardbus bridge: 0000:06:09.0
[17179573.404000]   IO window: 00003400-000034ff
[17179573.404000]   IO window: 00003800-000038ff
[17179573.404000]   PREFETCH window: 20000000-21ffffff
[17179573.404000]   MEM window: 24000000-25ffffff
[17179573.404000] PCI: Bridge: 0000:00:1e.0
[17179573.404000]   IO window: 3000-3fff
[17179573.404000]   MEM window: b0100000-b01fffff
[17179573.404000]   PREFETCH window: 20000000-21ffffff
[17179573.404000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.404000] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 22 (level, low) -> IRQ 169
[17179573.404000] NET: Registered protocol family 2
[17179573.440000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179573.440000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.440000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179573.440000] TCP: Hash tables configured (established 8192 bind 4096)
[17179573.440000] TCP reno registered
[17179573.440000] Simple Boot Flag at 0x37 set to 0x1
[17179573.440000] audit: initializing netlink socket (disabled)
[17179573.440000] audit(1167333607.440:1): initialized
[17179573.440000] VFS: Disk quotas dquot_6.5.1
[17179573.440000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.440000] Initializing Cryptographic API
[17179573.440000] io scheduler noop registered
[17179573.440000] io scheduler anticipatory registered
[17179573.440000] io scheduler deadline registered
[17179573.440000] io scheduler cfq registered (default)
[17179573.440000] isapnp: Scanning for PnP cards...
[17179573.796000] isapnp: No Plug & Play device found
[17179573.824000] Real Time Clock Driver v1.12ac
[17179573.824000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.824000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 21 (level, low) -> IRQ 177
[17179573.824000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[17179573.824000] mice: PS/2 mouse device common for all mice
[17179573.824000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.824000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.824000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.824000] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.824000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179573.824000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179573.828000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179573.828000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179573.828000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179573.828000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.828000] EISA: Probing bus 0 at eisa.0
[17179573.828000] Cannot allocate resource for EISA slot 1
[17179573.828000] Cannot allocate resource for EISA slot 2
[17179573.828000] Cannot allocate resource for EISA slot 3
[17179573.828000] EISA: Detected 0 cards.
[17179573.828000] TCP bic registered
[17179573.828000] NET: Registered protocol family 1
[17179573.828000] NET: Registered protocol family 8
[17179573.828000] NET: Registered protocol family 20
[17179573.828000] Using IPI No-Shortcut mode
[17179573.828000] ACPI: (supports S0 S3 S4 S5)
[17179573.828000] Freeing unused kernel memory: 308k freed
[17179574.444000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.008000] Capability LSM initialized
[17179575.040000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179575.040000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.040000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179575.040000] ACPI: Getting cpuindex for acpiid 0x1
[17179575.108000] ACPI: Thermal Zone [TZS0] (30 C)
[17179575.136000] ACPI: Thermal Zone [TZS1] (30 C)
[17179575.444000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179575.444000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 185
[17179575.444000] ICH6: chipset revision 3
[17179575.444000] ICH6: not 100% native mode: will probe irqs later
[17179575.444000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:DMA
[17179575.444000] Probing IDE interface ide0...
[17179575.732000] hda: ST960812A, ATA DISK drive
[17179576.516000] hdb: PHILIPS DVD+/-RW SDVD8441, ATAPI CD/DVD-ROM drive
[17179576.572000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.580000] hda: max request size: 512KiB
[17179576.588000] hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.588000] hda: cache flushes supported
[17179576.588000]  hda: hda1 hda2 < hda5 hda6 > hda3
[17179576.652000] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.652000] Uniform CD-ROM driver Revision: 3.20
[17179578.260000] Probing IDE interface ide1...
[17179578.284000] usbcore: registered new driver usbfs
[17179578.284000] usbcore: registered new driver hub
[17179578.284000] USB Universal Host Controller Interface driver v3.0
[17179578.288000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 193
[17179578.288000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179578.288000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179578.288000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179578.288000] uhci_hcd 0000:00:1d.0: irq 193, io base 0x00001820
[17179578.288000] usb usb1: configuration #1 chosen from 1 choice
[17179578.288000] hub 1-0:1.0: USB hub found
[17179578.288000] hub 1-0:1.0: 2 ports detected
[17179578.392000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 201
[17179578.392000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179578.392000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179578.392000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179578.392000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x00001840
[17179578.392000] usb usb2: configuration #1 chosen from 1 choice
[17179578.392000] hub 2-0:1.0: USB hub found
[17179578.392000] hub 2-0:1.0: 2 ports detected
[17179578.496000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[17179578.496000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179578.496000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179578.496000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179578.496000] uhci_hcd 0000:00:1d.2: irq 209, io base 0x00001860
[17179578.496000] usb usb3: configuration #1 chosen from 1 choice
[17179578.496000] hub 3-0:1.0: USB hub found
[17179578.496000] hub 3-0:1.0: 2 ports detected
[17179578.600000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 217
[17179578.600000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179578.600000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179578.600000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179578.600000] uhci_hcd 0000:00:1d.3: irq 217, io base 0x00001880
[17179578.600000] usb usb4: configuration #1 chosen from 1 choice
[17179578.600000] hub 4-0:1.0: USB hub found
[17179578.600000] hub 4-0:1.0: 2 ports detected
[17179578.632000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179578.704000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 193
[17179578.704000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179578.704000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179578.704000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179578.704000] ehci_hcd 0000:00:1d.7: debug port 1
[17179578.704000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179578.704000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xb0040000
[17179578.708000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.708000] usb usb5: configuration #1 chosen from 1 choice
[17179578.708000] hub 5-0:1.0: USB hub found
[17179578.708000] hub 5-0:1.0: 8 ports detected
[17179578.864000] Attempting manual resume
[17179578.884000] kjournald starting.  Commit interval 5 seconds
[17179578.884000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.156000] usb 1-1: device not accepting address 2, error -71
[17179579.640000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[17179579.812000] usb 1-1: configuration #1 chosen from 1 choice
[17179590.252000] hw_random hardware driver 1.0.0 loaded
[17179590.496000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.664000] agpgart: Detected an Intel 915GM Chipset.
[17179590.664000] agpgart: Detected 7932K stolen memory.
[17179590.684000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179590.952000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[17179590.984000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179590.984000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179591.248000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 21 (level, low) -> IRQ 177
[17179591.248000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[17179591.256000] ts: Compaq touchscreen protocol output
[17179591.328000] 8139too Fast Ethernet driver 0.9.27
[17179591.364000] usbcore: registered new driver hiddev
[17179591.428000] input: CHESEN USB MOUSE as /class/input/input2
[17179591.428000] input: USB HID v1.10 Mouse [CHESEN USB MOUSE] on usb-0000:00:1d.0-1
[17179591.428000] usbcore: registered new driver usbhid
[17179591.428000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179592.068000] intel8x0_measure_ac97_clock: measured 55388 usecs
[17179592.068000] intel8x0: clocking to 48000
[17179592.068000] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 22 (level, low) -> IRQ 169
[17179592.068000] Yenta: CardBus bridge found at 0000:06:09.0 [1025:006a]
[17179592.068000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179592.068000] Yenta: Routing CardBus interrupts to PCI
[17179592.068000] Yenta TI: socket 0000:06:09.0, mfunc 0x00001022, devctl 0x44
[17179592.300000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 169
[17179592.300000] Socket status: 30000006
[17179592.300000] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[17179592.300000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179592.300000] cs: IO port probe 0x3000-0x3fff: clean.
[17179592.300000] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[17179592.300000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x21ffffff
[17179592.304000] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 225
[17179592.304000] eth0: RealTek RTL8139 at 0xd014a000, 00:0a:e4:ee:79:3a, IRQ 225
[17179592.304000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179592.316000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179592.432000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179592.648000] cs: IO port probe 0x100-0x3af: clean.
[17179592.648000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179592.648000] cs: IO port probe 0x820-0x8ff: clean.
[17179592.648000] cs: IO port probe 0xc00-0xcf7: clean.
[17179592.652000] cs: IO port probe 0xa00-0xaff: clean.
[17179592.820000] lp: driver loaded but no devices found
[17179592.844000] Adding 722884k swap on /dev/disk/by-uuid/65dc76cc-4912-4f05-b445-11f5922d3ca8.  Priority:-1 extents:1 across:722884k
[17179592.904000] EXT3 FS on hda3, internal journal
[17179593.508000] NET: Registered protocol family 17
[17179594.100000] ACPI: AC Adapter [ADP1] (on-line)
[17179594.376000] ACPI: Battery Slot [BAT0] (battery present)
[17179594.392000] ACPI: Power Button (FF) [PWRF]
[17179594.392000] ACPI: Lid Switch [LID0]
[17179594.392000] ACPI: Sleep Button (CM) [SLPB]
[17179594.540000] ibm_acpi: ec object not found
[17179594.568000] pcc_acpi: loading...
[17179594.672000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[17179597.092000] [drm] Initialized drm 1.0.1 20051102
[17179597.096000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179597.096000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179597.156000] NET: Registered protocol family 10
[17179597.156000] lo: Disabled Privacy Extensions
[17179597.156000] IPv6 over IPv4 tunneling driver
[17179598.580000] apm: BIOS not found.
[17179603.656000] Bluetooth: Core ver 2.8
[17179603.656000] NET: Registered protocol family 31
[17179603.656000] Bluetooth: HCI device and connection manager initialized
[17179603.656000] Bluetooth: HCI socket layer initialized
[17179603.668000] Bluetooth: L2CAP ver 2.8
[17179603.668000] Bluetooth: L2CAP socket layer initialized
[17179603.700000] Bluetooth: RFCOMM socket layer initialized
[17179603.700000] Bluetooth: RFCOMM TTY layer initialized
[17179603.700000] Bluetooth: RFCOMM ver 1.7
[17179607.520000] eth0: no IPv6 routers present
[17179616.028000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179616.892000] ISOFS: changing to secondary root
[17179620.288000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[17188041.428000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17188041.760000] ISO 9660 Extensions: RRIP_1991A
[17188104.504000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188104.504000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188104.812000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188104.812000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188104.864000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188104.864000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188104.916000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188104.916000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188104.968000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188104.968000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.020000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.020000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.072000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.072000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.124000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.124000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.180000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.180000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.232000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.232000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.284000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.284000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.336000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.336000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.388000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.388000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.444000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.444000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.496000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.496000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.548000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.548000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.600000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.600000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.652000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.652000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.704000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.704000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.756000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.756000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.808000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.808000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.860000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.860000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.916000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.916000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188105.968000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188105.968000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188106.020000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188106.020000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188106.072000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188106.072000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188106.124000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188106.124000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188106.176000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[17188106.176000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[17188106.188000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[17188106.188000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

---

### Post by FrodoB on 2006-12-28
Try modprobing the ndiswrapper and then check iwconfig to see if it exists then:
 
sudo modprobe ndiswrapper
 
If this works then add ndiswrapper to /etc/modules and it should be there when you reboot:
sudo gedit /etc/modules 
Add the word **ndiswrapper** and save the file using "save as" this will then load everytime you boot

---

### Post by phpzer0 on 2006-12-31
I have 6.10 edgy eft now, can i still use the code you posted in this thread? :)

---

### Post by Unreadedpost.com on 2006-12-31
I have EXACTLY the same problem!

It works perfect in KDE, but not with XGL/Beryl.

I folowed this guide for XGL:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl) (Method B)
[www.unreadedpost.com](www.unreadedpost.com)

---

### Post by thedshow on 2008-03-30
hey im having a hugeeee problem with my wireless.  This ubuntu is the real deal holyfield.  I have version 7.10  

My LSPCI reads


00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
01:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
01:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
01:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
01:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)



my iwconfig reads

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


IF ANYONE COULD HELP ME, I WOULD OWE YOU BIG TIME....thanks
-dylan

---

