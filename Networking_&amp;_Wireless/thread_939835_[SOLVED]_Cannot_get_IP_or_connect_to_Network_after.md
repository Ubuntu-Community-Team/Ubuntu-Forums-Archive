---
title: "[SOLVED] Cannot get IP or connect to Network after installing ATI driver"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by ccontrerd on 2008-10-06
Hi,

I've been working with this problem for a couple of weeks but I think I was able to isolate it, all comes to this, I install Ubuntu, 8.04 (but also tried update, beta, etc.) Network card works (wire) can get DHCP address...happy. I installed ATI driver, driver updates ( I have used envy, also directly installed driver for Linux from ATIs site, etc etc). Driver installs, then no network...I use the commands -sudo ifdown eth0 and -sudo ifup eth0 and I'm not able to get a DCHP, in fact I see that keeps sending DCHP requests and requests and nothing... I try to set IP manually... no response eihter, the arp displays as incomplete, I TRY to force it manually to the MAC of the Gateway and nothing. Ok I unistall the ATI driver and now I try -sudo ifdown eth0 and -sudo ifup eth0 and now I have Internet.!!!

For those who are wondering about my network card I have tried 3 different cards, Realtek...etc. I even have tried and USB Wireless adapter and when I have the ATI driver installed seems the IP stack or something is messed someway.

Also a funny thing is that if I install the ATI driver and instead to do a hard reboot I use CTRL-ALT-BACSKPACE the driver works and also the networ card..! the problem arises when I try a hardware reboot, this times reboots and cannot get IP address or communicate if I set one fix, again until I un install the ATI driver and then I go again...

Any one can suggest something? 

PD I really have tried a lot of things but I prefer to listen to suggestion instead of making a big list and instead telling you about I have try already...

Regards

---

### Post by nixscripter on 2008-10-06
What is your graphics card? It might be fighting with the network card on the bus.

Check **/var/log/messages** and see if there are complaints about drivers failing to load stuff.

---

### Post by ccontrerd on 2008-10-08
Well this is the /var/log/messages....

Sure I dont see something weird in the booting, BTW the ATI is a Radeon HD2600 PRO. 

Check it in the attach.

Also I have some sudo ifdown and sudo ifup capture in one the case where graphic driver is installed and the second without the driver...as you can see in the former I cannot get a DHCP IP, and in the second case is possible...


Thanks for the support!

---

### Post by nixscripter on 2008-10-09
Uh, did it attach? I don't see it...

---

### Post by ccontrerd on 2008-10-10
Sorry about that I tried to attach some file and I had invalid file error, tried to tar it but same, so here is the output:

