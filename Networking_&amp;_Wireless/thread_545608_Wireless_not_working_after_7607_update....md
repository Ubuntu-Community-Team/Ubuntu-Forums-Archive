---
title: "Wireless not working after 7/6/07 update...?"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by siazikk on 2007-09-07
Hello!  This is my first posting!

I'm running Dapper 6.06 and installed an automatic update yesterday (Thursday 9/6/07).  Since then my wireless connection doesn't work. 
Did anyone else have this problem?
Is there a way I can roll back to how my system was the day before?
Thanks in advance for any help!!

~Katrina

siazikk@Peace:~$ sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:9b:f0:1c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sis900 driverversion=v1.08.09 Sep. 19 2005 duplex=full ip=192.168.0.3 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:e2003000-e2003fff irq:177
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: b
       bus info: pci@00:0b.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:e2010000-e201ffff irq:225


siazikk@Peace:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:9B:F0:1C
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe9b:f01c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4673 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4549642 (4.3 MiB)  TX bytes:612124 (597.7 KiB)
          Interrupt:177 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

siazikk@Peace:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

hmmmm....
??

---

### Post by noob12 on 2007-09-07
This indicates that no device driver has claimed the device.
> 
*-network:1 UNCLAIMED
description: Ethernet controller
product: Atheros Communications, Inc.
vendor: Atheros Communications, Inc.
physical id: b
bus info: pci@00:0b.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: cap_list
resources: iomemory:e2010000-e201ffff irq:225


Check what you upgraded (and show us too):
```
grep 2007-09-07 /var/log/dpkg.log
```

In the case that you upgraded the kernel, and you had installed drivers for your wireless yourself in the prior kernel, you may need to repeat the procedure to install the drivers.  If you upgraded the kernel, the prior kernel should have been kept around in the grub boot menu list and you would normally be able to select the old kernel while booting.  You can make it the default again by editing **/boot/grub/menu.lst** and commenting out the section for new kernel.  That's all for the case where you upgraded the kernel, which you may not have done.

If you didn't do a kernel upgrade, we need to look for other causes.

---

### Post by siazikk on 2007-09-07
That makes sense.  Thanks for your reply!! 
My wireless worked immediately from the first install of Ubuntu without tweaking... until now.

I did the update from the gui icon that says there are updates available.  

This is what the log says:

siazikk@Peace:~$ grep 2007-09-06 /var/log/dpkg.log
2007-09-06 21:00:36 upgrade libkrb53 1.4.3-5ubuntu0.4 1.4.3-5ubuntu0.5
2007-09-06 21:00:36 status half-configured libkrb53 1.4.3-5ubuntu0.4
2007-09-06 21:00:36 status unpacked libkrb53 1.4.3-5ubuntu0.4
2007-09-06 21:00:36 status half-installed libkrb53 1.4.3-5ubuntu0.4
2007-09-06 21:00:36 status half-installed libkrb53 1.4.3-5ubuntu0.4
2007-09-06 21:00:37 status unpacked libkrb53 1.4.3-5ubuntu0.5
2007-09-06 21:00:37 status unpacked libkrb53 1.4.3-5ubuntu0.5
2007-09-06 21:00:37 status unpacked libkrb53 1.4.3-5ubuntu0.5
2007-09-06 21:00:37 status half-configured libkrb53 1.4.3-5ubuntu0.5
2007-09-06 21:00:44 status installed libkrb53 1.4.3-5ubuntu0.5

