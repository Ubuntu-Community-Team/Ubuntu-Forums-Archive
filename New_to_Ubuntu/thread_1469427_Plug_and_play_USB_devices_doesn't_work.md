---
title: "Plug and play USB devices doesn't work"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Night Howl on 2010-05-02
Hello,
I'm new in linux. Few days ago I decided to try Ubuntu 10.04 LTS. I have Asus F3KE AP130C (AMD Athlon X2 TK57). I have whole disk for Ubuntu, no dual boot with Windows or else distribution of Linux.
Like every new user I have lot of troubles but I can handle it, except one. I tried to google it and I also tried search on this forum. Maybe I'm looking for wrong solution, but I didn't find it.

My problem is, that usb doesn't work like plug and play. I really need to use my usb flash drive, but to load it I need to restart computer. And even if I restart it, sometimes it disappear during copying files. I tried it with more flash drives, mobile phones (connected as flash drive) and it is still the same. I tried live CD openSUSE and it was the same situation. When I used Windows it worked great.
I have also wireless mouse and keyboard and they work fine without problems (they are always connected). Also SD card can load after plug.

My *lsusb* before connect usb flash drive:

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1164:1f08 YUAN High-Tech Development Co., Ltd 
Bus 001 Device 004: ID 174f:5a35 Syntek Sonix 1.3MPixel USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```*lsusb* after connect usb flash drive:

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1164:1f08 YUAN High-Tech Development Co., Ltd 
Bus 001 Device 004: ID 174f:5a35 Syntek Sonix 1.3MPixel USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I think nothing changed. I don't know why and what I can do about that. Please help. (English is not my native language, please excuse mistakes.)

---

### Post by P4man on 2010-05-02
Thats rather strange. I assume you have tried various USB ports and disconnecting usb devices you dont need? Could you try with a powered (active) usb hub?

Also, plug the drive in, then unplug it, open a terminal and type

```
dmesg
```

copy/paste the output here, it may shed some light on the issue.

---

### Post by cloyd on 2010-05-02
Try this site: [https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)      There is a world of information there. However, the relevant part is this:

**Create the Mount Point**

 Now we need to create a mount point for the device, let's say we want to call it "external". You can call it whatever you want, just please don't use spaces in the name or it gets a little more complicated - use an underscore to separate words (like "my_external"). Create the mount point: 
sudo mkdir /media/external 
**Mount the Drive**

 [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=example.png[/IMG] We can now mount the drive. Let's say the device is /dev/sdb1, the filesystem is FAT16 or FAT32 (like it is for most USB flash drives), and we want to mount it at /media/external (having already created the mount point): 

sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137 



The options following the "-o" allow your user to have ownership of the drive, and the masks allow for extra security for file system permissions. If you don't use those extra options you *may* not be able to read and write the drive with your regular username. 
Otherwise if the device is formatted with NTFS, run: 

sudo mount -t ntfs-3g /dev/sdb1 /media/external 

End of quote. 

However you must manually unmount, and will have to give the long mount command every time you mount. However, you can write an executable script file to do this for you. That will take a lot of the pain out of it. I have to use this in UNR 9.10 to mount 90% of my devices. 

There is lots of information in the ubuntu documentation. I think I overlooked it . . . still don't use it as much as I should.

Good luck.

---

### Post by P4man on 2010-05-02
cloyd, you shouldnt have to do any of that to mount a USB drive. you just plug it in, no more. Unless you want to have manual control over mountpoint and all, but it shouldnt be necessary. Moreoever, his device is not even showing up in lsusb, so something is wrong on a lower level.

---

### Post by Night Howl on 2010-05-02
Thank you for trying help me. I know about mounting, but I'm not sure if it will help me.

I tried every usb port with different devices. But I don't own an active usb hub (I will try to borrow or to buy one, if it will be necessary).

But I did few tests and everything logged with *dmesg*. And during this process I found something new. Maybe everything is my bad. First time I started Ubuntu I had flash drive plugged. I removed it without using Safely remove hardware. I discovered there is actualy icon for my usb flash drive when I clicked on Computer in Main menu (in Gnome panel). But even if the flash drive is plugged I can't do anything with it. If I try to remove it safely I get this:

```
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:13.5/usb1/1-4)
SYNCHRONIZE CACHE: synchronize cache(10): transport: Host_status=0x07 [DID_ERROR]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: start stop unit: transport: Host_status=0x07 [DID_ERROR]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory
```

But doesnt matter if I have flash drive in port, lsusb doesn't detect it (everything is like in my first post).

DMESG logging
First attempt: I turned off computer, plugged my wireless mouse with keyboard and to another port I plugged usb flash drive. After logging to ubuntu I unplugged devices and in terminal did this:

```
dmesg > test1.txt
```

result:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic-pae (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 (Ubuntu 2.6.32-21.32-generic-pae 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff98000 (usable)
[    0.000000]  BIOS-e820: 000000007ff98000 - 000000007ffa0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffae000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ff98 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ff98000 (usable)
[    0.000000]  modified: 000000007ff98000 - 000000007ffa0000 (ACPI NVS)
[    0.000000]  modified: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[    0.000000]  modified: 000000007ffae000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 10000-16000
[    0.000000] RAMDISK: 37864000 - 37fef0ad
[    0.000000] Allocated new RAMDISK: 00938000 - 010c30ad
[    0.000000] Move RAMDISK from 0000000037864000 - 0000000037fef0ac to 00938000 - 010c30ac
[    0.000000] ACPI: RSDP 000f8db0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffa0000 00048 (v01 _ASUS_ Notebook 20071213 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffa0200 00084 (v02 121307 FACP1504 20071213 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffa0640 096EE (v01  F3K00 F3K00001 00000001 INTL 20051117)
[    0.000000] ACPI: FACS 7ffae000 00040
[    0.000000] ACPI: APIC 7ffa0390 0005C (v01 121307 APIC1504 20071213 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffa03f0 0003C (v01 121307 OEMMCFG  20071213 MSFT 00000097)
[    0.000000] ACPI: SLIC 7ffa0430 00176 (v01 _ASUS_ Notebook 20071213 MSFT 00000097)
[    0.000000] ACPI: ECDT 7ffa05e0 00054 (v01 121307 OEMECDT  20071213 MSFT 00000097)
[    0.000000] ACPI: BOOT 7ffa05b0 00028 (v01 121307 BOOT1504 20071213 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffae040 0007D (v01 121307 OEMB1504 20071213 MSFT 00000097)
[    0.000000] ACPI: HPET 7ffa9d30 00038 (v01 121307 OEMHPET  20071213 MSFT 00000097)
[    0.000000] ACPI: SSDT 7ffa9d70 0022C (v01  AMI   POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1157MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00012000 - 00018f40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000092f7d8]    TEXT DATA BSS ==> [0000100000 - 000092f7d8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000930000 - 0000937159]              BRK ==> [0000930000 - 0000937159]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000938000 - 00010c30ad]      NEW RAMDISK ==> [0000938000 - 00010c30ad]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x0007ff98
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ff98
[    0.000000] On node 0 totalpages: 524071
[    0.000000] free_area_init_node: node 0, pgdat c07d4d20, node_mem_map c10c5200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2316 pages used for memmap
[    0.000000]   HighMem zone: 294030 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:80000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c2200000 s39448 r0 d21992 u1048576
[    0.000000] pcpu-alloc: s39448 r0 d21992 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519975
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=a2dfe6c3-f09d-4dd3-aff4-4432ef0fe522 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10483360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:0007ff98)
[    0.000000] Memory: 2051548k/2096736k available (4826k kernel code, 43752k reserved, 2211k data, 672k init, 1185384k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc07e0000 - 0xc0888000   ( 672 kB)
[    0.000000]       .data : 0xc05b6a1b - 0xc07df7a8   (2211 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05b6a1b   (4826 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1894.928 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3789.85 BogoMIPS (lpj=7579712)
[    0.004025] Security Framework initialized
[    0.004045] AppArmor: AppArmor initialized
[    0.004053] Mount-cache hash table entries: 512
[    0.004179] Initializing cgroup subsys ns
[    0.004183] Initializing cgroup subsys cpuacct
[    0.004187] Initializing cgroup subsys memory
[    0.004194] Initializing cgroup subsys devices
[    0.004197] Initializing cgroup subsys freezer
[    0.004200] Initializing cgroup subsys net_cls
[    0.004218] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004221] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004224] CPU: Physical Processor ID: 0
[    0.004226] CPU: Processor Core ID: 0
[    0.004230] mce: CPU supports 5 MCE banks
[    0.004241] using C1E aware idle routine
[    0.004249] Performance Events: AMD PMU driver.
[    0.004253] ... version:                0
[    0.004255] ... bit width:              48
[    0.004257] ... generic registers:      4
[    0.004259] ... value mask:             0000ffffffffffff
[    0.004262] ... max period:             00007fffffffffff
[    0.004264] ... fixed-purpose events:   0
[    0.004266] ... event mask:             000000000000000f
[    0.004270] Checking 'hlt' instruction... OK.
[    0.022429] ACPI: Core revision 20090903
[    0.040009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040016] ftrace: allocating 22402 entries in 44 pages
[    0.044084] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044402] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.084654] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.172064] CPU1: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[    0.172090] Brought up 2 CPUs
[    0.172093] Total of 2 processors activated (7580.35 BogoMIPS).
[    0.172088] System has AMD C1E enabled
[    0.172088] Switch to broadcast mode on CPU1
[    0.172261] CPU0 attaching sched-domain:
[    0.172264]  domain 0: span 0-1 level MC
[    0.172267]   groups: 0 1
[    0.172273] CPU1 attaching sched-domain:
[    0.172275]  domain 0: span 0-1 level MC
[    0.172278]   groups: 1 0
[    0.172368] Switch to broadcast mode on CPU0
[    0.172368] devtmpfs: initialized
[    0.172368] regulator: core version 0.5
[    0.172368] Time: 13:52:13  Date: 05/02/10
[    0.172368] NET: Registered protocol family 16
[    0.172368] Trying to unpack rootfs image as initramfs...
[    0.172368] EISA bus registered
[    0.172368] ACPI: bus type pci registered
[    0.172368] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.172368] PCI: Not using MMCONFIG.
[    0.173048] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=8
[    0.173050] PCI: Using configuration type 1 for base access
[    0.176129] bio: create slab <bio-0> at 0
[    0.177285] ACPI: EC: EC description table is found, configuring boot EC
[    0.178661] ACPI: Executed 3 blocks of module-level executable AML code
[    0.190722] ACPI: Interpreter enabled
[    0.190731] ACPI: (supports S0 S3 S4 S5)
[    0.190760] ACPI: Using IOAPIC for interrupt routing
[    0.191064] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.194594] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.194597] PCI: Using MMCONFIG for extended config space
[    0.203332] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.203643] ACPI: No dock devices found.
[    0.203825] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.203914] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.203918] pci 0000:00:02.0: PME# disabled
[    0.203956] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.203959] pci 0000:00:04.0: PME# disabled
[    0.203995] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.204006] pci 0000:00:05.0: PME# disabled
[    0.204042] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.204045] pci 0000:00:06.0: PME# disabled
[    0.204080] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.204084] pci 0000:00:07.0: PME# disabled
[    0.204136] pci 0000:00:12.0: reg 10 io port: [0xb000-0xb007]
[    0.204144] pci 0000:00:12.0: reg 14 io port: [0xa000-0xa003]
[    0.204152] pci 0000:00:12.0: reg 18 io port: [0x9000-0x9007]
[    0.204160] pci 0000:00:12.0: reg 1c io port: [0x8000-0x8003]
[    0.204168] pci 0000:00:12.0: reg 20 io port: [0x7000-0x700f]
[    0.204176] pci 0000:00:12.0: reg 24 32bit mmio: [0xfdeff800-0xfdeffbff]
[    0.204196] pci 0000:00:12.0: set SATA to AHCI mode
[    0.204238] pci 0000:00:13.0: reg 10 32bit mmio: [0xfdefe000-0xfdefefff]
[    0.204298] pci 0000:00:13.1: reg 10 32bit mmio: [0xfdefd000-0xfdefdfff]
[    0.204358] pci 0000:00:13.2: reg 10 32bit mmio: [0xfdefc000-0xfdefcfff]
[    0.204418] pci 0000:00:13.3: reg 10 32bit mmio: [0xfdefb000-0xfdefbfff]
[    0.204478] pci 0000:00:13.4: reg 10 32bit mmio: [0xfdefa000-0xfdefafff]
[    0.204556] pci 0000:00:13.5: reg 10 32bit mmio: [0xfdeff000-0xfdeff0ff]
[    0.204613] pci 0000:00:13.5: supports D1 D2
[    0.204615] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.204620] pci 0000:00:13.5: PME# disabled
[    0.204672] pci 0000:00:14.0: reg 10 io port: [0xb00-0xb0f]
[    0.204745] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.204753] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.204760] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.204768] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.204776] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.204833] pci 0000:00:14.2: reg 10 64bit mmio: [0xfdef4000-0xfdef7fff]
[    0.204880] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.204884] pci 0000:00:14.2: PME# disabled
[    0.205089] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.205096] pci 0000:01:00.0: reg 14 io port: [0xc000-0xc0ff]
[    0.205102] pci 0000:01:00.0: reg 18 32bit mmio: [0xfdff0000-0xfdffffff]
[    0.205118] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfdfc0000-0xfdfdffff]
[    0.205137] pci 0000:01:00.0: supports D1 D2
[    0.205191] pci 0000:00:02.0: bridge io port: [0xc000-0xcfff]
[    0.205195] pci 0000:00:02.0: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.205200] pci 0000:00:02.0: bridge 64bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.205250] pci 0000:00:04.0: bridge io port: [0xd000-0xdfff]
[    0.205253] pci 0000:00:04.0: bridge 32bit mmio: [0xfe000000-0xfe8fffff]
[    0.205258] pci 0000:00:04.0: bridge 64bit mmio pref: [0xfa000000-0xfcffffff]
[    0.205355] pci 0000:06:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.205375] pci 0000:06:00.0: reg 18 64bit mmio: [0xfe9ff000-0xfe9fffff]
[    0.205394] pci 0000:06:00.0: reg 30 32bit mmio pref: [0xfe9e0000-0xfe9effff]
[    0.205433] pci 0000:06:00.0: supports D1 D2
[    0.205436] pci 0000:06:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.205441] pci 0000:06:00.0: PME# disabled
[    0.205504] pci 0000:00:06.0: bridge io port: [0xe000-0xefff]
[    0.205507] pci 0000:00:06.0: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.205552] pci 0000:07:00.0: reg 10 64bit mmio: [0xfeaf0000-0xfeafffff]
[    0.205605] pci 0000:07:00.0: supports D1
[    0.205607] pci 0000:07:00.0: PME# supported from D0 D1 D3hot
[    0.205612] pci 0000:07:00.0: PME# disabled
[    0.205674] pci 0000:00:07.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.205723] pci 0000:08:01.0: reg 10 32bit mmio: [0xfebff800-0xfebfffff]
[    0.205788] pci 0000:08:01.0: PME# supported from D0 D3hot D3cold
[    0.205793] pci 0000:08:01.0: PME# disabled
[    0.205839] pci 0000:08:01.1: reg 10 32bit mmio: [0xfebff400-0xfebff4ff]
[    0.205903] pci 0000:08:01.1: supports D1 D2
[    0.205906] pci 0000:08:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205912] pci 0000:08:01.1: PME# disabled
[    0.205957] pci 0000:08:01.2: reg 10 32bit mmio: [0xfebff000-0xfebff0ff]
[    0.206022] pci 0000:08:01.2: supports D1 D2
[    0.206024] pci 0000:08:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206030] pci 0000:08:01.2: PME# disabled
[    0.206075] pci 0000:08:01.3: reg 10 32bit mmio: [0xfebfec00-0xfebfecff]
[    0.206140] pci 0000:08:01.3: supports D1 D2
[    0.206142] pci 0000:08:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206148] pci 0000:08:01.3: PME# disabled
[    0.206213] pci 0000:00:14.4: transparent bridge
[    0.206221] pci 0000:00:14.4: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.206241] pci_bus 0000:00: on NUMA node 0
[    0.206249] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.206516] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.215379] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.215533] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 *15)
[    0.215682] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.215828] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.215975] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.216130] ACPI: PCI Interrupt Link [LNKF] (IRQs *9)
[    0.216273] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.216420] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.216570] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.216576] vgaarb: loaded
[    0.216696] SCSI subsystem initialized
[    0.216806] libata version 3.00 loaded.
[    0.216880] usbcore: registered new interface driver usbfs
[    0.216894] usbcore: registered new interface driver hub
[    0.216920] usbcore: registered new device driver usb
[    0.217076] ACPI: WMI: Mapper loaded
[    0.217079] PCI: Using ACPI for IRQ routing
[    0.217334] NetLabel: Initializing
[    0.217337] NetLabel:  domain hash size = 128
[    0.217338] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.217353] NetLabel:  unlabeled traffic allowed by default
[    0.217400] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.217407] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.219417] Switching to clocksource hpet
[    0.219527] AppArmor: AppArmor Filesystem Enabled
[    0.219527] pnp: PnP ACPI init
[    0.219527] ACPI: bus type pnp registered
[    0.220917] pnp: PnP ACPI: found 13 devices
[    0.220920] ACPI: ACPI bus type pnp unregistered
[    0.220924] PnPBIOS: Disabled by ACPI PNP
[    0.220941] system 00:06: ioport range 0x250-0x253 has been reserved
[    0.220944] system 00:06: ioport range 0x256-0x25f has been reserved
[    0.220949] system 00:06: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.220953] system 00:06: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.220963] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.220967] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.220971] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.220974] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.220978] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.220981] system 00:08: ioport range 0xc50-0xc51 has been reserved
[    0.220985] system 00:08: ioport range 0xc52-0xc52 has been reserved
[    0.220988] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.220992] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.220996] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.220999] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.221003] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.221006] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.221010] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.221013] system 00:08: ioport range 0x800-0x89f has been reserved
[    0.221017] system 00:08: ioport range 0xb10-0xb1f has been reserved
[    0.221021] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.221024] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.221028] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[    0.221032] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.221036] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.221044] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.221050] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.221054] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.221057] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.221061] system 00:0c: iomem range 0x100000-0x7fffffff could not be reserved
[    0.221065] system 00:0c: iomem range 0xe0000000-0xffffffff could not be reserved
[    0.255800] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.255804] pci 0000:00:02.0:   IO window: 0xc000-0xcfff
[    0.255808] pci 0000:00:02.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.255812] pci 0000:00:02.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.255817] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.255820] pci 0000:00:04.0:   IO window: 0xd000-0xdfff
[    0.255824] pci 0000:00:04.0:   MEM window: 0xfe000000-0xfe8fffff
[    0.255827] pci 0000:00:04.0:   PREFETCH window: 0x000000fa000000-0x000000fcffffff
[    0.255832] pci 0000:00:05.0: PCI bridge, secondary bus 0000:05
[    0.255834] pci 0000:00:05.0:   IO window: disabled
[    0.255837] pci 0000:00:05.0:   MEM window: disabled
[    0.255840] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.255845] pci 0000:00:06.0: PCI bridge, secondary bus 0000:06
[    0.255848] pci 0000:00:06.0:   IO window: 0xe000-0xefff
[    0.255852] pci 0000:00:06.0:   MEM window: 0xfe900000-0xfe9fffff
[    0.255855] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.255859] pci 0000:00:07.0: PCI bridge, secondary bus 0000:07
[    0.255861] pci 0000:00:07.0:   IO window: disabled
[    0.255865] pci 0000:00:07.0:   MEM window: 0xfea00000-0xfeafffff
[    0.255868] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.255872] pci 0000:00:14.4: PCI bridge, secondary bus 0000:08
[    0.255875] pci 0000:00:14.4:   IO window: disabled
[    0.255881] pci 0000:00:14.4:   MEM window: 0xfeb00000-0xfebfffff
[    0.255885] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.255900] pci 0000:00:02.0: setting latency timer to 64
[    0.255907] pci 0000:00:04.0: setting latency timer to 64
[    0.255913] pci 0000:00:05.0: setting latency timer to 64
[    0.255919] pci 0000:00:06.0: setting latency timer to 64
[    0.255924] pci 0000:00:07.0: setting latency timer to 64
[    0.255934] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.255937] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.255940] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.255943] pci_bus 0000:01: resource 1 mem: [0xfdf00000-0xfdffffff]
[    0.255947] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]
[    0.255950] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.255953] pci_bus 0000:02: resource 1 mem: [0xfe000000-0xfe8fffff]
[    0.255956] pci_bus 0000:02: resource 2 pref mem [0xfa000000-0xfcffffff]
[    0.255959] pci_bus 0000:06: resource 0 io:  [0xe000-0xefff]
[    0.255962] pci_bus 0000:06: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.255966] pci_bus 0000:07: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.255969] pci_bus 0000:08: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.255972] pci_bus 0000:08: resource 3 io:  [0x00-0xffff]
[    0.255975] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.256025] NET: Registered protocol family 2
[    0.256126] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.256489] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.257112] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.257412] TCP: Hash tables configured (established 131072 bind 65536)
[    0.257415] TCP reno registered
[    0.257518] NET: Registered protocol family 1
[    0.352051] pci 0000:01:00.0: Boot video device
[    0.352088] Simple Boot Flag at 0x52 set to 0x1
[    0.352288] cpufreq-nforce2: No nForce2 chipset.
[    0.352316] Scanning for low memory corruption every 60 seconds
[    0.352428] audit: initializing netlink socket (disabled)
[    0.352440] type=2000 audit(1272808332.349:1): initialized
[    0.363594] highmem bounce pool size: 64 pages
[    0.363600] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.365246] VFS: Disk quotas dquot_6.5.2
[    0.365311] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.365956] fuse init (API version 7.13)
[    0.366052] msgmni has been set to 1693
[    0.366288] alg: No test for stdrng (krng)
[    0.366352] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.366355] io scheduler noop registered
[    0.366357] io scheduler anticipatory registered
[    0.366360] io scheduler deadline registered
[    0.366408] io scheduler cfq registered (default)
[    0.366572]   alloc irq_desc for 24 on node -1
[    0.366574]   alloc kstat_irqs on node -1
[    0.366584] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.366590] pcieport 0000:00:02.0: setting latency timer to 64
[    0.366670]   alloc irq_desc for 25 on node -1
[    0.366672]   alloc kstat_irqs on node -1
[    0.366677] pcieport 0000:00:04.0: irq 25 for MSI/MSI-X
[    0.366682] pcieport 0000:00:04.0: setting latency timer to 64
[    0.366765]   alloc irq_desc for 26 on node -1
[    0.366767]   alloc kstat_irqs on node -1
[    0.366772] pcieport 0000:00:05.0: irq 26 for MSI/MSI-X
[    0.366777] pcieport 0000:00:05.0: setting latency timer to 64
[    0.366854]   alloc irq_desc for 27 on node -1
[    0.366856]   alloc kstat_irqs on node -1
[    0.366861] pcieport 0000:00:06.0: irq 27 for MSI/MSI-X
[    0.366866] pcieport 0000:00:06.0: setting latency timer to 64
[    0.366944]   alloc irq_desc for 28 on node -1
[    0.366946]   alloc kstat_irqs on node -1
[    0.366951] pcieport 0000:00:07.0: irq 28 for MSI/MSI-X
[    0.366956] pcieport 0000:00:07.0: setting latency timer to 64
[    0.367024] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.367105] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.367299] ACPI: AC Adapter [AC0] (on-line)
[    0.367385] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.367389] ACPI: Power Button [PWRB]
[    0.367440] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.367448] ACPI: Sleep Button [SLPB]
[    0.367496] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.369391] ACPI: Lid Switch [LID]
[    0.369447] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.369450] ACPI: Power Button [PWRF]
[    0.369945] ACPI: processor limited to max C-state 1
[    0.369974] processor LNXCPU:00: registered as cooling_device0
[    0.370012] processor LNXCPU:01: registered as cooling_device1
[    0.375542] thermal LNXTHERM:01: registered as thermal_zone0
[    0.375551] ACPI: Thermal Zone [THRM] (69 C)
[    0.377420] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.378909] brd: module loaded
[    0.379456] loop: module loaded
[    0.379582] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.379795]   alloc irq_desc for 16 on node -1
[    0.379798]   alloc kstat_irqs on node -1
[    0.379805] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.379848] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.380235] Fixed MDIO Bus: probed
[    0.380275] PPP generic driver version 2.4.2
[    0.380328] tun: Universal TUN/TAP device driver, 1.6
[    0.380330] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.380434] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.380455]   alloc irq_desc for 19 on node -1
[    0.380458]   alloc kstat_irqs on node -1
[    0.380463] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.380484] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.380529] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.380558] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.380574] ehci_hcd 0000:00:13.5: debug port 1
[    0.380598] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfdeff000
[    0.380970] isapnp: Scanning for PnP cards...
[    0.430346] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.430462] usb usb1: configuration #1 chosen from 1 choice
[    0.430495] hub 1-0:1.0: USB hub found
[    0.430505] hub 1-0:1.0: 10 ports detected
[    0.430593] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.430614] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.430636] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.430676] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.430704] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfdefe000
[    0.463829] Freeing initrd memory: 7724k freed
[    0.475250] ACPI: Battery Slot [BAT0] (battery present)
[    0.497155] usb usb2: configuration #1 chosen from 1 choice
[    0.497189] hub 2-0:1.0: USB hub found
[    0.497202] hub 2-0:1.0: 2 ports detected
[    0.497267]   alloc irq_desc for 17 on node -1
[    0.497269]   alloc kstat_irqs on node -1
[    0.497277] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.497297] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.497337] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.497369] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfdefd000
[    0.557086] usb usb3: configuration #1 chosen from 1 choice
[    0.557114] hub 3-0:1.0: USB hub found
[    0.557125] hub 3-0:1.0: 2 ports detected
[    0.557175]   alloc irq_desc for 18 on node -1
[    0.557178]   alloc kstat_irqs on node -1
[    0.557182] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.557194] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.557234] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.557257] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfdefc000
[    0.652749] usb usb4: configuration #1 chosen from 1 choice
[    0.652779] hub 4-0:1.0: USB hub found
[    0.652790] hub 4-0:1.0: 2 ports detected
[    0.652842] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.652855] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    0.652892] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    0.652910] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfdefb000
[    0.709087] usb usb5: configuration #1 chosen from 1 choice
[    0.709118] hub 5-0:1.0: USB hub found
[    0.709129] hub 5-0:1.0: 2 ports detected
[    0.709177] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.709190] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    0.709227] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    0.709243] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfdefa000
[    0.740059] isapnp: No Plug & Play device found
[    0.768146] usb usb6: configuration #1 chosen from 1 choice
[    0.768184] hub 6-0:1.0: USB hub found
[    0.768197] hub 6-0:1.0: 2 ports detected
[    0.768261] uhci_hcd: USB Universal Host Controller Interface driver
[    0.768355] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.770215] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.772260] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.772269] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.772304] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.772329] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.772355] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.772500] mice: PS/2 mouse device common for all mice
[    0.772677] rtc_cmos 00:02: RTC can wake from S4
[    0.772726] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.772756] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.772876] device-mapper: uevent: version 1.0.3
[    0.773015] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.773139] device-mapper: multipath: version 1.1.0 loaded
[    0.773142] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.773291] EISA: Probing bus 0 at eisa.0
[    0.773325] Cannot allocate resource for EISA slot 7
[    0.773328] Cannot allocate resource for EISA slot 8
[    0.773330] EISA: Detected 0 cards.
[    0.773473] cpuidle: using governor ladder
[    0.773476] cpuidle: using governor menu
[    0.773983] TCP cubic registered
[    0.774148] NET: Registered protocol family 10
[    0.774665] lo: Disabled Privacy Extensions
[    0.775029] NET: Registered protocol family 17
[    0.775070] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 processors (2 cpu cores) (version 2.20.00)
[    0.775122] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x13
[    0.775125] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x14
[    0.775127] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x15
[    0.775130] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1a
[    0.775180] Using IPI No-Shortcut mode
[    0.775282] PM: Resume from disk failed.
[    0.775299] registered taskstats version 1
[    0.775727]   Magic number: 10:858:886
[    0.775836] rtc_cmos 00:02: setting system clock to 2010-05-02 13:52:13 UTC (1272808333)
[    0.775839] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.775841] EDD information not available.
[    0.775897] Freeing unused kernel memory: 672k freed
[    0.776428] Write protecting the kernel text: 4828k
[    0.776505] Write protecting the kernel read-only data: 1876k
[    0.800622] udev: starting version 151
[    0.805324] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.853217] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    0.962558] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.962585] r8169 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.962632] r8169 0000:06:00.0: setting latency timer to 64
[    0.962682]   alloc irq_desc for 29 on node -1
[    0.962685]   alloc kstat_irqs on node -1
[    0.962699] r8169 0000:06:00.0: irq 29 for MSI/MSI-X
[    0.963400] eth0: RTL8168b/8111b at 0xf82c6000, 00:1d:60:07:8c:25, XID 18000000 IRQ 29
[    0.984577] scsi0 : pata_atiixp
[    0.984803] scsi1 : pata_atiixp
[    0.986169] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    0.986173] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    0.986339] ahci 0000:00:12.0: version 3.0
[    0.986357]   alloc irq_desc for 22 on node -1
[    0.986360]   alloc kstat_irqs on node -1
[    0.986368] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.986408] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    0.986524] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.986528] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    0.987170] scsi2 : ahci
[    0.987389] scsi3 : ahci
[    0.987497] scsi4 : ahci
[    0.987620] scsi5 : ahci
[    0.987776] ata3: SATA max UDMA/133 abar m1024@0xfdeff800 port 0xfdeff900 irq 22
[    0.987781] ata4: SATA max UDMA/133 abar m1024@0xfdeff800 port 0xfdeff980 irq 22
[    0.987785] ata5: SATA max UDMA/133 abar m1024@0xfdeff800 port 0xfdeffa00 irq 22
[    0.987790] ata6: SATA max UDMA/133 abar m1024@0xfdeff800 port 0xfdeffa80 irq 22
[    0.988309]   alloc irq_desc for 20 on node -1
[    0.988313]   alloc kstat_irqs on node -1
[    0.988322] ohci1394 0000:08:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.988819] usb 1-4: configuration #1 chosen from 1 choice
[    0.998213] Initializing USB Mass Storage driver...
[    0.998363] scsi6 : SCSI emulation for USB Mass Storage devices
[    0.998471] usbcore: registered new interface driver usb-storage
[    0.998474] USB Mass Storage support registered.
[    0.998481] usb-storage: device found at 3
[    0.998483] usb-storage: waiting for device to settle before scanning
[    1.046101] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.100059] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    1.164531] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632H, AS02, max UDMA/33
[    1.196484] ata1.00: configured for UDMA/33
[    1.201005] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  AS02 PQ: 0 ANSI: 5
[    1.215342] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.215346] Uniform CD-ROM driver Revision: 3.20
[    1.215483] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.215569] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.241956] usb 1-6: configuration #1 chosen from 1 choice
[    1.308072] ata4: SATA link down (SStatus 0 SControl 300)
[    1.308107] ata5: SATA link down (SStatus 0 SControl 300)
[    1.308158] ata6: SATA link down (SStatus 0 SControl 300)
[    1.352057] usb 1-10: new high speed USB device using ehci_hcd and address 5
[    1.472030] ata3: softreset failed (device not ready)
[    1.472034] ata3: applying SB600 PMP SRST workaround and retrying
[    1.485895] usb 1-10: configuration #1 chosen from 1 choice
[    1.638021] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.638739] ata3.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
[    1.638743] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.638765] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.639662] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.639665] ata3.00: configured for UDMA/133
[    1.652184] scsi 2:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    1.652388] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.652424] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.652568] sd 2:0:0:0: [sda] Write Protect is off
[    1.652572] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.652600] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.652778]  sda: sda1 sda2 sda3
[    1.669496] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.748060] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    1.900840] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    1.920808] usb 2-2: configuration #1 chosen from 1 choice
[    2.320319] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800039d4559]
[    5.996207] usb-storage: device scan complete
[    5.996920] scsi 6:0:0:0: Direct-Access     Corsair  Voyager Mini     0.00 PQ: 0 ANSI: 2
[    5.997567] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    5.998264] sd 6:0:0:0: [sdb] 15771720 512-byte logical blocks: (8.07 GB/7.52 GiB)
[    5.998758] sd 6:0:0:0: [sdb] Write Protect is off
[    5.998762] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[    5.998766] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.001384] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.001388]  sdb:
[    6.292429] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.292434] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    9.789863] Adding 3996664k swap on /dev/sda1.  Priority:-1 extents:1 across:3996664k 
[    9.796742] udev: starting version 151
[    9.965628] Linux agpgart interface v0.103
[    9.966312] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   10.046576] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   10.048995] asus_laptop: Asus Laptop Support version 0.42
[   10.106319] lp: driver loaded but no devices found
[   10.115010] asus_laptop:   F3Ke model detected
[   10.134745] input: Asus Laptop extra buttons as /devices/virtual/input/input6
[   10.163366] cfg80211: Calling CRDA to update world regulatory domain
[   10.171085] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   10.191705] sdhci: Secure Digital Host Controller Interface driver
[   10.191709] sdhci: Copyright(c) Pierre Ossman
[   10.191950] acpi device:26: registered as cooling_device2
[   10.192383] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:22/LNXVIDEO:01/input/input7
[   10.192489] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[   10.193555] [drm] Initialized drm 1.1.0 20060810
[   10.198701] sdhci-pci 0000:08:01.1: SDHCI controller found [1180:0822] (rev 22)
[   10.198726]   alloc irq_desc for 21 on node -1
[   10.198729]   alloc kstat_irqs on node -1
[   10.198739] sdhci-pci 0000:08:01.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   10.199777] sdhci-pci 0000:08:01.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   10.202046] Registered led device: mmc0::
[   10.203086] mmc0: SDHCI controller on PCI [0000:08:01.1] using DMA
[   10.213945] Linux video capture interface: v2.00
[   10.225905] cfg80211: World regulatory domain updated:
[   10.225910] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.225914] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.225917] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.225920] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.225923] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.225926] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.276643] type=1505 audit(1272808342.997:2):  operation="profile_load" pid=684 name="/sbin/dhclient3"
[   10.276941] type=1505 audit(1272808342.997:3):  operation="profile_load" pid=684 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.277110] type=1505 audit(1272808342.997:4):  operation="profile_load" pid=684 name="/usr/lib/connman/scripts/dhclient-script"
[   10.313068] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.313080] ath9k 0000:07:00.0: setting latency timer to 64
[   10.328791] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (174f:5a35)
[   10.339847] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/input/input8
[   10.340050] usbcore: registered new interface driver uvcvideo
[   10.340355] USB Video Class driver (v0.1.0)
[   10.351438] usbcore: registered new interface driver hiddev
[   10.351556] usbcore: registered new interface driver usbhid
[   10.351559] usbhid: v2.6:USB HID core driver
[   10.366049] dib0700: loaded with support for 13 different device-types
[   10.368683] dvb-usb: found a 'YUAN High-Tech STK7700PH' in warm state.
[   10.369180] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.369972] DVB: registering new adapter (YUAN High-Tech STK7700PH)
[   10.419330] [drm] radeon defaulting to kernel modesetting.
[   10.419336] [drm] radeon kernel modesetting enabled.
[   10.419428] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.419434] radeon 0000:01:00.0: setting latency timer to 64
[   10.421423] [drm] radeon: Initializing kernel modesetting.
[   10.421534] [drm] register mmio base: 0xFDFF0000
[   10.421537] [drm] register mmio size: 65536
[   10.422741] ATOM BIOS: Asus
[   10.422966] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[   10.422989] [drm] Generation 2 PCI interface, using max accessible memory
[   10.422993] [drm] radeon: VRAM 128M
[   10.422995] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   10.422998] [drm] radeon: GTT 512M
[   10.423000] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   10.423047]   alloc irq_desc for 30 on node -1
[   10.423050]   alloc kstat_irqs on node -1
[   10.423062] radeon 0000:01:00.0: irq 30 for MSI/MSI-X
[   10.423069] [drm] radeon: using MSI.
[   10.423097] [drm] radeon: irq initialized.
[   10.423246] [drm] Detected VRAM RAM=128M, BAR=128M
[   10.423252] [drm] RAM width 64bits DDR
[   10.423345] [TTM] Zone  kernel: Available graphics memory: 437774 kiB.
[   10.423347] [TTM] Zone highmem: Available graphics memory: 1030466 kiB.
[   10.423370] [drm] radeon: 128M of VRAM memory ready
[   10.423372] [drm] radeon: 512M of GTT memory ready.
[   10.423392] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   10.426608] [drm] RB2D reset succeed (RBBM_STATUS=0x10000140)
[   10.426628] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   10.426696] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   10.426716] [drm] radeon: cp idle (0x10000C03)
[   10.428519] [drm] Loading R500 Microcode
[   10.428835] platform radeon_cp.0: firmware: requesting radeon/R520_cp.bin
[   10.432447] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input9
[   10.432555] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.0-2/input0
[   10.434857] [drm] radeon: ring at 0x0000000020000000
[   10.434892] [drm] ring test succeeded in 7 usecs
[   10.435071] [drm] radeon: ib pool ready.
[   10.435627] [drm] ib test succeeded in 0 usecs
[   10.435820] [drm] Default TV standard: PAL
[   10.435892] [drm] Radeon Display Connectors
[   10.435894] [drm] Connector 0:
[   10.435895] [drm]   VGA
[   10.435898] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   10.435901] [drm]   Encoders:
[   10.435903] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   10.435905] [drm] Connector 1:
[   10.435906] [drm]   LVDS
[   10.435909] [drm]   DDC: 0xc54 0xc54 0xc58 0xc58 0xc5c 0xc5c 0xc60 0xc60
[   10.435911] [drm]   Encoders:
[   10.435912] [drm]     LCD1: INTERNAL_LVTM1
[   10.435914] [drm] Connector 2:
[   10.435916] [drm]   S-video
[   10.435917] [drm]   Encoders:
[   10.435919] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   10.435921] [drm] Connector 3:
[   10.435922] [drm]   DVI-I
[   10.435924] [drm]   HPD1
[   10.435926] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   10.435928] [drm]   Encoders:
[   10.435930] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[   10.440113] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[   10.441147] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.1/input/input10
[   10.441348] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-2/input1
[   10.572022] ath: EEPROM regdomain: 0x60
[   10.572026] ath: EEPROM indicates we should expect a direct regpair map
[   10.572031] ath: Country alpha2 being used: 00
[   10.572034] ath: Regpair used: 0x60
[   10.632155] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.633086] Registered led device: ath9k-phy0::radio
[   10.633109] Registered led device: ath9k-phy0::assoc
[   10.633132] Registered led device: ath9k-phy0::tx
[   10.633160] Registered led device: ath9k-phy0::rx
[   10.633172] phy0: Atheros AR5418 MAC/BB Rev:2 AR5133 RF Rev:81: mem=0xf8600000, irq=19
[   10.657497] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   10.665512] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.670394] xc2028 5-0061: creating new instance
[   10.670399] xc2028 5-0061: type set to XCeive xc2028/xc3028 tuner
[   10.670508] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb1/1-10/input/input11
[   10.670582] dvb-usb: schedule remote query interval to 50 msecs.
[   10.670587] dvb-usb: YUAN High-Tech STK7700PH successfully initialized and connected.
[   10.670880] usbcore: registered new interface driver dvb_usb_dib0700
[   10.727026] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input12
[   10.746125] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input13
[   10.777364] hda_codec: ALC660-VD: BIOS auto-probing.
[   10.778126] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input14
[   10.904014] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   11.085639] [drm] fb mappable at 0xF00C0000
[   11.085643] [drm] vram apper at 0xF0000000
[   11.085646] [drm] size 5299200
[   11.085648] [drm] fb depth is 24
[   11.085650] [drm]    pitch is 5888
[   11.085894] fb0: radeondrmfb frame buffer device
[   11.085897] registered panic notifier
[   11.085904] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   11.089503] vga16fb: initializing
[   11.089510] vga16fb: mapped to 0xc00a0000
[   11.089516] vga16fb: not registering due to another framebuffer present
[   11.441977] Console: switching to colour frame buffer device 160x50
[   11.628426] r8169: eth0: link up
[   11.628434] r8169: eth0: link up
[   21.772052] eth0: no IPv6 routers present
[   78.717508] usb 1-4: USB disconnect, address 3
[   84.394272] usb 2-2: USB disconnect, address 2
```