Oct  8 13:09:09 carlos-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct  8 13:09:09 carlos-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Oct  8 13:09:09 carlos-desktop kernel: Loaded 28492 symbols from /boot/System.map-2.6.24-19-generic.
Oct  8 13:09:09 carlos-desktop kernel: Symbols match kernel version 2.6.24.
Oct  8 13:09:09 carlos-desktop kernel: Loaded 24673 symbols from 100 modules.
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Au
g 20 17:53:40 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Command line: root=UUID=85b272e6-4fe9-4f5c-95ee-1f01e7763892 ro quiet splash
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffc0000 (usable)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007ffce000 (ACPI data)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]  BIOS-e820: 000000007ffce000 - 000000007fff0000 (ACPI NVS)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] end_pfn_map = 1043969
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] DMI 2.3 present.
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F84E0 checksum 0
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: RSDP 000F84E0, 0014 (r0 ACPIAM)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: RSDT 7FFC0000, 0030 (r1 A M I  OEMRSDT   4000627 MSFT       97)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: FACP 7FFC0200, 0084 (r2 A M I  OEMFACP   4000627 MSFT       97)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: DSDT 7FFC0400, 409D (r1  12345 12345123      123 INTL  2002026)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: FACS 7FFCE000, 0040
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: APIC 7FFC0390, 006C (r1 A M I  OEMAPIC   4000627 MSFT       97)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: OEMB 7FFCE040, 004B (r1 A M I  AMI_OEM   4000627 MSFT       97)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] No NUMA configuration found
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Faking a node at 0000000000000000-000000007ffc0000
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007ffc0000
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Zone PFN ranges:
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]   DMA             0 ->     4096
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]   DMA32        4096 ->  1048576
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]   Normal    1048576 ->  1048576
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Movable zone start PFN for each node
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]     0:        0 ->      159
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000]     0:      256 ->   524224
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Processor #0 (Bootup-CPU)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Processor #1
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Setting APIC routing to flat
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e6000
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e6000 - 0000000000100000
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515740
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Policy zone: DMA32
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Kernel command line: root=UUID=85b272e6-4fe9-4f5c-95ee-1f01e7763892 ro quiet splash
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] Initializing CPU#0
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Oct  8 13:09:09 carlos-desktop kernel: [    0.000000] TSC calibrated against PM_TIMER
Oct  8 13:09:09 carlos-desktop kernel: [   34.132375] time.c: Detected 3066.661 MHz processor.
Oct  8 13:09:09 carlos-desktop kernel: [   34.134025] Console: colour VGA+ 80x25
Oct  8 13:09:09 carlos-desktop kernel: [   34.134029] console [tty0] enabled
Oct  8 13:09:09 carlos-desktop kernel: [   34.134046] Checking aperture...
Oct  8 13:09:09 carlos-desktop kernel: [   34.172195] Memory: 2055128k/2096896k available (2489k kernel code, 41380k reserved, 1318k data, 320k init)
Oct  8 13:09:09 carlos-desktop kernel: [   34.172253] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Oct  8 13:09:09 carlos-desktop kernel: [   34.250046] Calibrating delay using timer specific routine.. 6141.79 BogoMIPS (lpj=12283583)
Oct  8 13:09:09 carlos-desktop kernel: [   34.250095] Security Framework initialized
Oct  8 13:09:09 carlos-desktop kernel: [   34.250104] SELinux:  Disabled at boot.
Oct  8 13:09:09 carlos-desktop kernel: [   34.250127] AppArmor: AppArmor initialized
Oct  8 13:09:09 carlos-desktop kernel: [   34.250131] Failure registering capabilities with primary security module.
Oct  8 13:09:09 carlos-desktop kernel: [   34.250457] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Oct  8 13:09:09 carlos-desktop kernel: [   34.253229] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Oct  8 13:09:09 carlos-desktop kernel: [   34.254623] Mount-cache hash table entries: 256
Oct  8 13:09:09 carlos-desktop kernel: [   34.254853] Initializing cgroup subsys ns
Oct  8 13:09:09 carlos-desktop kernel: [   34.254860] Initializing cgroup subsys cpuacct
Oct  8 13:09:09 carlos-desktop kernel: [   34.254889] CPU: Trace cache: 12K uops, L1 D cache: 16K
Oct  8 13:09:09 carlos-desktop kernel: [   34.254892] CPU: L2 cache: 1024K
Oct  8 13:09:09 carlos-desktop kernel: [   34.254895] CPU 0/0 -> Node 0
Oct  8 13:09:09 carlos-desktop kernel: [   34.254896] using mwait in idle threads.
Oct  8 13:09:09 carlos-desktop kernel: [   34.254898] CPU: Physical Processor ID: 0
Oct  8 13:09:09 carlos-desktop kernel: [   34.254900] CPU: Processor Core ID: 0
Oct  8 13:09:09 carlos-desktop kernel: [   34.254915] CPU0: Thermal monitoring enabled (TM1)
Oct  8 13:09:09 carlos-desktop kernel: [   34.254935] SMP alternatives: switching to UP code
Oct  8 13:09:09 carlos-desktop kernel: [   34.256163] Early unpacking initramfs... done
Oct  8 13:09:09 carlos-desktop kernel: [   34.574965] ACPI: Core revision 20070126
Oct  8 13:09:09 carlos-desktop kernel: [   34.575022] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct  8 13:09:09 carlos-desktop kernel: [   34.618642] Using local APIC timer interrupts.
Oct  8 13:09:09 carlos-desktop kernel: [   34.651170] Detected 8.333 MHz APIC timer.
Oct  8 13:09:09 carlos-desktop kernel: [   34.651306] SMP alternatives: switching to SMP code
Oct  8 13:09:09 carlos-desktop kernel: [   34.652293] Booting processor 1/2 APIC 0x1
Oct  8 13:09:09 carlos-desktop kernel: [   37.193355] Initializing CPU#1
Oct  8 13:09:09 carlos-desktop kernel: [   37.273127] Calibrating delay using timer specific routine.. 6133.20 BogoMIPS (lpj=12266410)
Oct  8 13:09:09 carlos-desktop kernel: [   37.273142] CPU: Trace cache: 12K uops, L1 D cache: 16K
Oct  8 13:09:09 carlos-desktop kernel: [   37.273144] CPU: L2 cache: 1024K
Oct  8 13:09:09 carlos-desktop kernel: [   37.273148] CPU 1/1 -> Node 0
Oct  8 13:09:09 carlos-desktop kernel: [   37.273150] CPU: Physical Processor ID: 0
Oct  8 13:09:09 carlos-desktop kernel: [   37.273152] CPU: Processor Core ID: 0
Oct  8 13:09:09 carlos-desktop kernel: [   37.273166] CPU1: Thermal monitoring enabled (TM1)
Oct  8 13:09:09 carlos-desktop kernel: [   37.273416]               Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 09
Oct  8 13:09:09 carlos-desktop kernel: [   34.743244] checking TSC synchronization [CPU#0 -> CPU#1]:
Oct  8 13:09:09 carlos-desktop kernel: [   34.763196] Measured 7780533070 cycles TSC warp between CPUs, turning off TSC clock.
Oct  8 13:09:09 carlos-desktop kernel: [   34.763200] Marking TSC unstable due to check_tsc_sync_source failed
Oct  8 13:09:09 carlos-desktop kernel: [   34.763245] Brought up 2 CPUs
Oct  8 13:09:09 carlos-desktop kernel: [   34.763827] net_namespace: 120 bytes
Oct  8 13:09:09 carlos-desktop kernel: [   34.764278] Time: 13:08:46  Date: 10/08/08
Oct  8 13:09:09 carlos-desktop kernel: [   34.764313] NET: Registered protocol family 16
Oct  8 13:09:09 carlos-desktop kernel: [   34.764581] ACPI: bus type pci registered
Oct  8 13:09:09 carlos-desktop kernel: [   34.764680] PCI: Using configuration type 1
Oct  8 13:09:09 carlos-desktop kernel: [   34.774178] ACPI: Interpreter enabled
Oct  8 13:09:09 carlos-desktop kernel: [   34.774182] ACPI: (supports S0 S1 S3 S4 S5)
Oct  8 13:09:09 carlos-desktop kernel: [   34.774201] ACPI: Using IOAPIC for interrupt routing
Oct  8 13:09:09 carlos-desktop kernel: [   34.784421] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct  8 13:09:09 carlos-desktop kernel: [   34.797433] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct  8 13:09:09 carlos-desktop kernel: [   34.797551] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Oct  8 13:09:09 carlos-desktop kernel: [   34.797663] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Oct  8 13:09:09 carlos-desktop kernel: [   34.797774] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct  8 13:09:09 carlos-desktop kernel: [   34.797885] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct  8 13:09:09 carlos-desktop kernel: [   34.797996] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct  8 13:09:09 carlos-desktop kernel: [   34.798107] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct  8 13:09:09 carlos-desktop kernel: [   34.798217] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct  8 13:09:09 carlos-desktop kernel: [   34.798358] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  1C, should be 17 [20070126]
Oct  8 13:09:09 carlos-desktop kernel: [   34.798365] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct  8 13:09:09 carlos-desktop kernel: [   34.798408] pnp: PnP ACPI init
Oct  8 13:09:09 carlos-desktop kernel: [   34.798419] ACPI: bus type pnp registered
Oct  8 13:09:09 carlos-desktop kernel: [   34.804803] pnp: PnP ACPI: found 11 devices
Oct  8 13:09:09 carlos-desktop kernel: [   34.804806] ACPI: ACPI bus type pnp unregistered
Oct  8 13:09:09 carlos-desktop kernel: [   34.805133] PCI: Using ACPI for IRQ routing
Oct  8 13:09:09 carlos-desktop kernel: [   34.805137] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct  8 13:09:09 carlos-desktop kernel: [   34.818759] NET: Registered protocol family 8
Oct  8 13:09:09 carlos-desktop kernel: [   34.818762] NET: Registered protocol family 20
Oct  8 13:09:09 carlos-desktop kernel: [   34.818804] PCI-GART: No AMD northbridge found.
Oct  8 13:09:09 carlos-desktop kernel: [   34.818865] AppArmor: AppArmor Filesystem Enabled
Oct  8 13:09:09 carlos-desktop kernel: [   34.830748] system 00:06: ioport range 0xa00-0xa0f has been reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830751] system 00:06: ioport range 0x290-0x29f has been reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830753] system 00:06: ioport range 0xa20-0xa2f has been reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830756] system 00:06: ioport range 0xa30-0xa3f has been reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830758] system 00:06: ioport range 0xa40-0xa4f has been reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830764] system 00:07: ioport range 0x3e0-0x3e7 has been reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830766] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830768] system 00:07: ioport range 0x800-0x87f has been reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830770] system 00:07: ioport range 0x400-0x41f has been reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830778] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830780] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830787] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830789] system 00:0a: iomem range 0xc0000-0xcffff has been reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830791] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830794] system 00:0a: iomem range 0x100000-0x7fffffff could not be reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.830797] system 00:0a: iomem range 0xff380000-0xffffffff could not be reserved
Oct  8 13:09:09 carlos-desktop kernel: [   34.831340] PCI: Bridge: 0000:00:01.0
Oct  8 13:09:09 carlos-desktop kernel: [   34.831343]   IO window: a000-cfff
Oct  8 13:09:09 carlos-desktop kernel: [   34.831348]   MEM window: ff500000-ff5fffff
Oct  8 13:09:09 carlos-desktop kernel: [   34.831352]   PREFETCH window: bff00000-dfefffff
Oct  8 13:09:09 carlos-desktop kernel: [   34.831391] NET: Registered protocol family 2
Oct  8 13:09:09 carlos-desktop kernel: [   34.834681] Time: acpi_pm clocksource has been installed.
Oct  8 13:09:09 carlos-desktop kernel: [   34.866725] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Oct  8 13:09:09 carlos-desktop kernel: [   34.867896] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Oct  8 13:09:09 carlos-desktop kernel: [   34.873261] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Oct  8 13:09:09 carlos-desktop kernel: [   34.874619] TCP: Hash tables configured (established 262144 bind 65536)
Oct  8 13:09:09 carlos-desktop kernel: [   34.874626] TCP reno registered
Oct  8 13:09:09 carlos-desktop kernel: [   34.886815] checking if image is initramfs... it is
Oct  8 13:09:09 carlos-desktop kernel: [   35.508479] Freeing initrd memory: 7550k freed
Oct  8 13:09:09 carlos-desktop kernel: [   38.049716] audit: initializing netlink socket (disabled)
Oct  8 13:09:09 carlos-desktop kernel: [   38.049743] audit(1223471326.348:1): initialized
Oct  8 13:09:09 carlos-desktop kernel: [   38.052606] VFS: Disk quotas dquot_6.5.1
Oct  8 13:09:09 carlos-desktop kernel: [   38.052709] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Oct  8 13:09:09 carlos-desktop kernel: [   38.052885] io scheduler noop registered
Oct  8 13:09:09 carlos-desktop kernel: [   38.052888] io scheduler anticipatory registered
Oct  8 13:09:09 carlos-desktop kernel: [   38.052890] io scheduler deadline registered
Oct  8 13:09:09 carlos-desktop kernel: [   38.053029] io scheduler cfq registered (default)
Oct  8 13:09:09 carlos-desktop kernel: [   38.053046] PCI: VIA PCI bridge detected. Disabling DAC.
Oct  8 13:09:09 carlos-desktop kernel: [   38.053115] PCI: Bypassing VIA 8237 APIC De-Assert Message
Oct  8 13:09:09 carlos-desktop kernel: [   38.089205] Real Time Clock Driver v1.12ac
Oct  8 13:09:09 carlos-desktop kernel: [   38.089351] Linux agpgart interface v0.102
Oct  8 13:09:09 carlos-desktop kernel: [   38.089354] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct  8 13:09:09 carlos-desktop kernel: [   38.089501] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct  8 13:09:09 carlos-desktop kernel: [   38.090309] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct  8 13:09:09 carlos-desktop kernel: [   38.091344] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct  8 13:09:09 carlos-desktop kernel: [   38.091438] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct  8 13:09:09 carlos-desktop kernel: [   38.091634] PNP: No PS/2 controller found. Probing ports directly.
Oct  8 13:09:09 carlos-desktop kernel: [   38.092054] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct  8 13:09:09 carlos-desktop kernel: [   38.092062] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct  8 13:09:09 carlos-desktop kernel: [   38.111395] mice: PS/2 mouse device common for all mice
Oct  8 13:09:09 carlos-desktop kernel: [   38.111455] cpuidle: using governor ladder
Oct  8 13:09:09 carlos-desktop kernel: [   38.111458] cpuidle: using governor menu
Oct  8 13:09:09 carlos-desktop kernel: [   38.111581] NET: Registered protocol family 1
Oct  8 13:09:09 carlos-desktop kernel: [   38.111663] registered taskstats version 1
Oct  8 13:09:09 carlos-desktop kernel: [   38.111799]   Magic number: 12:68:129
Oct  8 13:09:09 carlos-desktop kernel: [   38.111967]   hash matches device PNP0C02:01
Oct  8 13:09:09 carlos-desktop kernel: [   38.111973]   hash matches device device:04
Oct  8 13:09:09 carlos-desktop kernel: [   38.111981] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Oct  8 13:09:09 carlos-desktop kernel: [   38.111985] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct  8 13:09:09 carlos-desktop kernel: [   38.111987] EDD information not available.
Oct  8 13:09:09 carlos-desktop kernel: [   38.112002] Freeing unused kernel memory: 320k freed
Oct  8 13:09:09 carlos-desktop kernel: [   36.829063] fuse init (API version 7.9)
Oct  8 13:09:09 carlos-desktop kernel: [   39.478213] ACPI Error (tbinstal-0134): Table has invalid signature [  ^E&#65533;], must be SSDT, PSDT or OEMx [20070126]
Oct  8 13:09:09 carlos-desktop kernel: [   39.478226] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node ffff81007dc064a0), AE_
BAD_SIGNATURE
Oct  8 13:09:09 carlos-desktop kernel: [   36.948141] ACPI: Processor [CPU1] (supports 16 throttling states)
Oct  8 13:09:09 carlos-desktop kernel: [   37.045363] ACPI Error (tbinstal-0134): Table has invalid signature [  ^E&#65533;], must be SSDT, PSDT or OEMx [20070126]
Oct  8 13:09:09 carlos-desktop kernel: [   37.045372] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node ffff81007dc06560), AE_
BAD_SIGNATURE
Oct  8 13:09:09 carlos-desktop kernel: [   39.575624] ACPI: Processor [CPU2] (supports 16 throttling states)
Oct  8 13:09:09 carlos-desktop kernel: [   39.575652] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct  8 13:09:09 carlos-desktop kernel: [   39.575666] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct  8 13:09:09 carlos-desktop kernel: [   40.033935] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
Oct  8 13:09:09 carlos-desktop kernel: [   40.034057] PCI: Enabling device 0000:00:08.0 (0000 -> 0003)
Oct  8 13:09:09 carlos-desktop kernel: [   40.034085] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct  8 13:09:09 carlos-desktop kernel: [   40.034773] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
Oct  8 13:09:09 carlos-desktop kernel: [   40.041100] eth0: ADMtek Comet rev 17 at Port 0x1000, 00:04:e2:23:42:13, IRQ 16.
Oct  8 13:09:09 carlos-desktop kernel: [   37.583972] SCSI subsystem initialized
Oct  8 13:09:09 carlos-desktop kernel: [   37.647606] usbcore: registered new interface driver usbfs
Oct  8 13:09:09 carlos-desktop kernel: [   37.647646] usbcore: registered new interface driver hub
Oct  8 13:09:09 carlos-desktop kernel: [   37.663177] usbcore: registered new device driver usb
Oct  8 13:09:09 carlos-desktop kernel: [   40.206947] PCI: Enabling device 0000:00:09.2 (0000 -> 0002)
Oct  8 13:09:09 carlos-desktop kernel: [   40.206968] ACPI: PCI Interrupt 0000:00:09.2[B] -> GSI 18 (level, low) -> IRQ 18
Oct  8 13:09:09 carlos-desktop kernel: [   40.260315] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[88024000-880247ff]  Max Packet=[2048]  IR/IT c
ontexts=[4/8]
Oct  8 13:09:09 carlos-desktop kernel: [   37.754858] USB Universal Host Controller Interface driver v3.0
Oct  8 13:09:09 carlos-desktop kernel: [   37.755029] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
Oct  8 13:09:09 carlos-desktop kernel: [   37.755050] uhci_hcd 0000:00:10.0: UHCI Host Controller
Oct  8 13:09:09 carlos-desktop kernel: [   37.755471] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Oct  8 13:09:09 carlos-desktop kernel: [   37.755523] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d480
Oct  8 13:09:09 carlos-desktop kernel: [   37.755787] usb usb1: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   37.755826] hub 1-0:1.0: USB hub found
Oct  8 13:09:09 carlos-desktop kernel: [   37.755836] hub 1-0:1.0: 2 ports detected
Oct  8 13:09:09 carlos-desktop kernel: [   37.858483] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
Oct  8 13:09:09 carlos-desktop kernel: [   37.858506] uhci_hcd 0000:00:10.1: UHCI Host Controller
Oct  8 13:09:09 carlos-desktop kernel: [   37.858552] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Oct  8 13:09:09 carlos-desktop kernel: [   37.858587] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d400
Oct  8 13:09:09 carlos-desktop kernel: [   37.858780] usb usb2: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   37.858822] hub 2-0:1.0: USB hub found
Oct  8 13:09:09 carlos-desktop kernel: [   37.858835] hub 2-0:1.0: 2 ports detected
Oct  8 13:09:09 carlos-desktop kernel: [   37.962114] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
Oct  8 13:09:09 carlos-desktop kernel: [   37.962133] uhci_hcd 0000:00:10.2: UHCI Host Controller
Oct  8 13:09:09 carlos-desktop kernel: [   37.962170] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Oct  8 13:09:09 carlos-desktop kernel: [   37.962196] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d080
Oct  8 13:09:09 carlos-desktop kernel: [   37.962327] usb usb3: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   37.962357] hub 3-0:1.0: USB hub found
Oct  8 13:09:09 carlos-desktop kernel: [   37.962364] hub 3-0:1.0: 2 ports detected
Oct  8 13:09:09 carlos-desktop kernel: [   38.065809] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
Oct  8 13:09:09 carlos-desktop kernel: [   38.065827] uhci_hcd 0000:00:10.3: UHCI Host Controller
Oct  8 13:09:09 carlos-desktop kernel: [   38.065858] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Oct  8 13:09:09 carlos-desktop kernel: [   38.065885] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d000
Oct  8 13:09:09 carlos-desktop kernel: [   38.066019] usb usb4: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   38.066049] hub 4-0:1.0: USB hub found
Oct  8 13:09:09 carlos-desktop kernel: [   38.066057] hub 4-0:1.0: 2 ports detected
Oct  8 13:09:09 carlos-desktop kernel: [   40.699880] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
Oct  8 13:09:09 carlos-desktop kernel: [   40.702093] scsi0 : pata_via
Oct  8 13:09:09 carlos-desktop kernel: [   40.703349] scsi1 : pata_via
Oct  8 13:09:09 carlos-desktop kernel: [   40.705490] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Oct  8 13:09:09 carlos-desktop kernel: [   40.705493] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Oct  8 13:09:09 carlos-desktop kernel: [   40.883581] usb 2-1: new full speed USB device using uhci_hcd and address 2
Oct  8 13:09:09 carlos-desktop kernel: [   41.023086] ata1.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.03, max UDMA/66
Oct  8 13:09:09 carlos-desktop kernel: [   38.514971] usb 2-1: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   38.517938] hub 2-1:1.0: USB hub found
Oct  8 13:09:09 carlos-desktop kernel: [   38.519869] hub 2-1:1.0: 4 ports detected
Oct  8 13:09:09 carlos-desktop kernel: [   41.194479] ata1.00: configured for UDMA/66
Oct  8 13:09:09 carlos-desktop kernel: [   38.876361] ata2.00: ATA-7: ST3500630A, 3.AAF, max UDMA/100
Oct  8 13:09:09 carlos-desktop kernel: [   38.876367] ata2.00: 976773168 sectors, multi 16: LBA48 
Oct  8 13:09:09 carlos-desktop kernel: [   38.877743] ata2.01: ATA-6: WDC WD2500BB-14GUA0, 08.02D08, max UDMA/100
Oct  8 13:09:09 carlos-desktop kernel: [   38.877746] ata2.01: 488397168 sectors, multi 16: LBA48 
Oct  8 13:09:09 carlos-desktop kernel: [   38.942757] ata2.00: configured for UDMA/100
Oct  8 13:09:09 carlos-desktop kernel: [   38.956733] ata2.01: configured for UDMA/100
Oct  8 13:09:09 carlos-desktop kernel: [   38.958126] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.03 PQ: 0 ANSI: 5
Oct  8 13:09:09 carlos-desktop kernel: [   38.958304] scsi 1:0:0:0: Direct-Access     ATA      ST3500630A       3.AA PQ: 0 ANSI: 5
Oct  8 13:09:09 carlos-desktop kernel: [   38.958479] scsi 1:0:1:0: Direct-Access     ATA      WDC WD2500BB-14G 08.0 PQ: 0 ANSI: 5
Oct  8 13:09:09 carlos-desktop kernel: [   41.489807] PCI: Enabling device 0000:00:10.4 (0000 -> 0002)
Oct  8 13:09:09 carlos-desktop kernel: [   41.489841] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
Oct  8 13:09:09 carlos-desktop kernel: [   41.490196] ehci_hcd 0000:00:10.4: EHCI Host Controller
Oct  8 13:09:09 carlos-desktop kernel: [   41.490294] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Oct  8 13:09:09 carlos-desktop kernel: [   41.490348] ehci_hcd 0000:00:10.4: irq 21, io mem 0x88024c00
Oct  8 13:09:09 carlos-desktop kernel: [   38.995046] usb 3-1: new low speed USB device using uhci_hcd and address 2
Oct  8 13:09:09 carlos-desktop kernel: [   41.537200] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct  8 13:09:09 carlos-desktop kernel: [   41.537342] usb usb5: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   41.537372] hub 5-0:1.0: USB hub found
Oct  8 13:09:09 carlos-desktop kernel: [   41.537381] hub 5-0:1.0: 8 ports detected
Oct  8 13:09:09 carlos-desktop kernel: [   39.110899] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
Oct  8 13:09:09 carlos-desktop kernel: [   39.110990] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
Oct  8 13:09:09 carlos-desktop kernel: [   39.115222] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
Oct  8 13:09:09 carlos-desktop kernel: [   39.115277] sata_via 0000:00:0f.0: routed to hard irq line 5
Oct  8 13:09:09 carlos-desktop kernel: [   39.117095] scsi2 : sata_via
Oct  8 13:09:09 carlos-desktop kernel: [   39.126142] scsi3 : sata_via
Oct  8 13:09:09 carlos-desktop kernel: [   39.128297] ata3: SATA max UDMA/133 cmd 0xe480 ctl 0xe400 bmdma 0xdc00 irq 20
Oct  8 13:09:09 carlos-desktop kernel: [   39.128303] ata4: SATA max UDMA/133 cmd 0xe080 ctl 0xe000 bmdma 0xdc08 irq 20
Oct  8 13:09:09 carlos-desktop kernel: [   39.330106] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Oct  8 13:09:09 carlos-desktop kernel: [   39.445796] usb 2-1: USB disconnect, address 2
Oct  8 13:09:09 carlos-desktop kernel: [   39.541509] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Oct  8 13:09:09 carlos-desktop kernel: [   39.564442] Driver 'sr' needs updating - please use bus_type methods
Oct  8 13:09:09 carlos-desktop kernel: [   39.567413] Driver 'sd' needs updating - please use bus_type methods
Oct  8 13:09:09 carlos-desktop kernel: [   42.101735] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Oct  8 13:09:09 carlos-desktop kernel: [   42.101746] Uniform CD-ROM driver Revision: 3.20
Oct  8 13:09:09 carlos-desktop kernel: [   39.571858] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct  8 13:09:09 carlos-desktop kernel: [   39.571883] sd 1:0:0:0: [sda] Write Protect is off
Oct  8 13:09:09 carlos-desktop kernel: [   39.571928] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  8 13:09:09 carlos-desktop kernel: [   39.572030] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct  8 13:09:09 carlos-desktop kernel: [   39.572053] sd 1:0:0:0: [sda] Write Protect is off
Oct  8 13:09:09 carlos-desktop kernel: [   39.572106] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  8 13:09:09 carlos-desktop kernel: [   39.572114]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
Oct  8 13:09:09 carlos-desktop kernel: [   39.579822] sd 1:0:0:0: Attached scsi generic sg1 type 0
Oct  8 13:09:09 carlos-desktop kernel: [   39.579865] scsi 1:0:1:0: Attached scsi generic sg2 type 0
Oct  8 13:09:09 carlos-desktop kernel: [   39.589613]  sda1 sda2 sda3 sda4
Oct  8 13:09:09 carlos-desktop kernel: [   39.589775] sd 1:0:0:0: [sda] Attached SCSI disk
Oct  8 13:09:09 carlos-desktop kernel: [   39.589899] sd 1:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Oct  8 13:09:09 carlos-desktop kernel: [   39.589921] sd 1:0:1:0: [sdb] Write Protect is off
Oct  8 13:09:09 carlos-desktop kernel: [   39.589958] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  8 13:09:09 carlos-desktop kernel: [   39.590036] sd 1:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Oct  8 13:09:09 carlos-desktop kernel: [   39.590058] sd 1:0:1:0: [sdb] Write Protect is off
Oct  8 13:09:09 carlos-desktop kernel: [   39.590100] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct  8 13:09:09 carlos-desktop kernel: [   39.590106]  sdb: sdb1
Oct  8 13:09:09 carlos-desktop kernel: [   39.624077] sd 1:0:1:0: [sdb] Attached SCSI disk
Oct  8 13:09:09 carlos-desktop kernel: [   42.351426] usb 5-3: new high speed USB device using ehci_hcd and address 2
Oct  8 13:09:09 carlos-desktop kernel: [   39.953212] usb 5-3: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   39.953359] hub 5-3:1.0: USB hub found
Oct  8 13:09:09 carlos-desktop kernel: [   39.953459] hub 5-3:1.0: 4 ports detected
Oct  8 13:09:09 carlos-desktop kernel: [   42.778458] kjournald starting.  Commit interval 5 seconds
Oct  8 13:09:09 carlos-desktop kernel: [   40.248274] EXT3-fs: mounted filesystem with ordered data mode.
Oct  8 13:09:09 carlos-desktop kernel: [   40.455062] usb 5-3.1: new high speed USB device using ehci_hcd and address 4
Oct  8 13:09:09 carlos-desktop kernel: [   40.564249] usb 5-3.1: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   40.778198] usb 5-3.2: new full speed USB device using ehci_hcd and address 5
Oct  8 13:09:09 carlos-desktop kernel: [   43.427709] usb 5-3.2: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   41.117190] usb 5-3.3: new high speed USB device using ehci_hcd and address 6
Oct  8 13:09:09 carlos-desktop kernel: [   41.226143] usb 5-3.3: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   41.226414] hub 5-3.3:1.0: USB hub found
Oct  8 13:09:09 carlos-desktop kernel: [   41.226761] hub 5-3.3:1.0: 4 ports detected
Oct  8 13:09:09 carlos-desktop kernel: [   41.543944] usb 5-3.4: new full speed USB device using ehci_hcd and address 7
Oct  8 13:09:09 carlos-desktop kernel: [   41.652533] usb 5-3.4: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   41.890928] usb 3-1: new low speed USB device using uhci_hcd and address 3
Oct  8 13:09:09 carlos-desktop kernel: [   42.069110] usb 3-1: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   42.270172] usb 5-3.3.3: new high speed USB device using ehci_hcd and address 8
Oct  8 13:09:09 carlos-desktop kernel: [   42.363392] usb 5-3.3.3: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   42.561289] usb 5-3.3.4: new high speed USB device using ehci_hcd and address 9
Oct  8 13:09:09 carlos-desktop kernel: [   42.653767] usb 5-3.3.4: configuration #1 chosen from 1 choice
Oct  8 13:09:09 carlos-desktop kernel: [   47.782894] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct  8 13:09:09 carlos-desktop kernel: [   47.842616] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct  8 13:09:09 carlos-desktop kernel: [   47.927015] gameport: EMU10K1 is pci0000:00:09.1/gameport0, io 0xe800, speed 1123kHz
Oct  8 13:09:09 carlos-desktop kernel: [   50.584602] input: PC Speaker as /devices/platform/pcspkr/input/input1
Oct  8 13:09:09 carlos-desktop kernel: [   50.672359] agpgart: Detected VIA VT3314 chipset
Oct  8 13:09:09 carlos-desktop kernel: [   50.740687] agpgart: AGP aperture is 256M @ 0xe0000000
Oct  8 13:09:09 carlos-desktop kernel: [   51.088947] input: Power Button (FF) as /devices/virtual/input/input2
Oct  8 13:09:09 carlos-desktop kernel: [   51.102970] ACPI: Power Button (FF) [PWRF]
Oct  8 13:09:09 carlos-desktop kernel: [   51.103224] input: Sleep Button (CM) as /devices/virtual/input/input3
Oct  8 13:09:09 carlos-desktop kernel: [   51.126865] ACPI: Sleep Button (CM) [SLPB]
Oct  8 13:09:09 carlos-desktop kernel: [   51.127058] input: Power Button (CM) as /devices/virtual/input/input4
Oct  8 13:09:09 carlos-desktop kernel: [   51.150802] ACPI: Power Button (CM) [PWRB]
Oct  8 13:09:09 carlos-desktop kernel: [   51.998169] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Oct  8 13:09:09 carlos-desktop kernel: [   52.092600] [fglrx]   vendor: 1002 device: 9587 count: 1
Oct  8 13:09:09 carlos-desktop kernel: [   52.092774] [fglrx] Maximum main memory to use for locked dma buffers: 1887 MBytes.
Oct  8 13:09:09 carlos-desktop kernel: [   52.093567] [fglrx] PAT is enabled successfully!
Oct  8 13:09:09 carlos-desktop kernel: [   52.093614] [fglrx] module loaded - fglrx 8.50.3 [Jun  2 2008] with 1 minors
Oct  8 13:09:09 carlos-desktop kernel: [   52.425412] PCI: Enabling device 0000:01:00.1 (0000 -> 0002)
Oct  8 13:09:09 carlos-desktop kernel: [   52.425435] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 17 (level, low) -> IRQ 17
Oct  8 13:09:09 carlos-desktop kernel: [   52.714641] usbcore: registered new interface driver hiddev
Oct  8 13:09:09 carlos-desktop kernel: [   50.256289] parport_pc 00:05: reported by Plug and Play ACPI
Oct  8 13:09:09 carlos-desktop kernel: [   50.256388] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Oct  8 13:09:09 carlos-desktop kernel: [   52.816789] input: Saitek PLC Cyborg Force Rumble Pad as /devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1:1.0/input/in
put5
Oct  8 13:09:09 carlos-desktop kernel: [   52.816845] input,hidraw0: USB HID v1.10 Joystick [Saitek PLC Cyborg Force Rumble Pad] on usb-0000:00:10.2-1
Oct  8 13:09:09 carlos-desktop kernel: [   52.816887] usbcore: registered new interface driver usbhid
Oct  8 13:09:09 carlos-desktop kernel: [   52.816893] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct  8 13:09:09 carlos-desktop kernel: [   50.290978] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1077
Oct  8 13:09:09 carlos-desktop kernel: [   50.291543] usblp1: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x03F0 pid 0x3E17
Oct  8 13:09:09 carlos-desktop kernel: [   50.291568] usbcore: registered new interface driver usblp
Oct  8 13:09:09 carlos-desktop kernel: [   52.937874] Linux video capture interface: v2.00
Oct  8 13:09:09 carlos-desktop kernel: [   52.985852] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/ov511/ov511.c: USB OV
511+ video device found
Oct  8 13:09:09 carlos-desktop kernel: [   52.986023] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/ov511/ov511.c: model:
 Lifeview RoboCam