I was able to use the wireless card that evening (since I didn't reboot)  The next day I noticed the change.

Can I rollback to before the update?  Or does it look like I have to install the driver? If so, how do I find out what driver I need?
I have an Acer Aspire 3500.

Thanks!
~Katrina

---

### Post by noob12 on 2007-09-07
Well, from the log output we can see that you didn't actually do a kernel upgrade at all, you just got the **libkrb** update; we should really look for another cause.  No indication you should install drivers or rollback anything at this point.

Can you post the output from 
```

dmesg

```
We hope to see some indications of why the driver isn't claiming the device.

---

### Post by siazikk on 2007-09-11
Thanks!  Here is the output from dmesg:
(I'm not able to connect to the internet often now that I don't have wireless, so my visits here will be infrequent.  I do appreciate your patience and your help!  Thanks!)

siazikk@Peace:~$ dmesg
[17179569.184000] Linux version 2.6.15-29-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Aug 29 13:20:33 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bdf0000 (usable)
[17179569.184000]  BIOS-e820: 000000001bdf0000 - 000000001bdfa000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001bdfa000 - 000000001be00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001be00000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 445MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f8180
[17179569.184000] On node 0 totalpages: 114160
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110064 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f8150
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1bdf64c2
[17179569.184000] ACPI: FADT (v001 SiS    661MX    0x06040000 PTL  0x00000001) @ 0x1bdf9f46
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x1bdf9fba
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x1bdf64f2
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
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1400.245 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.532000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.532000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.544000] Memory: 442164k/456640k available (1977k kernel code, 13892k reserved, 605k data, 288k init, 0k highmem)
[17179572.544000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.624000] Calibrating delay using timer specific routine.. 2802.21 BogoMIPS (lpj=5604424)
[17179572.624000] Security Framework v1.0.0 initialized
[17179572.624000] SELinux:  Disabled at boot.
[17179572.624000] Mount-cache hash table entries: 512
[17179572.624000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179572.624000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179572.624000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.624000] CPU: L2 cache: 1024K
[17179572.624000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000000 00000000 00000000
[17179572.624000] mtrr: v2.0 (20020519)
[17179572.624000] CPU: Intel(R) Celeron(R) M processor         1.40GHz stepping 08
[17179572.624000] Enabling fast FPU save and restore... done.
[17179572.624000] Enabling unmasked SIMD FPU exception support... done.
[17179572.624000] Checking 'hlt' instruction... OK.
[17179572.640000] checking if image is initramfs... it is
[17179573.428000] Freeing initrd memory: 6616k freed
[17179573.444000] ACPI: Looking for DSDT ... not found!
[17179573.448000] ENABLING IO-APIC IRQs
[17179573.448000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179573.596000] NET: Registered protocol family 16
[17179573.596000] EISA bus registered
[17179573.596000] ACPI: bus type pci registered
[17179573.596000] PCI: PCI BIOS revision 2.10 entry at 0xfd786, last bus=1
[17179573.596000] PCI: Using configuration type 1
[17179573.596000] ACPI: Subsystem revision 20051216
[17179573.596000] ACPI: Interpreter enabled
[17179573.596000] ACPI: Using IOAPIC for interrupt routing
[17179573.600000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.600000] PCI: Probing PCI hardware (bus 00)
[17179573.600000] Uncovering SIS963 that hid as a SIS503 (compatible=0)
[17179573.600000] Enabling SiS 96x SMBus.
[17179573.600000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179573.600000] Boot video device is 0000:01:00.0
[17179573.600000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.608000] ACPI: Embedded Controller [EC0] (gpe 25) interrupt mode.
[17179573.624000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
[17179573.624000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 9 10 11)
[17179573.624000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[17179573.624000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11)
[17179573.624000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[17179573.624000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[17179573.624000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[17179573.624000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
[17179573.624000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.624000] pnp: PnP ACPI init
[17179573.636000] pnp: PnP ACPI: found 8 devices
[17179573.636000] PnPBIOS: Disabled by ACPI PNP
[17179573.636000] PCI: Using ACPI for IRQ routing
[17179573.636000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.636000] pnp: 00:03: ioport range 0x8000-0x807f could not be reserved
[17179573.636000] pnp: 00:03: ioport range 0x8080-0x80ff has been reserved
[17179573.636000] pnp: 00:03: ioport range 0x8100-0x811f has been reserved
[17179573.636000] pnp: 00:03: ioport range 0x4d0-0x4d1 has been reserved
[17179573.636000] pnp: 00:03: ioport range 0xfe00-0xfe00 has been reserved
[17179573.636000] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[17179573.636000] PCI: Bridge: 0000:00:01.0
[17179573.636000]   IO window: 9000-9fff
[17179573.636000]   MEM window: e2100000-e21fffff
[17179573.636000]   PREFETCH window: e8000000-efffffff
[17179573.636000] PCI: Bus 2, cardbus bridge: 0000:00:06.0
[17179573.636000]   IO window: 00002400-000024ff
[17179573.636000]   IO window: 00002800-000028ff
[17179573.636000]   PREFETCH window: 30000000-31ffffff
[17179573.636000]   MEM window: 32000000-33ffffff
[17179573.636000] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
[17179573.636000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179573.640000] audit: initializing netlink socket (disabled)
[17179573.640000] audit(1189524034.640:1): initialized
[17179573.640000] VFS: Disk quotas dquot_6.5.1
[17179573.640000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.640000] Initializing Cryptographic API
[17179573.640000] io scheduler noop registered
[17179573.640000] io scheduler anticipatory registered
[17179573.640000] io scheduler deadline registered
[17179573.640000] io scheduler cfq registered
[17179573.640000] isapnp: Scanning for PnP cards...
[17179574.004000] isapnp: No Plug & Play device found
[17179574.020000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.088000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.092000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.092000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.096000] PCI: Enabling device 0000:00:02.6 (0000 -> 0001)
[17179574.096000] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 185
[17179574.096000] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[17179574.096000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.096000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.096000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.096000] mice: PS/2 mouse device common for all mice
[17179574.108000] EISA: Probing bus 0 at eisa.0
[17179574.108000] Cannot allocate resource for EISA slot 1
[17179574.108000] Cannot allocate resource for EISA slot 2
[17179574.108000] Cannot allocate resource for EISA slot 8
[17179574.108000] EISA: Detected 0 cards.
[17179574.108000] NET: Registered protocol family 2
[17179574.164000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179574.164000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179574.164000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179574.164000] TCP: Hash tables configured (established 16384 bind 16384)
[17179574.164000] TCP reno registered
[17179574.164000] TCP bic registered
[17179574.164000] NET: Registered protocol family 1
[17179574.164000] NET: Registered protocol family 8
[17179574.164000] NET: Registered protocol family 20
[17179574.164000] Using IPI Shortcut mode
[17179574.172000] ACPI wakeup devices:
[17179574.172000] PCI0  LAN MODM  KBC USB0 USB1 USB2 USB3
[17179574.172000] ACPI: (supports S0 S3 S4 S5)
[17179574.172000] Freeing unused kernel memory: 288k freed
[17179574.192000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.244000] vga16fb: initializing
[17179574.244000] vga16fb: mapped to 0xc00a0000
[17179574.340000] Console: switching to colour frame buffer device 80x25
[17179574.340000] fb0: VGA16 VGA frame buffer device
[17179575.408000] Capability LSM initialized
[17179575.444000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179575.444000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.444000] ACPI: Thermal Zone [THRM] (41 C)
[17179575.816000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179575.816000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 193
[17179575.816000] SIS5513: chipset revision 0
[17179575.816000] SIS5513: not 100% native mode: will probe irqs later
[17179575.816000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179575.816000]     ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:DMA, hdb:pio
[17179575.816000]     ide1: BM-DMA at 0x1008-0x100f, BIOS settings: hdc:DMA, hdd:pio
[17179575.816000] Probing IDE interface ide0...
[17179576.104000] hda: HTS424040M9AT00, ATA DISK drive
[17179576.776000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.792000] Probing IDE interface ide1...
[17179577.528000] hdc: UJDA760 DVD/CDRW, ATAPI CD/DVD-ROM drive
[17179577.864000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.872000] hda: max request size: 1024KiB
[17179577.880000] hda: 78140160 sectors (40007 MB) w/1739KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.880000] hda: cache flushes supported
[17179577.880000]  hda: hda1 hda2 < hda5 >
[17179577.952000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.952000] Uniform CD-ROM driver Revision: 3.20
[17179578.568000] usbcore: registered new driver usbfs
[17179578.568000] usbcore: registered new driver hub
[17179578.568000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.568000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 201
[17179578.568000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179578.792000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179578.792000] ohci_hcd 0000:00:03.0: irq 201, io mem 0xe2000000
[17179578.852000] hub 1-0:1.0: USB hub found
[17179578.852000] hub 1-0:1.0: 3 ports detected
[17179578.956000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 209
[17179578.956000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179579.176000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179579.176000] ohci_hcd 0000:00:03.1: irq 209, io mem 0xe2001000
[17179579.232000] hub 2-0:1.0: USB hub found
[17179579.232000] hub 2-0:1.0: 3 ports detected
[17179579.336000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 217
[17179579.336000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179579.336000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[17179579.336000] ehci_hcd 0000:00:03.3: irq 217, io mem 0xe2002000
[17179579.336000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.336000] hub 3-0:1.0: USB hub found
[17179579.336000] hub 3-0:1.0: 6 ports detected
[17179579.592000] Attempting manual resume
[17179579.652000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.668000] kjournald starting.  Commit interval 5 seconds
[17179595.552000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179595.560000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.712000] Linux agpgart interface v0.101 (c) Dave Jones
[17179595.720000] agpgart: Detected SiS 661 chipset
[17179595.724000] agpgart: AGP aperture is 32M @ 0xe0000000
[17179595.960000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179595.960000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0082]
[17179595.960000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179595.960000] Yenta: Routing CardBus interrupts to PCI
[17179595.960000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
[17179595.992000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 185
[17179595.992000] ath_hal: module license 'Proprietary' taints kernel.
[17179595.992000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179596.072000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179596.076000] ath_rate_sample: 1.2
[17179596.080000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179596.148000] Real Time Clock Driver v1.12
[17179596.192000] Yenta: ISA IRQ mask 0x06f8, PCI irq 177
[17179596.192000] Socket status: 30000006
[17179596.388000] input: PC Speaker as /class/input/input1
[17179596.396000] i2c-sis96x version 1.0.0
[17179596.396000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[17179596.676000] cs: IO port probe 0x100-0x3af: clean.
[17179596.676000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[17179596.680000] cs: IO port probe 0x820-0x8ff: clean.
[17179596.680000] cs: IO port probe 0xc00-0xcf7: clean.
[17179596.680000] cs: IO port probe 0xa00-0xaff: clean.
[17179596.700000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[17179596.736000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179596.784000] ts: Compaq touchscreen protocol output
[17179596.812000] intel8x0_measure_ac97_clock: measured 55470 usecs
[17179596.812000] intel8x0: clocking to 48000
[17179596.812000] PCI: Enabling device 0000:00:0b.0 (0010 -> 0012)
[17179596.812000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 225
[17179596.812000] ath_attach: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[17179596.812000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
[17179597.284000] sis900.c: v1.08.09 Sep. 19 2005
[17179597.284000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179597.292000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[17179597.296000] 0000:00:04.0: Using transceiver found at address 13 as default
[17179597.300000] eth0: SiS 900 PCI Fast Ethernet at 0x2000, IRQ 177, 00:c0:9f:9b:f0:1c.
[17179597.656000] eth0: Media Link Off
[17179597.772000] lp: driver loaded but no devices found
[17179597.824000] Adding 1317288k swap on /dev/hda5.  Priority:-1 extents:1 across:1317288k
[17179597.928000] EXT3 FS on hda1, internal journal
[17179598.108000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179598.108000] md: bitmap version 4.39
[17179598.940000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179598.972000] NET: Registered protocol family 17
[17179599.540000] cdrom: open failed.
[17179605.984000] ACPI: AC Adapter [ACAD] (on-line)
[17179606.008000] ACPI: Battery Slot [BAT1] (battery present)
[17179606.096000] ACPI: Power Button (FF) [PWRF]
[17179606.096000] ACPI: Lid Switch [LID]
[17179606.096000] ACPI: Power Button (CM) [PWRB]
[17179606.096000] ACPI: Sleep Button (CM) [SLPB]
[17179606.196000] ibm_acpi: ec object not found
[17179606.228000] pcc_acpi: loading...
[17179615.560000] ppdev: user-space parallel port driver
[17179616.012000] apm: BIOS not found.
[17179616.352000] Bluetooth: Core ver 2.8
[17179616.352000] NET: Registered protocol family 31
[17179616.352000] Bluetooth: HCI device and connection manager initialized
[17179616.352000] Bluetooth: HCI socket layer initialized
[17179616.432000] Bluetooth: L2CAP ver 2.8
[17179616.432000] Bluetooth: L2CAP socket layer initialized
[17179616.464000] Bluetooth: RFCOMM socket layer initialized
[17179616.464000] Bluetooth: RFCOMM TTY layer initialized
[17179616.464000] Bluetooth: RFCOMM ver 1.7
[17179768.656000] eth0: Media Link On 100mbps full-duplex
[17179774.020000] NET: Registered protocol family 10
[17179774.020000] lo: Disabled Privacy Extensions
[17179774.020000] IPv6 over IPv4 tunneling driver
[17179784.740000] eth0: no IPv6 routers present
[17179837.492000] eth0: Media Link On 100mbps full-duplex
[17179846.088000] eth0: no IPv6 routers present
[17179940.988000] ibm_acpi: ec object not found
siazikk@Peace:~$

---

### Post by noob12 on 2007-09-11
Well the driver loads but then complains about this:
> 
[17179596.812000] ath_attach: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)


Are you saying the driver used to work with this hardware and then stopped?   By any chance do you dual boot with WIndows?   Does it work differently if you warm boot across?

It will be useful if you can get the exact ids for the device using **lspci -nn** or **lspci -vv** and extracting the line or lines for the Atheros card you have.

Hoping some other readers might be familiar with this.

---

### Post by bmartin on 2007-09-11
**lspci -nn** is probably the only thing necessary. Most likely it's compatible with the [Madwifi driver]("http://ubuntuforums.org/showthread.php?t=485579"). If it's a newer Atheros chipset, you might have to use ndiswrapper. I wrote a guide for the 5007EG chipset; there are guides for some of the other chipsets, as well.

---

### Post by kevdog on 2007-09-11
Are you guys saying that the newer Atheros chipset will not work with madwifi??  I might be wrong in my understanding buy arent the restricted atheros drivers that come with Feisty (linux-restricted-package) include simply the madwifi drivers??  Im sure compiling the drivers from source would update the kernel module, but it the user stated it was working before, but now is not working after an upgrade, Im not following how installing libkrb (a Kerberos library) would in any way effect the madwifi drivers.  

Id be curious if the user manually unloaded the modules and then reloaded them by hand at the command line, if dmesg would produce the same output.  I think the modules are ath_hal and ath_pci off the top of my head, but I would have to check the madwifi site for sure to confirm this.

---

### Post by siazikk on 2007-09-13
Hello!  Thanks for the replies everyone!
I will be out of town for one week so I will try any more suggestions when I return...

For now I will say that I do not dual boot, and the wireless was working fine before the update (it is possible something else triggered it coincidently around the same day)

The output of lspci -vv and -n is this:

siazikk@Peace:~$ lspci -vv
0000:00:0b.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
        Subsystem: AMBIT Microsystem Corp.: Unknown device 0418
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 225
        Region 0: Memory at e2010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

siazikk@Peace:~$ lspci -n
0000:00:00.0 0600: 1039:0661 (rev 11)
0000:00:01.0 0604: 1039:0003
0000:00:02.0 0601: 1039:0963 (rev 25)
0000:00:02.1 0c05: 1039:0016
0000:00:02.5 0101: 1039:5513
0000:00:02.6 0703: 1039:7013 (rev a0)
0000:00:02.7 0401: 1039:7012 (rev a0)
0000:00:03.0 0c03: 1039:7001 (rev 0f)
0000:00:03.1 0c03: 1039:7001 (rev 0f)
0000:00:03.3 0c03: 1039:7002
0000:00:04.0 0200: 1039:0900 (rev 91)
0000:00:06.0 0607: 104c:ac50 (rev 02)
0000:00:0b.0 0200: 168c:001a (rev 01)
0000:01:00.0 0300: 1039:6330

I'm not sure how to read this.
How do I find out exactly what chipset I have?
I looked on the Acer website (I have an older Acer Aspire 3500, I got it the summer of 2005)
The website wasn't clear about the network card.  It did state that it had a Core Logic Chipset SiS M661MX.  Is that what I'm looking for?

Does this info help you?
Thanks, and I will be back in touch next week!!
Adios!

---

### Post by kevdog on 2007-09-14
please post 

lspci -nn
lshw -C network

---

### Post by siazikk on 2007-09-21
Hello!  I'm back home and ready to figure this out!

siazikk@Peace:~$ sudo lspci -nn
0000:00:00.0 0600: 1039:0661 (rev 11)
0000:00:01.0 0604: 1039:0003
0000:00:02.0 0601: 1039:0963 (rev 25)
0000:00:02.1 0c05: 1039:0016
0000:00:02.5 0101: 1039:5513
0000:00:02.6 0703: 1039:7013 (rev a0)
0000:00:02.7 0401: 1039:7012 (rev a0)
0000:00:03.0 0c03: 1039:7001 (rev 0f)
0000:00:03.1 0c03: 1039:7001 (rev 0f)
0000:00:03.3 0c03: 1039:7002
0000:00:04.0 0200: 1039:0900 (rev 91)
0000:00:06.0 0607: 104c:ac50 (rev 02)
0000:00:0b.0 0200: 168c:001a (rev 01)
0000:01:00.0 0300: 1039:6330


siazikk@Peace:~$ sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:9b:f0:1c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sis900 driverversion=v1.08.09 Sep. 19 2005 duplex=full ip=192.168.100.2 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:e2003000-e2003fff irq:177
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: b
       bus info: pci@00:0b.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:e2010000-e201ffff irq:225

---

### Post by noob12 on 2007-09-21
OK.  Here's what I see from this.

This tells us you have an **168c:001a** which is apparently an Atheros 5213 device.

The device is UNCLAIMED by any driver.

This device is in the supported device list for the ath_pci module in current Ubuntu 7.04. (I am looking at modinfo of the ath_pci module in 2.6.20-16-generic on mine; these have ath_pci 0.9.3.1 and ath_hal 0.9.18.0).  It's hard to tell about ath_hal, because it doesn't enumerate covered devices statically in its modinfo.

Your dmesg shows kernel version 2.6.15-29-386,  and:
```

[17179595.992000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179596.072000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179596.076000] ath_rate_sample: 1.2
[17179596.080000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
... later
[17179596.812000] ath_attach: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

```
after which things become pretty much hopeless.

Meanwhile I notice that the current stable released madwifi driver set (0.9.3.2) includes ath_pci 9.4.5 and ath_hal 0.9.18.0.

It really looks like you may have an oddly matched set of ath_hal and ath_pci modules.  You might try building from the latest stable madwifi release; I don't think you need trunk/experimental versions.  This might be causing your problem.   

You might also  just want to try the stock support in 2.6.20-16.

What I can't explain is why this would ever have worked for you.  Maybe you were booting a different kernel version from the menu?

---