I hope it s whole output. In the moment before I unplugged flash drive, mouse and keyboard my lsusb was:

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1164:1f08 YUAN High-Tech Development Co., Ltd 
Bus 001 Device 004: ID 174f:5a35 Syntek Sonix 1.3MPixel USB 2.0 Camera
Bus 001 Device 003: ID 1b1c:0b29  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The second attempt: Every device is unplugged. Restart computer. After restart I plugged usb flash drive. In Computer from Main menu there is an icon. lsusb no change. After trying safely remove there is an error (same as before). I unplugged device and did dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic-pae (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 (Ubuntu 2.6.32-21.32-generic-pae 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff98000 (usable)
[    0.000000]  BIOS-e820: 000000007ff98000 - 000000007ffa0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffae000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ff98 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ff98000 (usable)
[    0.000000]  modified: 000000007ff98000 - 000000007ffa0000 (ACPI NVS)
[    0.000000]  modified: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[    0.000000]  modified: 000000007ffae000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 10000-16000
[    0.000000] RAMDISK: 37864000 - 37fef0ad
[    0.000000] Allocated new RAMDISK: 00938000 - 010c30ad
[    0.000000] Move RAMDISK from 0000000037864000 - 0000000037fef0ac to 00938000 - 010c30ac
[    0.000000] ACPI: RSDP 000f8db0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffa0000 00048 (v01 _ASUS_ Notebook 20071213 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffa0200 00084 (v02 121307 FACP1504 20071213 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffa0640 096EE (v01  F3K00 F3K00001 00000001 INTL 20051117)
[    0.000000] ACPI: FACS 7ffae000 00040
[    0.000000] ACPI: APIC 7ffa0390 0005C (v01 121307 APIC1504 20071213 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffa03f0 0003C (v01 121307 OEMMCFG  20071213 MSFT 00000097)
[    0.000000] ACPI: SLIC 7ffa0430 00176 (v01 _ASUS_ Notebook 20071213 MSFT 00000097)
[    0.000000] ACPI: ECDT 7ffa05e0 00054 (v01 121307 OEMECDT  20071213 MSFT 00000097)
[    0.000000] ACPI: BOOT 7ffa05b0 00028 (v01 121307 BOOT1504 20071213 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffae040 0007D (v01 121307 OEMB1504 20071213 MSFT 00000097)
[    0.000000] ACPI: HPET 7ffa9d30 00038 (v01 121307 OEMHPET  20071213 MSFT 00000097)
[    0.000000] ACPI: SSDT 7ffa9d70 0022C (v01  AMI   POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1157MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00012000 - 00018f40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000092f7d8]    TEXT DATA BSS ==> [0000100000 - 000092f7d8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000930000 - 0000937159]              BRK ==> [0000930000 - 0000937159]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000938000 - 00010c30ad]      NEW RAMDISK ==> [0000938000 - 00010c30ad]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x0007ff98
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ff98
[    0.000000] On node 0 totalpages: 524071
[    0.000000] free_area_init_node: node 0, pgdat c07d4d20, node_mem_map c10c5200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2316 pages used for memmap
[    0.000000]   HighMem zone: 294030 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:80000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c2200000 s39448 r0 d21992 u1048576
[    0.000000] pcpu-alloc: s39448 r0 d21992 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519975
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=a2dfe6c3-f09d-4dd3-aff4-4432ef0fe522 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10483360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:0007ff98)
[    0.000000] Memory: 2051548k/2096736k available (4826k kernel code, 43752k reserved, 2211k data, 672k init, 1185384k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc07e0000 - 0xc0888000   ( 672 kB)
[    0.000000]       .data : 0xc05b6a1b - 0xc07df7a8   (2211 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05b6a1b   (4826 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using HPET reference calibration
[    0.000000] Detected 1895.089 MHz processor.
[    0.016006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3790.17 BogoMIPS (lpj=7580356)
[    0.016026] Security Framework initialized
[    0.016046] AppArmor: AppArmor initialized
[    0.016054] Mount-cache hash table entries: 512
[    0.016179] Initializing cgroup subsys ns
[    0.016183] Initializing cgroup subsys cpuacct
[    0.016188] Initializing cgroup subsys memory
[    0.016195] Initializing cgroup subsys devices
[    0.016197] Initializing cgroup subsys freezer
[    0.016200] Initializing cgroup subsys net_cls
[    0.016218] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.016221] CPU: L2 Cache: 256K (64 bytes/line)
[    0.016224] CPU: Physical Processor ID: 0
[    0.016226] CPU: Processor Core ID: 0
[    0.016230] mce: CPU supports 5 MCE banks
[    0.016242] using C1E aware idle routine
[    0.016250] Performance Events: AMD PMU driver.
[    0.016254] ... version:                0
[    0.016256] ... bit width:              48
[    0.016258] ... generic registers:      4
[    0.016260] ... value mask:             0000ffffffffffff
[    0.016262] ... max period:             00007fffffffffff
[    0.016265] ... fixed-purpose events:   0
[    0.016267] ... event mask:             000000000000000f
[    0.016271] Checking 'hlt' instruction... OK.
[    0.034428] ACPI: Core revision 20090903
[    0.052009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.052016] ftrace: allocating 22402 entries in 44 pages
[    0.056084] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.056405] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.096994] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[    0.100001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.020000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.184086] CPU1: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[    0.184112] Brought up 2 CPUs
[    0.184114] Total of 2 processors activated (7580.67 BogoMIPS).
[    0.184110] System has AMD C1E enabled
[    0.184110] Switch to broadcast mode on CPU1
[    0.184283] CPU0 attaching sched-domain:
[    0.184287]  domain 0: span 0-1 level MC
[    0.184290]   groups: 0 1
[    0.184296] CPU1 attaching sched-domain:
[    0.184299]  domain 0: span 0-1 level MC
[    0.184301]   groups: 1 0
[    0.184392] Switch to broadcast mode on CPU0
[    0.184392] devtmpfs: initialized
[    0.184392] regulator: core version 0.5
[    0.184392] Time: 15:03:34  Date: 05/02/10
[    0.184392] NET: Registered protocol family 16
[    0.184392] Trying to unpack rootfs image as initramfs...
[    0.184392] EISA bus registered
[    0.184392] ACPI: bus type pci registered
[    0.184392] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.184392] PCI: Not using MMCONFIG.
[    0.185048] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=8
[    0.185051] PCI: Using configuration type 1 for base access
[    0.188131] bio: create slab <bio-0> at 0
[    0.189287] ACPI: EC: EC description table is found, configuring boot EC
[    0.190664] ACPI: Executed 3 blocks of module-level executable AML code
[    0.202721] ACPI: Interpreter enabled
[    0.202730] ACPI: (supports S0 S3 S4 S5)
[    0.202759] ACPI: Using IOAPIC for interrupt routing
[    0.203064] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.206580] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.206583] PCI: Using MMCONFIG for extended config space
[    0.215328] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.215637] ACPI: No dock devices found.
[    0.215820] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.215911] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.215915] pci 0000:00:02.0: PME# disabled
[    0.215952] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.215956] pci 0000:00:04.0: PME# disabled
[    0.215992] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.215995] pci 0000:00:05.0: PME# disabled
[    0.216039] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.216042] pci 0000:00:06.0: PME# disabled
[    0.216078] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.216081] pci 0000:00:07.0: PME# disabled
[    0.216134] pci 0000:00:12.0: reg 10 io port: [0xb000-0xb007]
[    0.216142] pci 0000:00:12.0: reg 14 io port: [0xa000-0xa003]
[    0.216150] pci 0000:00:12.0: reg 18 io port: [0x9000-0x9007]
[    0.216158] pci 0000:00:12.0: reg 1c io port: [0x8000-0x8003]
[    0.216166] pci 0000:00:12.0: reg 20 io port: [0x7000-0x700f]
[    0.216174] pci 0000:00:12.0: reg 24 32bit mmio: [0xfdeff800-0xfdeffbff]
[    0.216194] pci 0000:00:12.0: set SATA to AHCI mode
[    0.216237] pci 0000:00:13.0: reg 10 32bit mmio: [0xfdefe000-0xfdefefff]
[    0.216297] pci 0000:00:13.1: reg 10 32bit mmio: [0xfdefd000-0xfdefdfff]
[    0.216357] pci 0000:00:13.2: reg 10 32bit mmio: [0xfdefc000-0xfdefcfff]
[    0.216417] pci 0000:00:13.3: reg 10 32bit mmio: [0xfdefb000-0xfdefbfff]
[    0.216477] pci 0000:00:13.4: reg 10 32bit mmio: [0xfdefa000-0xfdefafff]
[    0.216557] pci 0000:00:13.5: reg 10 32bit mmio: [0xfdeff000-0xfdeff0ff]
[    0.216613] pci 0000:00:13.5: supports D1 D2
[    0.216616] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.216621] pci 0000:00:13.5: PME# disabled
[    0.216672] pci 0000:00:14.0: reg 10 io port: [0xb00-0xb0f]
[    0.216745] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.216753] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.216761] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.216769] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.216777] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.216834] pci 0000:00:14.2: reg 10 64bit mmio: [0xfdef4000-0xfdef7fff]
[    0.216881] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.216886] pci 0000:00:14.2: PME# disabled
[    0.217091] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.217097] pci 0000:01:00.0: reg 14 io port: [0xc000-0xc0ff]
[    0.217104] pci 0000:01:00.0: reg 18 32bit mmio: [0xfdff0000-0xfdffffff]
[    0.217120] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfdfc0000-0xfdfdffff]
[    0.217139] pci 0000:01:00.0: supports D1 D2
[    0.217193] pci 0000:00:02.0: bridge io port: [0xc000-0xcfff]
[    0.217196] pci 0000:00:02.0: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.217201] pci 0000:00:02.0: bridge 64bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.217252] pci 0000:00:04.0: bridge io port: [0xd000-0xdfff]
[    0.217255] pci 0000:00:04.0: bridge 32bit mmio: [0xfe000000-0xfe8fffff]
[    0.217260] pci 0000:00:04.0: bridge 64bit mmio pref: [0xfa000000-0xfcffffff]
[    0.217358] pci 0000:06:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.217377] pci 0000:06:00.0: reg 18 64bit mmio: [0xfe9ff000-0xfe9fffff]
[    0.217396] pci 0000:06:00.0: reg 30 32bit mmio pref: [0xfe9e0000-0xfe9effff]
[    0.217435] pci 0000:06:00.0: supports D1 D2
[    0.217438] pci 0000:06:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.217443] pci 0000:06:00.0: PME# disabled
[    0.217505] pci 0000:00:06.0: bridge io port: [0xe000-0xefff]
[    0.217509] pci 0000:00:06.0: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.217553] pci 0000:07:00.0: reg 10 64bit mmio: [0xfeaf0000-0xfeafffff]
[    0.217606] pci 0000:07:00.0: supports D1
[    0.217609] pci 0000:07:00.0: PME# supported from D0 D1 D3hot
[    0.217613] pci 0000:07:00.0: PME# disabled
[    0.217676] pci 0000:00:07.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.217725] pci 0000:08:01.0: reg 10 32bit mmio: [0xfebff800-0xfebfffff]
[    0.217790] pci 0000:08:01.0: PME# supported from D0 D3hot D3cold
[    0.217795] pci 0000:08:01.0: PME# disabled
[    0.217841] pci 0000:08:01.1: reg 10 32bit mmio: [0xfebff400-0xfebff4ff]
[    0.217906] pci 0000:08:01.1: supports D1 D2
[    0.217908] pci 0000:08:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.217914] pci 0000:08:01.1: PME# disabled
[    0.217960] pci 0000:08:01.2: reg 10 32bit mmio: [0xfebff000-0xfebff0ff]
[    0.218024] pci 0000:08:01.2: supports D1 D2
[    0.218027] pci 0000:08:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.218032] pci 0000:08:01.2: PME# disabled
[    0.218078] pci 0000:08:01.3: reg 10 32bit mmio: [0xfebfec00-0xfebfecff]
[    0.218142] pci 0000:08:01.3: supports D1 D2
[    0.218145] pci 0000:08:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.218151] pci 0000:08:01.3: PME# disabled
[    0.218216] pci 0000:00:14.4: transparent bridge
[    0.218224] pci 0000:00:14.4: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.218244] pci_bus 0000:00: on NUMA node 0
[    0.218252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.218519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.227379] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.227533] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 *15)
[    0.227681] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.227827] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.227974] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.228130] ACPI: PCI Interrupt Link [LNKF] (IRQs *9)
[    0.228272] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.228419] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.228570] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.228576] vgaarb: loaded
[    0.228696] SCSI subsystem initialized
[    0.228809] libata version 3.00 loaded.
[    0.228883] usbcore: registered new interface driver usbfs
[    0.228897] usbcore: registered new interface driver hub
[    0.228922] usbcore: registered new device driver usb
[    0.229080] ACPI: WMI: Mapper loaded
[    0.229082] PCI: Using ACPI for IRQ routing
[    0.229334] NetLabel: Initializing
[    0.229337] NetLabel:  domain hash size = 128
[    0.229339] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.229353] NetLabel:  unlabeled traffic allowed by default
[    0.229400] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.229407] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.231419] Switching to clocksource hpet
[    0.231529] AppArmor: AppArmor Filesystem Enabled
[    0.231529] pnp: PnP ACPI init
[    0.231529] ACPI: bus type pnp registered
[    0.233280] pnp: PnP ACPI: found 13 devices
[    0.233284] ACPI: ACPI bus type pnp unregistered
[    0.233288] PnPBIOS: Disabled by ACPI PNP
[    0.233304] system 00:06: ioport range 0x250-0x253 has been reserved
[    0.233308] system 00:06: ioport range 0x256-0x25f has been reserved
[    0.233312] system 00:06: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.233316] system 00:06: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.233327] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.233330] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.233334] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.233337] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.233341] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.233345] system 00:08: ioport range 0xc50-0xc51 has been reserved
[    0.233348] system 00:08: ioport range 0xc52-0xc52 has been reserved
[    0.233352] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.233355] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.233359] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.233363] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.233366] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.233370] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.233373] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.233377] system 00:08: ioport range 0x800-0x89f has been reserved
[    0.233381] system 00:08: ioport range 0xb10-0xb1f has been reserved
[    0.233384] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.233388] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.233392] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[    0.233396] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.233400] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.233407] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.233414] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.233417] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.233421] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.233424] system 00:0c: iomem range 0x100000-0x7fffffff could not be reserved
[    0.233428] system 00:0c: iomem range 0xe0000000-0xffffffff could not be reserved
[    0.268169] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.268173] pci 0000:00:02.0:   IO window: 0xc000-0xcfff
[    0.268177] pci 0000:00:02.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.268181] pci 0000:00:02.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.268186] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.268189] pci 0000:00:04.0:   IO window: 0xd000-0xdfff
[    0.268193] pci 0000:00:04.0:   MEM window: 0xfe000000-0xfe8fffff
[    0.268197] pci 0000:00:04.0:   PREFETCH window: 0x000000fa000000-0x000000fcffffff
[    0.268201] pci 0000:00:05.0: PCI bridge, secondary bus 0000:05
[    0.268203] pci 0000:00:05.0:   IO window: disabled
[    0.268207] pci 0000:00:05.0:   MEM window: disabled
[    0.268210] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.268214] pci 0000:00:06.0: PCI bridge, secondary bus 0000:06
[    0.268217] pci 0000:00:06.0:   IO window: 0xe000-0xefff
[    0.268221] pci 0000:00:06.0:   MEM window: 0xfe900000-0xfe9fffff
[    0.268224] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.268228] pci 0000:00:07.0: PCI bridge, secondary bus 0000:07
[    0.268230] pci 0000:00:07.0:   IO window: disabled
[    0.268234] pci 0000:00:07.0:   MEM window: 0xfea00000-0xfeafffff
[    0.268237] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.268242] pci 0000:00:14.4: PCI bridge, secondary bus 0000:08
[    0.268244] pci 0000:00:14.4:   IO window: disabled
[    0.268250] pci 0000:00:14.4:   MEM window: 0xfeb00000-0xfebfffff
[    0.268255] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.268269] pci 0000:00:02.0: setting latency timer to 64
[    0.268275] pci 0000:00:04.0: setting latency timer to 64
[    0.268281] pci 0000:00:05.0: setting latency timer to 64
[    0.268287] pci 0000:00:06.0: setting latency timer to 64
[    0.268293] pci 0000:00:07.0: setting latency timer to 64
[    0.268303] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.268306] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.268309] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.268312] pci_bus 0000:01: resource 1 mem: [0xfdf00000-0xfdffffff]
[    0.268316] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]
[    0.268319] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.268322] pci_bus 0000:02: resource 1 mem: [0xfe000000-0xfe8fffff]
[    0.268325] pci_bus 0000:02: resource 2 pref mem [0xfa000000-0xfcffffff]
[    0.268329] pci_bus 0000:06: resource 0 io:  [0xe000-0xefff]
[    0.268332] pci_bus 0000:06: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.268335] pci_bus 0000:07: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.268338] pci_bus 0000:08: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.268341] pci_bus 0000:08: resource 3 io:  [0x00-0xffff]
[    0.268344] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.268384] NET: Registered protocol family 2
[    0.268486] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.268848] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.269471] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.269777] TCP: Hash tables configured (established 131072 bind 65536)
[    0.269780] TCP reno registered
[    0.269883] NET: Registered protocol family 1
[    0.364052] pci 0000:01:00.0: Boot video device
[    0.364088] Simple Boot Flag at 0x52 set to 0x1
[    0.364288] cpufreq-nforce2: No nForce2 chipset.
[    0.364316] Scanning for low memory corruption every 60 seconds
[    0.364427] audit: initializing netlink socket (disabled)
[    0.364439] type=2000 audit(1272812614.361:1): initialized
[    0.375592] highmem bounce pool size: 64 pages
[    0.375599] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.377243] VFS: Disk quotas dquot_6.5.2
[    0.377308] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.377955] fuse init (API version 7.13)
[    0.378051] msgmni has been set to 1693
[    0.378287] alg: No test for stdrng (krng)
[    0.378350] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.378354] io scheduler noop registered
[    0.378356] io scheduler anticipatory registered
[    0.378358] io scheduler deadline registered
[    0.378407] io scheduler cfq registered (default)
[    0.378569]   alloc irq_desc for 24 on node -1
[    0.378572]   alloc kstat_irqs on node -1
[    0.378581] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.378588] pcieport 0000:00:02.0: setting latency timer to 64
[    0.378666]   alloc irq_desc for 25 on node -1
[    0.378668]   alloc kstat_irqs on node -1
[    0.378673] pcieport 0000:00:04.0: irq 25 for MSI/MSI-X
[    0.378678] pcieport 0000:00:04.0: setting latency timer to 64
[    0.378760]   alloc irq_desc for 26 on node -1
[    0.378762]   alloc kstat_irqs on node -1
[    0.378767] pcieport 0000:00:05.0: irq 26 for MSI/MSI-X
[    0.378772] pcieport 0000:00:05.0: setting latency timer to 64
[    0.378849]   alloc irq_desc for 27 on node -1
[    0.378851]   alloc kstat_irqs on node -1
[    0.378856] pcieport 0000:00:06.0: irq 27 for MSI/MSI-X
[    0.378861] pcieport 0000:00:06.0: setting latency timer to 64
[    0.378939]   alloc irq_desc for 28 on node -1
[    0.378941]   alloc kstat_irqs on node -1
[    0.378946] pcieport 0000:00:07.0: irq 28 for MSI/MSI-X
[    0.378951] pcieport 0000:00:07.0: setting latency timer to 64
[    0.379018] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.379099] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.379296] ACPI: AC Adapter [AC0] (on-line)
[    0.379382] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.379386] ACPI: Power Button [PWRB]
[    0.379437] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.379444] ACPI: Sleep Button [SLPB]
[    0.379492] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.381331] ACPI: Lid Switch [LID]
[    0.381385] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.381389] ACPI: Power Button [PWRF]
[    0.381885] ACPI: processor limited to max C-state 1
[    0.381913] processor LNXCPU:00: registered as cooling_device0
[    0.381952] processor LNXCPU:01: registered as cooling_device1
[    0.387476] thermal LNXTHERM:01: registered as thermal_zone0
[    0.387484] ACPI: Thermal Zone [THRM] (69 C)
[    0.389369] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.390859] brd: module loaded
[    0.391405] loop: module loaded
[    0.391527] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.391743]   alloc irq_desc for 16 on node -1
[    0.391746]   alloc kstat_irqs on node -1
[    0.391754] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.391796] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.392184] Fixed MDIO Bus: probed
[    0.392224] PPP generic driver version 2.4.2
[    0.392276] tun: Universal TUN/TAP device driver, 1.6
[    0.392278] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.392384] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.392406]   alloc irq_desc for 19 on node -1
[    0.392408]   alloc kstat_irqs on node -1
[    0.392414] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.392435] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.392478] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.392507] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.392522] ehci_hcd 0000:00:13.5: debug port 1
[    0.392547] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfdeff000
[    0.393128] isapnp: Scanning for PnP cards...
[    0.442262] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.442375] usb usb1: configuration #1 chosen from 1 choice
[    0.442409] hub 1-0:1.0: USB hub found
[    0.442420] hub 1-0:1.0: 10 ports detected
[    0.442508] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.442526] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.442545] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.442584] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.442612] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfdefe000
[    0.448406] ACPI: Battery Slot [BAT0] (battery present)
[    0.482717] Freeing initrd memory: 7724k freed
[    0.509178] usb usb2: configuration #1 chosen from 1 choice
[    0.509212] hub 2-0:1.0: USB hub found
[    0.509227] hub 2-0:1.0: 2 ports detected
[    0.509291]   alloc irq_desc for 17 on node -1
[    0.509294]   alloc kstat_irqs on node -1
[    0.509302] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.509324] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.509365] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.509396] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfdefd000
[    0.569088] usb usb3: configuration #1 chosen from 1 choice
[    0.569119] hub 3-0:1.0: USB hub found
[    0.569129] hub 3-0:1.0: 2 ports detected
[    0.569176]   alloc irq_desc for 18 on node -1
[    0.569178]   alloc kstat_irqs on node -1
[    0.569183] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.569196] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.569236] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.569263] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfdefc000
[    0.664773] usb usb4: configuration #1 chosen from 1 choice
[    0.664805] hub 4-0:1.0: USB hub found
[    0.664816] hub 4-0:1.0: 2 ports detected
[    0.664869] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.664883] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    0.664918] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    0.664936] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfdefb000
[    0.721088] usb usb5: configuration #1 chosen from 1 choice
[    0.721117] hub 5-0:1.0: USB hub found
[    0.721127] hub 5-0:1.0: 2 ports detected
[    0.721175] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.721188] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    0.721226] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    0.721241] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfdefa000
[    0.752078] isapnp: No Plug & Play device found
[    0.780148] usb usb6: configuration #1 chosen from 1 choice
[    0.780182] hub 6-0:1.0: USB hub found
[    0.780196] hub 6-0:1.0: 2 ports detected
[    0.780264] uhci_hcd: USB Universal Host Controller Interface driver
[    0.780359] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.782220] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.784265] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.784275] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.784306] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.784335] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.784361] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.784503] mice: PS/2 mouse device common for all mice
[    0.784689] rtc_cmos 00:02: RTC can wake from S4
[    0.784737] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.784769] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.784890] device-mapper: uevent: version 1.0.3
[    0.785026] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.785150] device-mapper: multipath: version 1.1.0 loaded
[    0.785153] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.785305] EISA: Probing bus 0 at eisa.0
[    0.785340] Cannot allocate resource for EISA slot 7
[    0.785342] Cannot allocate resource for EISA slot 8
[    0.785345] EISA: Detected 0 cards.
[    0.785487] cpuidle: using governor ladder
[    0.785490] cpuidle: using governor menu
[    0.785994] TCP cubic registered
[    0.786163] NET: Registered protocol family 10
[    0.786678] lo: Disabled Privacy Extensions
[    0.787039] NET: Registered protocol family 17
[    0.787080] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 processors (2 cpu cores) (version 2.20.00)
[    0.787132] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x13
[    0.787134] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x14
[    0.787137] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x15
[    0.787140] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1a
[    0.787187] Using IPI No-Shortcut mode
[    0.787292] PM: Resume from disk failed.
[    0.787307] registered taskstats version 1
[    0.787731]   Magic number: 10:246:82
[    0.787839] rtc_cmos 00:02: setting system clock to 2010-05-02 15:03:35 UTC (1272812615)
[    0.787843] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.787845] EDD information not available.
[    0.787900] Freeing unused kernel memory: 672k freed
[    0.788432] Write protecting the kernel text: 4828k
[    0.788509] Write protecting the kernel read-only data: 1876k
[    0.808071] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    0.812679] udev: starting version 151
[    0.817702] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.951125] usb 1-6: configuration #1 chosen from 1 choice
[    0.981096] scsi0 : pata_atiixp
[    0.982456] scsi1 : pata_atiixp
[    0.984087] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    0.984092] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    0.984759] ahci 0000:00:12.0: version 3.0
[    0.984785]   alloc irq_desc for 22 on node -1
[    0.984788]   alloc kstat_irqs on node -1
[    0.984797] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.984843] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    0.984951] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.984955] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    0.985486] scsi2 : ahci
[    0.985585] scsi3 : ahci
[    0.985654] scsi4 : ahci
[    0.985717] scsi5 : ahci
[    0.985867] ata3: SATA max UDMA/133 abar m1024@0xfdeff800 port 0xfdeff900 irq 22
[    0.985872] ata4: SATA max UDMA/133 abar m1024@0xfdeff800 port 0xfdeff980 irq 22
[    0.985877] ata5: SATA max UDMA/133 abar m1024@0xfdeff800 port 0xfdeffa00 irq 22
[    0.985881] ata6: SATA max UDMA/133 abar m1024@0xfdeff800 port 0xfdeffa80 irq 22
[    1.064066] usb 1-10: new high speed USB device using ehci_hcd and address 3
[    1.164535] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632H, AS02, max UDMA/33
[    1.196519] ata1.00: configured for UDMA/33
[    1.197934] usb 1-10: configuration #1 chosen from 1 choice
[    1.201086] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  AS02 PQ: 0 ANSI: 5
[    1.217045] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.217050] Uniform CD-ROM driver Revision: 3.20
[    1.217195] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.217272] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.304073] ata6: SATA link down (SStatus 0 SControl 300)
[    1.304106] ata5: SATA link down (SStatus 0 SControl 300)
[    1.304136] ata4: SATA link down (SStatus 0 SControl 300)
[    1.468053] ata3: softreset failed (device not ready)
[    1.468057] ata3: applying SB600 PMP SRST workaround and retrying
[    1.632065] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.632774] ata3.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
[    1.632778] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.632800] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.633695] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.633700] ata3.00: configured for UDMA/133
[    1.648164] scsi 2:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    1.648352] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.648362] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.648454] sd 2:0:0:0: [sda] Write Protect is off
[    1.648458] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.648487] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.648749]  sda: sda1 sda2 sda3
[    1.667580] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.670951] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.670978] r8169 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.671029] r8169 0000:06:00.0: setting latency timer to 64
[    1.671080]   alloc irq_desc for 29 on node -1
[    1.671083]   alloc kstat_irqs on node -1
[    1.671097] r8169 0000:06:00.0: irq 29 for MSI/MSI-X
[    1.671830] eth0: RTL8168b/8111b at 0xf830a000, 00:1d:60:07:8c:25, XID 18000000 IRQ 29
[    1.674628]   alloc irq_desc for 20 on node -1
[    1.674633]   alloc kstat_irqs on node -1
[    1.674642] ohci1394 0000:08:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.731086] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.954297] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    3.004391] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800039d4559]
[    9.566151] Adding 3996664k swap on /dev/sda1.  Priority:-1 extents:1 across:3996664k 
[    9.585718] udev: starting version 151
[    9.671343] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    9.675375] sdhci: Secure Digital Host Controller Interface driver
[    9.675379] sdhci: Copyright(c) Pierre Ossman
[    9.683721] lp: driver loaded but no devices found
[    9.716080] sdhci-pci 0000:08:01.1: SDHCI controller found [1180:0822] (rev 22)
[    9.716104]   alloc irq_desc for 21 on node -1
[    9.716107]   alloc kstat_irqs on node -1
[    9.716115] sdhci-pci 0000:08:01.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    9.717148] sdhci-pci 0000:08:01.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    9.750155] Registered led device: mmc0::
[    9.751201] mmc0: SDHCI controller on PCI [0000:08:01.1] using DMA
[    9.793442] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    9.798792] Linux agpgart interface v0.103
[    9.928283] type=1505 audit(1272812624.640:2):  operation="profile_load" pid=610 name="/sbin/dhclient3"
[    9.928585] type=1505 audit(1272812624.640:3):  operation="profile_load" pid=610 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.928753] type=1505 audit(1272812624.640:4):  operation="profile_load" pid=610 name="/usr/lib/connman/scripts/dhclient-script"
[    9.951557] cfg80211: Calling CRDA to update world regulatory domain
[    9.975165] asus_laptop: Asus Laptop Support version 0.42
[    9.978916] asus_laptop:   F3Ke model detected
[   10.014183] cfg80211: World regulatory domain updated:
[   10.014188] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.014192] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.014196] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.014199] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.014202] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.014205] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.016605] input: Asus Laptop extra buttons as /devices/virtual/input/input6
[   10.027163] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   10.067739] [drm] Initialized drm 1.1.0 20060810
[   10.071063] acpi device:26: registered as cooling_device2
[   10.071591] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:22/LNXVIDEO:01/input/input7
[   10.071743] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[   10.082292] Linux video capture interface: v2.00
[   10.135679] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (174f:5a35)
[   10.138532] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/input/input8
[   10.138595] usbcore: registered new interface driver uvcvideo
[   10.138599] USB Video Class driver (v0.1.0)
[   10.151270] dib0700: loaded with support for 13 different device-types
[   10.157482] dvb-usb: found a 'YUAN High-Tech STK7700PH' in warm state.
[   10.158028] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.161229] DVB: registering new adapter (YUAN High-Tech STK7700PH)
[   10.164234] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.164245] ath9k 0000:07:00.0: setting latency timer to 64
[   10.237562] [drm] radeon defaulting to kernel modesetting.
[   10.237567] [drm] radeon kernel modesetting enabled.
[   10.237659] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.237665] radeon 0000:01:00.0: setting latency timer to 64
[   10.239863] [drm] radeon: Initializing kernel modesetting.
[   10.242422] [drm] register mmio base: 0xFDFF0000
[   10.242426] [drm] register mmio size: 65536
[   10.243629] ATOM BIOS: Asus
[   10.243856] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[   10.243876] [drm] Generation 2 PCI interface, using max accessible memory
[   10.243879] [drm] radeon: VRAM 128M
[   10.243881] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   10.243883] [drm] radeon: GTT 512M
[   10.243885] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   10.243948]   alloc irq_desc for 30 on node -1
[   10.243951]   alloc kstat_irqs on node -1
[   10.243963] radeon 0000:01:00.0: irq 30 for MSI/MSI-X
[   10.243969] [drm] radeon: using MSI.
[   10.243997] [drm] radeon: irq initialized.
[   10.244148] [drm] Detected VRAM RAM=128M, BAR=128M
[   10.244154] [drm] RAM width 64bits DDR
[   10.249657] [TTM] Zone  kernel: Available graphics memory: 437774 kiB.
[   10.249661] [TTM] Zone highmem: Available graphics memory: 1030466 kiB.
[   10.249682] [drm] radeon: 128M of VRAM memory ready
[   10.249684] [drm] radeon: 512M of GTT memory ready.
[   10.249702] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   10.252884] [drm] RB2D reset succeed (RBBM_STATUS=0x10000140)
[   10.252904] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   10.252963] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   10.252983] [drm] radeon: cp idle (0x10000C03)
[   10.253219] [drm] Loading R500 Microcode
[   10.253610] platform radeon_cp.0: firmware: requesting radeon/R520_cp.bin
[   10.262306] [drm] radeon: ring at 0x0000000020000000
[   10.262342] [drm] ring test succeeded in 7 usecs
[   10.262527] [drm] radeon: ib pool ready.
[   10.263088] [drm] ib test succeeded in 0 usecs
[   10.263267] [drm] Default TV standard: PAL
[   10.263357] [drm] Radeon Display Connectors
[   10.263359] [drm] Connector 0:
[   10.263361] [drm]   VGA
[   10.263364] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   10.263366] [drm]   Encoders:
[   10.263368] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   10.263370] [drm] Connector 1:
[   10.263372] [drm]   LVDS
[   10.263375] [drm]   DDC: 0xc54 0xc54 0xc58 0xc58 0xc5c 0xc5c 0xc60 0xc60
[   10.263377] [drm]   Encoders:
[   10.263378] [drm]     LCD1: INTERNAL_LVTM1
[   10.263380] [drm] Connector 2:
[   10.263382] [drm]   S-video
[   10.263383] [drm]   Encoders:
[   10.263385] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   10.263387] [drm] Connector 3:
[   10.263388] [drm]   DVI-I
[   10.263390] [drm]   HPD1
[   10.263392] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   10.263395] [drm]   Encoders:
[   10.263396] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[   10.276277] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input9
[   10.294081] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input10
[   10.315907] ath: EEPROM regdomain: 0x60
[   10.315911] ath: EEPROM indicates we should expect a direct regpair map
[   10.315917] ath: Country alpha2 being used: 00
[   10.315919] ath: Regpair used: 0x60
[   10.326500] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.327308] Registered led device: ath9k-phy0::radio
[   10.327327] Registered led device: ath9k-phy0::assoc
[   10.327345] Registered led device: ath9k-phy0::tx
[   10.327363] Registered led device: ath9k-phy0::rx
[   10.327376] phy0: Atheros AR5418 MAC/BB Rev:2 AR5133 RF Rev:81: mem=0xf85c0000, irq=19
[   10.394725] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   10.450423] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.476177] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   10.487793] xc2028 5-0061: creating new instance
[   10.487798] xc2028 5-0061: type set to XCeive xc2028/xc3028 tuner
[   10.487915] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb1/1-10/input/input11
[   10.487984] dvb-usb: schedule remote query interval to 50 msecs.
[   10.487990] dvb-usb: YUAN High-Tech STK7700PH successfully initialized and connected.
[   10.488565] usbcore: registered new interface driver dvb_usb_dib0700
[   10.557033] hda_codec: ALC660-VD: BIOS auto-probing.
[   10.557802] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input12
[   10.877194] [drm] fb mappable at 0xF00C0000
[   10.877198] [drm] vram apper at 0xF0000000
[   10.877201] [drm] size 5299200
[   10.877203] [drm] fb depth is 24
[   10.877205] [drm]    pitch is 5888
[   10.877408] fb0: radeondrmfb frame buffer device
[   10.877411] registered panic notifier
[   10.877419] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   10.879855] vga16fb: initializing
[   10.879860] vga16fb: mapped to 0xc00a0000
[   10.879867] vga16fb: not registering due to another framebuffer present
[   11.225979] Console: switching to colour frame buffer device 160x50
[   11.451126] r8169: eth0: link up
[   11.451136] r8169: eth0: link up
[   22.064048] eth0: no IPv6 routers present
[   66.268069] usb 1-4: new high speed USB device using ehci_hcd and address 4
[   66.401883] usb 1-4: configuration #1 chosen from 1 choice
[   66.436882] Initializing USB Mass Storage driver...
[   66.437261] scsi6 : SCSI emulation for USB Mass Storage devices
[   66.437423] usbcore: registered new interface driver usb-storage
[   66.437429] USB Mass Storage support registered.
[   66.439765] usb-storage: device found at 4
[   66.439769] usb-storage: waiting for device to settle before scanning
[   71.436249] usb-storage: device scan complete
[   71.436972] scsi 6:0:0:0: Direct-Access     Corsair  Voyager Mini     0.00 PQ: 0 ANSI: 2
[   71.438192] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   71.442709] sd 6:0:0:0: [sdb] 15771720 512-byte logical blocks: (8.07 GB/7.52 GiB)
[   71.443457] sd 6:0:0:0: [sdb] Write Protect is off
[   71.443464] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   71.443467] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   71.448075] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   71.448082]  sdb:
[   71.740519] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   71.740525] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   71.867182] ehci_hcd 0000:00:13.5: force halt; handhake f8270024 00004000 00000000 -> -110
[   71.952092] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952098] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952102] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952106] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952109] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952112] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   71.952116] hub 1-0:1.0: cannot disable port 4 (err = -108)
[   71.952119] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952122] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952125] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952128] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952131] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952133] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   71.952137] hub 1-0:1.0: cannot disable port 4 (err = -108)
[   71.952140] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952144] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952147] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952151] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952154] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952157] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   71.952160] hub 1-0:1.0: cannot disable port 4 (err = -108)
[   71.952164] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952167] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952170] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952173] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952177] hub 1-0:1.0: cannot reset port 4 (err = -108)
[   71.952179] hub 1-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   71.952183] hub 1-0:1.0: cannot disable port 4 (err = -108)
[   71.952186] hub 1-0:1.0: cannot disable port 4 (err = -108)
[   71.952205] hub 1-0:1.0: hub_port_status failed (err = -108)
[   71.952256] sd 6:0:0:0: [sdb] Unhandled error code
[   71.952259] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.952263] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a7 80 00 00 08 00
[   71.952275] end_request: I/O error, dev sdb, sector 15771520
[   71.952280] Buffer I/O error on device sdb, logical block 1971440
[   71.952370] sd 6:0:0:0: [sdb] Unhandled error code
[   71.952372] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.952376] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a7 80 00 00 08 00
[   71.952385] end_request: I/O error, dev sdb, sector 15771520
[   71.952389] Buffer I/O error on device sdb, logical block 1971440
[   71.952487] sd 6:0:0:0: [sdb] Unhandled error code
[   71.952490] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.952493] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 38 00 00 08 00
[   71.952503] end_request: I/O error, dev sdb, sector 15771704
[   71.952506] Buffer I/O error on device sdb, logical block 1971463
[   71.952572] sd 6:0:0:0: [sdb] Unhandled error code
[   71.952575] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.952579] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 38 00 00 08 00
[   71.952588] end_request: I/O error, dev sdb, sector 15771704
[   71.952591] Buffer I/O error on device sdb, logical block 1971463
[   71.952664] sd 6:0:0:0: [sdb] Unhandled error code
[   71.952667] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.952671] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.952679] end_request: I/O error, dev sdb, sector 8
[   71.952683] Buffer I/O error on device sdb, logical block 1
[   71.952745] sd 6:0:0:0: [sdb] Unhandled error code
[   71.952748] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.952752] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.952762] end_request: I/O error, dev sdb, sector 8
[   71.952765] Buffer I/O error on device sdb, logical block 1
[   71.952836] sd 6:0:0:0: [sdb] Unhandled error code
[   71.952838] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.952842] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 40 00 00 01 00
[   71.952852] end_request: I/O error, dev sdb, sector 15771712
[   71.952855] Buffer I/O error on device sdb, logical block 1971464
[   71.952921] sd 6:0:0:0: [sdb] Unhandled error code
[   71.952923] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.952927] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 40 00 00 01 00
[   71.952936] end_request: I/O error, dev sdb, sector 15771712
[   71.952940] Buffer I/O error on device sdb, logical block 1971464
[   71.953006] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953009] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953012] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 40 00 00 01 00
[   71.953021] end_request: I/O error, dev sdb, sector 15771712
[   71.953024] Buffer I/O error on device sdb, logical block 1971464
[   71.953091] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953094] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953098] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 40 00 00 01 00
[   71.953108] end_request: I/O error, dev sdb, sector 15771712
[   71.953111] Buffer I/O error on device sdb, logical block 1971464
[   71.953184] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953187] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953190] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 40 00 00 01 00
[   71.953200] end_request: I/O error, dev sdb, sector 15771712
[   71.953267] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953269] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953273] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 40 00 00 01 00
[   71.953282] end_request: I/O error, dev sdb, sector 15771712
[   71.953349] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953352] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953356] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 08 00 00 08 00
[   71.953365] end_request: I/O error, dev sdb, sector 15771656
[   71.953434] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953436] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953440] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 38 00 00 08 00
[   71.953449] end_request: I/O error, dev sdb, sector 15771704
[   71.953516] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953518] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953522] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.953532] end_request: I/O error, dev sdb, sector 8
[   71.953597] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953600] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953603] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.953613] end_request: I/O error, dev sdb, sector 8
[   71.953678] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953681] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953685] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 40 00 00 01 00
[   71.953694] end_request: I/O error, dev sdb, sector 15771712
[   71.953761] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953764] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953767] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 40 00 00 01 00
[   71.953777] end_request: I/O error, dev sdb, sector 15771712
[   71.953846] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953849] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953853] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 f0 a8 40 00 00 01 00
[   71.953862] end_request: I/O error, dev sdb, sector 15771712
[   71.953935] sd 6:0:0:0: [sdb] Unhandled error code
[   71.953937] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.953941] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 08 00 00 00 08 00
[   71.953950] end_request: I/O error, dev sdb, sector 2048
[   71.954024] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954027] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954031] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 78 40 00 00 08 00
[   71.954040] end_request: I/O error, dev sdb, sector 30784
[   71.954109] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954112] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954116] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 20 00 00 08 00
[   71.954125] end_request: I/O error, dev sdb, sector 32
[   71.954227] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954229] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954233] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.954243] end_request: I/O error, dev sdb, sector 8
[   71.954310] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954312] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954316] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.954325] end_request: I/O error, dev sdb, sector 8
[   71.954391] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954393] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954397] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.954406] end_request: I/O error, dev sdb, sector 8
[   71.954471] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954474] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954478] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.954487] end_request: I/O error, dev sdb, sector 8
[   71.954555] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954557] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954561] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   71.954570] end_request: I/O error, dev sdb, sector 24
[   71.954635] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954638] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954642] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   71.954651] end_request: I/O error, dev sdb, sector 24
[   71.954718] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954720] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954724] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   71.954734] end_request: I/O error, dev sdb, sector 24
[   71.954799] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954802] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954805] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   71.954814] end_request: I/O error, dev sdb, sector 24
[   71.954884] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954887] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954890] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   71.954900] end_request: I/O error, dev sdb, sector 120
[   71.954966] sd 6:0:0:0: [sdb] Unhandled error code
[   71.954969] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.954972] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   71.954981] end_request: I/O error, dev sdb, sector 120
[   71.955047] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955050] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955053] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   71.955063] end_request: I/O error, dev sdb, sector 120
[   71.955129] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955132] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955135] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   71.955144] end_request: I/O error, dev sdb, sector 120
[   71.955210] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955213] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955217] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.955226] end_request: I/O error, dev sdb, sector 8
[   71.955292] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955294] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955298] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.955307] end_request: I/O error, dev sdb, sector 8
[   71.955373] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955375] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955379] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   71.955387] end_request: I/O error, dev sdb, sector 24
[   71.955452] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955455] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955459] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   71.955468] end_request: I/O error, dev sdb, sector 24
[   71.955534] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955537] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955541] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   71.955550] end_request: I/O error, dev sdb, sector 120
[   71.955616] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955618] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955622] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
[   71.955631] end_request: I/O error, dev sdb, sector 120
[   71.955700] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955702] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955706] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   71.955715] end_request: I/O error, dev sdb, sector 16
[   71.955785] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955788] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955792] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   71.955801] end_request: I/O error, dev sdb, sector 128
[   71.955867] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955870] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955874] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   71.955883] end_request: I/O error, dev sdb, sector 128
[   71.955949] sd 6:0:0:0: [sdb] Unhandled error code
[   71.955951] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.955955] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   71.955964] end_request: I/O error, dev sdb, sector 128
[   71.960116] sd 6:0:0:0: [sdb] Unhandled error code
[   71.960120] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.960125] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   71.960136] end_request: I/O error, dev sdb, sector 16
[   71.960335] sd 6:0:0:0: [sdb] Unhandled error code
[   71.960338] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.960341] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   71.960350] end_request: I/O error, dev sdb, sector 128
[   71.960481] sd 6:0:0:0: [sdb] Unhandled error code
[   71.960484] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.960487] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   71.960497] end_request: I/O error, dev sdb, sector 64
[   71.960672] sd 6:0:0:0: [sdb] Unhandled error code
[   71.960675] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.960679] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   71.960688] end_request: I/O error, dev sdb, sector 64
[   71.960855] sd 6:0:0:0: [sdb] Unhandled error code
[   71.960857] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.960861] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   71.960870] end_request: I/O error, dev sdb, sector 64
[   71.960976] sd 6:0:0:0: [sdb] Unhandled error code
[   71.960979] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.960982] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   71.960991] end_request: I/O error, dev sdb, sector 64
[   71.961157] sd 6:0:0:0: [sdb] Unhandled error code
[   71.961159] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.961163] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   71.961172] end_request: I/O error, dev sdb, sector 64
[   71.961315] sd 6:0:0:0: [sdb] Unhandled error code
[   71.961318] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.961321] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   71.961330] end_request: I/O error, dev sdb, sector 64
[   71.961524] sd 6:0:0:0: [sdb] Unhandled error code
[   71.961527] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.961530] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   71.961539] end_request: I/O error, dev sdb, sector 64
[   71.961641] sd 6:0:0:0: [sdb] Unhandled error code
[   71.961643] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.961647] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   71.961656] end_request: I/O error, dev sdb, sector 64
[   71.961836] sd 6:0:0:0: [sdb] Unhandled error code
[   71.961839] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.961842] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   71.961851] end_request: I/O error, dev sdb, sector 64
[   71.962155] sd 6:0:0:0: [sdb] Unhandled error code
[   71.962158] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.962162] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[   71.962171] end_request: I/O error, dev sdb, sector 64
[   71.962362] sd 6:0:0:0: [sdb] Unhandled error code
[   71.962365] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.962368] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[   71.962377] end_request: I/O error, dev sdb, sector 256
[   71.962498] sd 6:0:0:0: [sdb] Unhandled error code
[   71.962501] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.962505] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
[   71.962513] end_request: I/O error, dev sdb, sector 256
[   71.962658] sd 6:0:0:0: [sdb] Unhandled error code
[   71.962661] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.962665] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
[   71.962674] end_request: I/O error, dev sdb, sector 264
[   71.962815] sd 6:0:0:0: [sdb] Unhandled error code
[   71.962818] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.962822] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
[   71.962831] end_request: I/O error, dev sdb, sector 264
[   71.963018] sd 6:0:0:0: [sdb] Unhandled error code
[   71.963020] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.963024] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
[   71.963033] end_request: I/O error, dev sdb, sector 272
[   71.963163] sd 6:0:0:0: [sdb] Unhandled error code
[   71.963166] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.963170] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
[   71.963179] end_request: I/O error, dev sdb, sector 272
[   71.963324] sd 6:0:0:0: [sdb] Unhandled error code
[   71.963327] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.963330] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
[   71.963339] end_request: I/O error, dev sdb, sector 768
[   71.963530] sd 6:0:0:0: [sdb] Unhandled error code
[   71.963532] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.963536] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
[   71.963545] end_request: I/O error, dev sdb, sector 768
[   71.963657] sd 6:0:0:0: [sdb] Unhandled error code
[   71.963660] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.963664] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 08 00 00 08 00
[   71.963672] end_request: I/O error, dev sdb, sector 776
[   71.963839] sd 6:0:0:0: [sdb] Unhandled error code
[   71.963841] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.963845] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 08 00 00 08 00
[   71.963854] end_request: I/O error, dev sdb, sector 776
[   71.964093] sd 6:0:0:0: [sdb] Unhandled error code
[   71.964095] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.964100] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 10 00 00 08 00
[   71.964108] end_request: I/O error, dev sdb, sector 784
[   71.964246] sd 6:0:0:0: [sdb] Unhandled error code
[   71.964249] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.964253] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 10 00 00 08 00
[   71.964262] end_request: I/O error, dev sdb, sector 784
[   71.964406] sd 6:0:0:0: [sdb] Unhandled error code
[   71.964409] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.964412] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   71.964421] end_request: I/O error, dev sdb, sector 16
[   71.964595] sd 6:0:0:0: [sdb] Unhandled error code
[   71.964598] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.964602] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   71.964611] end_request: I/O error, dev sdb, sector 16
[   71.964754] sd 6:0:0:0: [sdb] Unhandled error code
[   71.964756] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.964760] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   71.964769] end_request: I/O error, dev sdb, sector 16
[   71.964947] sd 6:0:0:0: [sdb] Unhandled error code
[   71.964949] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.964953] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   71.964961] end_request: I/O error, dev sdb, sector 128
[   71.965102] sd 6:0:0:0: [sdb] Unhandled error code
[   71.965105] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.965109] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   71.965118] end_request: I/O error, dev sdb, sector 128
[   71.965183] sd 6:0:0:0: [sdb] Unhandled error code
[   71.965186] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.965190] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   71.965199] end_request: I/O error, dev sdb, sector 16
[   71.966811] sd 6:0:0:0: [sdb] Unhandled error code
[   71.966813] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.966817] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.966826] end_request: I/O error, dev sdb, sector 8
[   71.966893] sd 6:0:0:0: [sdb] Unhandled error code
[   71.966895] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.966898] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
[   71.966907] end_request: I/O error, dev sdb, sector 16
[   71.966973] sd 6:0:0:0: [sdb] Unhandled error code
[   71.966976] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.966979] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
[   71.966988] end_request: I/O error, dev sdb, sector 8
[   71.967053] sd 6:0:0:0: [sdb] Unhandled error code
[   71.967055] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.967059] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
[   71.967068] end_request: I/O error, dev sdb, sector 128
[   71.967135] sd 6:0:0:0: [sdb] Unhandled error code
[   71.967137] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[   71.967140] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
[   71.967149] end_request: I/O error, dev sdb, sector 4096
```

Every device I'm trying is working on PC with Windows and they are Fat32.

---

### Post by P4man on 2010-05-02
Clearly it detects the pendrive. You can see in the log its a Corsair  Voyager Mini 8GB stick, but the kernel seems to think something is really wrong with it. Since it seems you have the same problem with various usb drives, that seems rather unlikely.

Its also not a matter of safely removing. Even if the filesystem was dirty or corrupted, ubuntu might not mount the filesystem, but it would still show up in lsusb and nautilus etc. 

Do other devices hotplug properly? If you disconnect and reconnect your mouse, does that work? If not, its a problem with usb controller (and/or its driver)

Im not sure what you can do about this. A powered hub might be a workaround, but not really a good solution. Perhaps a bios update or checking your bios usb settings (if any), but Id file a bug report on launchpad.

Maybe someone else has better ideas?

---

### Post by Night Howl on 2010-05-02
My devices: 2 pendrives (pqi, corsair), nokia mobile phone with memory card, tablet  (Genius), mouse with cable (asus), receiver for wireless keyboard and mouse (logitech)

Everything this I tested. Nothing is working properly. If I disconnect and reconnect mouse (I'm using logitech wireless mouse) it is not working. But if I don't disconnect it, it works fine. On Windows system, everything works.
In my notebook I have card reader and it is working, or external monitor works great too.
Before I created this thread I read about BIOS usb settings, but I don't have these options in my BIOS so I assume it is defaultly permitted. I didn't try BIOS update because it sounds little scary. Maybe I will try it.

---

### Post by P4man on 2010-05-02
Your log shows one line that caught my attention:
```
ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
```

Really looks like this is a kernel bug for you particular usb controller and/or a poor workaround. File a bug report, this has got to be fixed.

in the meanwhile you could try installing a different (older) kernel

```
sudo apt-get install linux-image-2.6.32-16-generic
```

Then reboot, if you dont get a grub boot menu, hold down the shift key right after the bios loaded and select the 2.6.32-16 kernel from the list. See if it helps. If not, just reboot normally and you;l have the latest kernel again. You can verify your kernel being used now by entering

```
uname -a
```

in a terminal. Its probably  2.6.32-21 right now.

---

### Post by Night Howl on 2010-05-02
I'm sorry. Linux is not system for me probably. I am not experienced enough to change kernel. This is my 4th day with linux. :)
It wrote it can't find the package and even if i try to read about that I'm only disapointed and have no idea what to do.
So thank you very much for trying to help me but I'm a lost case. :)

---

### Post by P4man on 2010-05-02
> **Night Howl said:**
> I'm sorry. Linux is not system for me probably. I am not experienced enough to change kernel. This is my 4th day with linux. :)

just noticed that kernel is not in the default repositories, which is why you probably failed. **My bad**!

No other kernels are available in the default repo's, so lets try the rt kernel in the multiverse repo. Dont faint. Sounds harder than it is.And Lets use the "windows" way of a gui. 

First lets enable the "multiverse repository"

Go to system > administration > synaptic package manager (read the msg and click ok)

then in synaptic, go to settings > repositories
Make sure the 4th option is selected (->software restricted by... multiverse)

close window

Click the reload button so it fetches the list of software from that repository.

Then in synaptic in the search box at the top, search for"

```
linux-rt 
```and ```
linux-headers-rt
```

right click them both,and mark them for installation. If it asks for additional stuff (called dependencies), accept it.

Then click in the main bar on the green apply button. Thats all.
[SIZE="1"]
(Alternatively you could have selected a single cli command, middle mouse click it open a terminal and middle click again and press enter. There is a reason linux folks like a terminal :) )[/SIZE]
 
Anyway, after doing that, you must reboot and select that rt kernel from grub menu. See above on how to do that.

Feel free to ask if you get stuck anywhere.

---

### Post by anewguy on 2010-08-14
I know this is an older thread, but there is a kernel bug that prevents hot-mount devices such as some USB flash drives, external USB disk drives, etc., to be mounted/seen unless they are plugged in during boot.  This is a known bug and is documented on launchpad.  Kernel .35 supposedly fixes it.

---