Oct  8 13:09:09 carlos-desktop kernel: [   50.626002] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/ov511/ov511.c: Sensor
 is an OV7620
Oct  8 13:09:09 carlos-desktop kernel: [   50.689626] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/ov511/ov511.c: Device
 at usb-0000:00:10.4-3.4 registered to minor 0
Oct  8 13:09:09 carlos-desktop kernel: [   53.219916] usbcore: registered new interface driver ov511
Oct  8 13:09:09 carlos-desktop kernel: [   53.219923] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/ov511/ov511.c: v1.64 
for Linux 2.5 : ov511 USB Camera Driver
Oct  8 13:09:09 carlos-desktop kernel: [   53.237047] usbcore: registered new interface driver libusual
Oct  8 13:09:09 carlos-desktop kernel: [   53.268671] Initializing USB Mass Storage driver...
Oct  8 13:09:09 carlos-desktop kernel: [   53.284816] scsi4 : SCSI emulation for USB Mass Storage devices
Oct  8 13:09:09 carlos-desktop kernel: [   53.284942] usbcore: registered new interface driver usb-storage
Oct  8 13:09:09 carlos-desktop kernel: [   53.284947] USB Mass Storage support registered.
Oct  8 13:09:09 carlos-desktop kernel: [   50.909749] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/
hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
Oct  8 13:09:09 carlos-desktop kernel: [   53.475494] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct  8 13:09:09 carlos-desktop kernel: [   53.480129] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/
emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 EX [1005]
Oct  8 13:09:09 carlos-desktop kernel: [   53.566653] lp0: using parport0 (interrupt-driven).
Oct  8 13:09:09 carlos-desktop kernel: [   54.251706] EXT3 FS on sda3, internal journal
Oct  8 13:09:09 carlos-desktop kernel: [   55.742184] scsi 4:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB06 PQ: 0 ANSI: 0
Oct  8 13:09:09 carlos-desktop kernel: [   55.762750] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Oct  8 13:09:09 carlos-desktop kernel: [   55.762932] sr 4:0:0:0: Attached scsi generic sg3 type 5
Oct  8 13:09:09 carlos-desktop kernel: [   56.459689] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct  8 13:09:09 carlos-desktop kernel: [   56.926277] No dock devices found.
Oct  8 13:09:09 carlos-desktop kernel: [   58.426983] ppdev: user-space parallel port driver
Oct  8 13:09:10 carlos-desktop kernel: [   58.595714] audit(1223489350.151:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" 
name="/dev/tty" pid=5098 profile="/usr/sbin/cupsd" namespace="default"
Oct  8 13:09:10 carlos-desktop dhcdbd: Started up.
Oct  8 13:09:12 carlos-desktop kernel: [   63.851483] Bluetooth: Core ver 2.11
Oct  8 13:09:12 carlos-desktop kernel: [   63.852036] NET: Registered protocol family 31
Oct  8 13:09:12 carlos-desktop kernel: [   63.852041] Bluetooth: HCI device and connection manager initialized
Oct  8 13:09:12 carlos-desktop kernel: [   63.852048] Bluetooth: HCI socket layer initialized
Oct  8 13:09:13 carlos-desktop kernel: [   61.436088] Bluetooth: L2CAP ver 2.9
Oct  8 13:09:13 carlos-desktop kernel: [   61.436102] Bluetooth: L2CAP socket layer initialized
Oct  8 13:09:13 carlos-desktop kernel: [   61.501734] Bluetooth: RFCOMM socket layer initialized
Oct  8 13:09:13 carlos-desktop kernel: [   61.501781] Bluetooth: RFCOMM TTY layer initialized
Oct  8 13:09:13 carlos-desktop kernel: [   61.501788] Bluetooth: RFCOMM ver 1.8
Oct  8 13:09:13 carlos-desktop kernel: [   61.715099] Pid: 1203, comm: usplash Tainted: P   M    2.6.24-19-generic #1
Oct  8 13:09:13 carlos-desktop kernel: [   61.715104] 
Oct  8 13:09:13 carlos-desktop kernel: [   61.715105] Call Trace:
Oct  8 13:09:13 carlos-desktop kernel: [   61.715108]  <IRQ>  [__report_bad_irq+0x1e/0x80] __report_bad_irq+0x1e/0x80
Oct  8 13:09:13 carlos-desktop kernel: [   61.715176]  [note_interrupt+0x2ad/0x2e0] note_interrupt+0x2ad/0x2e0
Oct  8 13:09:13 carlos-desktop kernel: [   61.715218]  [handle_fasteoi_irq+0xa1/0x110] handle_fasteoi_irq+0xa1/0x110
Oct  8 13:09:13 carlos-desktop kernel: [   61.715247]  [do_IRQ+0x7b/0x100] do_IRQ+0x7b/0x100
Oct  8 13:09:13 carlos-desktop kernel: [   61.715288]  [ret_from_intr+0x0/0x0a] ret_from_intr+0x0/0xa
Oct  8 13:09:13 carlos-desktop kernel: [   61.715296]  <EOI> 
Oct  8 13:09:15 carlos-desktop kernel: [   66.677445] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct  8 13:09:16 carlos-desktop kernel: [   67.745450] [fglrx] AGP GART is configured for kernel IOMMU, internal GART will not be used
Oct  8 13:09:16 carlos-desktop kernel: [   67.745465] [fglrx] AGP detected, AgpState   = 0x07000a1b (hardware caps of chipset)
Oct  8 13:09:16 carlos-desktop kernel: [   67.746002] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Oct  8 13:09:16 carlos-desktop kernel: [   67.746172] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Oct  8 13:09:16 carlos-desktop kernel: [   67.746406] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Oct  8 13:09:16 carlos-desktop kernel: [   67.746551] [fglrx] AGP enabled,  AgpCommand = 0x07000312 (selected caps)
Oct  8 13:09:16 carlos-desktop kernel: [   67.746773] [fglrx] Setup AGP aperture
Oct  8 13:09:16 carlos-desktop kernel: [   65.242498] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Oct  8 13:09:16 carlos-desktop kernel: [   65.242508] [fglrx] Reserved FB block: Unshared offset:ff7a000, size:80000 
Oct  8 13:09:16 carlos-desktop kernel: [   65.242513] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
Oct  8 13:12:04 carlos-desktop kernel: [  232.190451] usb 5-3.3.2: new low speed USB device using ehci_hcd and address 10
Oct  8 13:12:04 carlos-desktop kernel: [  232.289494] usb 5-3.3.2: configuration #1 chosen from 1 choice
Oct  8 13:12:04 carlos-desktop kernel: [  232.300976] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /devices/pci0000:00/0000:00:10.4/usb5/5-3/
5-3.3/5-3.3.2/5-3.3.2:1.0/input/input6
Oct  8 13:12:04 carlos-desktop kernel: [  232.349867] input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:
00:10.4-3.3.2
Oct  8 13:12:04 carlos-desktop kernel: [  232.380892] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /devices/pci0000:00/0000:00:10.4/usb5/5-3/
5-3.3/5-3.3.2/5-3.3.2:1.1/input/input7
Oct  8 13:12:04 carlos-desktop kernel: [  232.493458] input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:
10.4-3.3.2
Oct  8 13:12:12 carlos-desktop kernel: [  240.257674] NET: Registered protocol family 10
Oct  8 13:12:12 carlos-desktop kernel: [  240.258332] lo: Disabled Privacy Extensions
Oct  8 13:13:47 carlos-desktop kernel: [  337.664735] Machine check events logged
Oct  8 13:29:09 carlos-desktop -- MARK --


And I include first case where I cannot get IP, and then after removing the ATI HD2600 how I can get the IP:

All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:04:e2:23:42:13
Sending on   LPF/eth0/00:04:e2:23:42:13
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.76 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.76 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5

carlos@carlos-desktop:~$ 


For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:04:e2:23:42:13
Sending on   LPF/eth0/00:04:e2:23:42:13
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
carlos@carlos-desktop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:04:e2:23:42:13
Sending on   LPF/eth0/00:04:e2:23:42:13
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.76 from 192.168.1.254
DHCPREQUEST of 192.168.1.76 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.76 from 192.168.1.254
bound to 192.168.1.76 -- renewal in 36269 seconds.
carlos@carlos-desktop:~$ 



Best Regards

---

### Post by nixscripter on 2008-10-11
If you unload the driver after you boot, does networking work? In other words, add **blacklist fglrx** to the end of **/etc/modules.d/blacklist**

You might not get an X server but that's okay -- I just want to know if it works from the console. Just remove the line after you're done with the test.

---

### Post by ccontrerd on 2008-10-12
All right I tried it and effectively I had a white screen when I try the graphic mode but in the shell I was able to obtain an IP address doing a ifdown - ifup commands just like in the case when I remove the graphic driver...

So right, now I'm even more sure it has to do with the graphic driver... :-)

---

### Post by nixscripter on 2008-10-13
I just noticed something. Look closely at your log:

```

Oct 8 13:09:09 carlos-desktop kernel: [ 40.033935] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
Oct 8 13:09:09 carlos-desktop kernel: [ 40.034057] PCI: Enabling device 0000:00:08.0 (0000 -> 0003)
Oct 8 13:09:09 carlos-desktop kernel: [ 40.034085] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 8 13:09:09 carlos-desktop kernel: [ 40.034773] tulip0: MII transceiver #1 config 1000 status 786d advertising 05e1.
Oct 8 13:09:09 carlos-desktop kernel: [ 40.041100] eth0: ADMtek Comet rev 17 at Port 0x1000, 00:04:e2:23:42:13, IRQ 16.

```

And:

```

Oct 8 13:09:15 carlos-desktop kernel: [ 66.677445] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 8 13:09:16 carlos-desktop kernel: [ 67.745450] [fglrx] AGP GART is configured for kernel IOMMU, internal GART will not be used
Oct 8 13:09:16 carlos-desktop kernel: [ 67.745465] [fglrx] AGP detected, AgpState = 0x07000a1b (hardware caps of chipset)
Oct 8 13:09:16 carlos-desktop kernel: [ 67.746002] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Oct 8 13:09:16 carlos-desktop kernel: [ 67.746172] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Oct 8 13:09:16 carlos-desktop kernel: [ 67.746406] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Oct 8 13:09:16 carlos-desktop kernel: [ 67.746551] [fglrx] AGP enabled, AgpCommand = 0x07000312 (selected caps)
Oct 8 13:09:16 carlos-desktop kernel: [ 67.746773] [fglrx] Setup AGP aperture
Oct 8 13:09:16 carlos-desktop kernel: [ 65.242498] [fglrx] Reserved FB block: Shared offset:0, size:1000000
Oct 8 13:09:16 carlos-desktop kernel: [ 65.242508] [fglrx] Reserved FB block: Unshared offset:ff7a000, size:80000
Oct 8 13:09:16 carlos-desktop kernel: [ 65.242513] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 


```

Both of them are trying to use interrupt line 16. Perhaps when the drivers load, one "stomps on" the other, because one (probably the graphics card) is unwilling to share the interrupt line.

Remove the line I suggested you put in earlier (the module blacklist), and then try adding the **irqpoll** flag to your kernel options, and see if that fixes the problem. Here's a temporary way to do it:

1. Reboot.
2. When it says "GRUB...Booting hit ESC for menu...2...1.." hit ESC.
3. You will get a menu of things to boot. Select the first one (should be highlighted), and type 'e'.
4. Select (with the arrow keys) the line that starts with "kernel ..." and hit 'e' again
5. At the end of the line, append **irqpoll** and hit enter.
6. Hit 'b' to boot it.

Do your both graphics card and network card work this time?

---

### Post by ccontrerd on 2008-10-19
Cool.... :-)

Seems is working both the Network Card and the ATI now...

I will edit the grub file so this is executed at the booting

Appreciate your time and help in finding the problem!

Best Regards!

---

### Post by nixscripter on 2008-10-19
Glad I could help.

Please mark this thread as solved (under the thread tools menu).

---

