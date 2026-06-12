---
title: "[SOLVED] sdb1 no write permision"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by mayagrafix on 2009-01-01
I have a USB external HD mounted which I can see on my desktop and shows up in the Thunar file manager. Problems is I cant write data (paste files or save documents) to it. Here is the Fdisk -l output:
<<<<<<<<<<<<>>>>>>>>>>>>>
[COLOR="Silver"]Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c700c6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3555    28555506   83  Linux
/dev/sda2            3556        3648      747022+   5  Extended
/dev/sda5            3556        3648      746991   82  Linux swap / Solaris[/COLOR]

Disk /dev/sdb: 6495 MB, 6495068160 bytes
255 heads, 63 sectors/track, 789 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005bbe6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         789     6337611   83  Linux
<<<<<<<<<<<<<<>>>>>>>>>>>>>>
The grayed out part shows my main HD. 

Thanks for your help Linux Gurus and Happy New Year!! :D

---

### Post by Rocket2DMn on 2009-01-01
Please post the output of the following commands as well:
```
cat /etc/fstab
sudo blkid
mount
```
Also, please try unplugging the device, plugging it back in and post the output of
```
dmesg
```

---

### Post by Rocket2DMn on 2009-01-01
Please post the output of the following commands as well:
```
cat /etc/fstab
sudo blkid
mount
```
Also, please try unplugging the device, plugging it back in and post the output of
```
dmesg
```

---

### Post by mayagrafix on 2009-01-01
Okay, I ran the commands and disconnected the USB external HD as requested. When I plugged it back in it showed up on the desktop and the file manager opened where it shows on the side bar. The last command dmesg provided a fairly large output, I hope it fits in here no problem:


[COLOR="Magenta"]rafael@Inspiron:~$ cat /etc/fstab[/COLOR]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3921d4ce-e855-405c-845c-9f1fb534e175 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=3b98928b-8019-4ea8-9877-f5e09877dc2e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1  /media/ntfsdata  ntfs ro,umask=0002,nls=utf8      0         0rafael@I

[COLOR="Magenta"]rafael@Inspiron:~$ sudo blkid[/COLOR]
[sudo] password for rafael: 
/dev/sda1: UUID="3921d4ce-e855-405c-845c-9f1fb534e175" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="3b98928b-8019-4ea8-9877-f5e09877dc2e" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdb1: UUID="81b9f3f4-5c1a-4ee0-9695-690884e745b0" TYPE="ext3"

[COLOR="Magenta"]rafael@Inspiron:~$ mount[/COLOR]
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rafael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rafael)
/dev/sdb1 on /media/ntfsdata type ext3 (rw)


<<<<<<<<<<<>>>>>>>>>>>>>>>>>>>


[COLOR="Magenta"]rafael@Inspiron:~$ dmesg[/COLOR]
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000eb800 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000010000000 (usable)
[    0.000000]  BIOS-e820: 00000000fffeb800 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x10000 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 10000000 @ 7000-c000
[    0.000000] RAMDISK: 0f793000 - 0ffefbb0
[    0.000000] DMI not present or invalid.
[    0.000000] ACPI Error (tbxfroot-0218): A valid RSDP was not found [20080609]
[    0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 256MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 10000000
[    0.000000]   low ram: 00000000 - 10000000
[    0.000000]   bootmap 00002000 - 00004000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0010000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [000f793000 - 000ffefbb0]          RAMDISK ==> [000f793000 - 000ffefbb0]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00010000
[    0.000000]   HighMem  0x00010000 -> 0x00010000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00010000
[    0.000000] On node 0 totalpages: 65439
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 60900 pages, LIFO batch:15
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01241000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ec000
[    0.000000] PM: Registered nosave memory: 00000000000ec000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effeb800)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64863
[    0.000000] Kernel command line: root=UUID=3921d4ce-e855-405c-845c-9f1fb534e175 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: Using PIT calibration value
[    0.000000] Detected 300.003 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 245576k/262144k available (2572k kernel code, 16036k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd0800000 - 0xff3fe000   ( 747 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004039] Calibrating delay loop (skipped), value calculated using timer frequency.. 600.00 BogoMIPS (lpj=1200012)
[    0.004164] Security Framework initialized
[    0.004210] SELinux:  Disabled at boot.
[    0.004356] AppArmor: AppArmor initialized
[    0.004415] Mount-cache hash table entries: 512
[    0.005448] Initializing cgroup subsys ns
[    0.005477] Initializing cgroup subsys cpuacct
[    0.005498] Initializing cgroup subsys memory
[    0.005588] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.005613] CPU: L2 cache: 256K
[    0.005707] Checking 'hlt' instruction... OK.
[    0.020249] SMP alternatives: switching to UP code
[    0.044105] Freeing SMP alternatives: 11k freed
[    0.044438] weird, boot CPU (#0) not listedby the BIOS.
[    0.044458] SMP motherboard not detected.
[    0.044479] Local APIC not detected. Using dummy APIC emulation.
[    0.044495] SMP disabled
[    0.045052] Brought up 1 CPUs
[    0.045072] Total of 1 processors activated (600.00 BogoMIPS).
[    0.048104] CPU0 attaching sched-domain:
[    0.048127]  domain 0: span 0 level CPU
[    0.048147]   groups: 0
[    0.050078] net_namespace: 840 bytes
[    0.050111] Booting paravirtualized kernel on bare hardware
[    0.051757] Time: 18:07:48  Date: 01/01/09
[    0.051958] NET: Registered protocol family 16
[    0.055143] EISA bus registered
[    0.056205] PCI: PCI BIOS revision 2.10 entry at 0xfd9d3, last bus=1
[    0.056228] PCI: Using configuration type 1 for base access
[    0.065743] ACPI: Interpreter disabled.
[    0.065770] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.066157] pnp: PnP ACPI: disabled
[    0.066179] PnPBIOS: Scanning system for PnP BIOS support...
[    0.066295] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6e60
[    0.066320] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb3ba, dseg 0x400
[    0.080049] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[    0.083670] PCI: Probing PCI hardware
[    0.083697] PCI: Probing PCI hardware (bus 00)
[    0.084382] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e3ffffff]
[    0.084626] PCI: 0000:00:04.0 reg 10 32bit mmio: [30100000, 30100fff]
[    0.084678] pci 0000:00:04.0: supports D1
[    0.084693] pci 0000:00:04.0: supports D2
[    0.084711] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot
[    0.084735] pci 0000:00:04.0: PME# disabled
[    0.084817] PCI: 0000:00:04.1 reg 10 32bit mmio: [30101000, 30101fff]
[    0.084866] pci 0000:00:04.1: supports D1
[    0.084880] pci 0000:00:04.1: supports D2
[    0.084897] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot
[    0.084919] pci 0000:00:04.1: PME# disabled
[    0.085168] PCI: 0000:00:07.1 reg 20 io port: [fcd0, fcdf]
[    0.085314] PCI: 0000:00:07.2 reg 20 io port: [fce0, fcff]
[    0.085400] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[    0.085412] * this clock source is slow. Consider trying other clock sources
[    0.085536] pci 0000:00:07.3: quirk: region 8000-803f claimed by PIIX4 ACPI
[    0.085562] pci 0000:00:07.3: quirk: region 2180-218f claimed by PIIX4 SMB
[    0.085673] PCI: 0000:00:08.0 reg 10 io port: [f800, f8ff]
[    0.085779] pci 0000:00:08.0: supports D1
[    0.085793] pci 0000:00:08.0: supports D2
[    0.085810] pci 0000:00:08.0: PME# supported from D1 D2 D3hot
[    0.085832] pci 0000:00:08.0: PME# disabled
[    0.086003] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.086034] PCI: 0000:01:00.0 reg 14 io port: [e800, e8ff]
[    0.086064] PCI: 0000:01:00.0 reg 18 32bit mmio: [fedfe000, fedfefff]
[    0.086121] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.086177] pci 0000:01:00.0: supports D1
[    0.086192] pci 0000:01:00.0: supports D2
[    0.086289] PCI: bridge 0000:00:01.0 io port: [e000, efff]
[    0.086312] PCI: bridge 0000:00:01.0 32bit mmio: [fd000000, fedfffff]
[    0.092319] pci 0000:00:07.0: PIIX/ICH IRQ router [8086/7110]
[    0.092410] PCI: setting IRQ 11 as level-triggered
[    0.092431] pci 0000:00:04.0: found PCI INT A -> IRQ 11
[    0.092510] pci 0000:00:04.0: sharing IRQ 11 with 0000:01:00.0
[    0.092545] pci 0000:00:04.1: found PCI INT B -> IRQ 11
[    0.093398] NET: Registered protocol family 8
[    0.093398] NET: Registered protocol family 20
[    0.093398] NetLabel: Initializing
[    0.093398] NetLabel:  domain hash size = 128
[    0.093398] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.093398] NetLabel:  unlabeled traffic allowed by default
[    0.096561] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.096582]    actual entries 65620
[    0.097543] AppArmor: AppArmor Filesystem Enabled
[    0.097686] system 00:00: ioport range 0x401-0x407 has been reserved
[    0.097712] system 00:00: ioport range 0x3810-0x388f has been reserved
[    0.097741] system 00:00: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.097817] system 00:05: iomem range 0x0-0x9ffff could not be reserved
[    0.097842] system 00:05: iomem range 0xdc000-0xfffff could not be reserved
[    0.097866] system 00:05: iomem range 0x100000-0xfffffff could not be reserved
[    0.097938] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.097962] system 00:0a: ioport range 0x8000-0x803f has been reserved
[    0.097985] system 00:0a: ioport range 0x2180-0x218f has been reserved
[    0.098035] system 00:0b: iomem range 0xcf000-0xcffff has been reserved
[    0.103700] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.103730] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.103758] pci 0000:00:01.0:   MEM window: 0xfd000000-0xfedfffff
[    0.103783] pci 0000:00:01.0:   PREFETCH window: 0x00000030000000-0x000000300fffff
[    0.103816] pci 0000:00:04.0: CardBus bridge, secondary bus 0000:02
[    0.103836] pci 0000:00:04.0:   IO window: 0x001000-0x0010ff
[    0.103860] pci 0000:00:04.0:   IO window: 0x001400-0x0014ff
[    0.103884] pci 0000:00:04.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.103909] pci 0000:00:04.0:   MEM window: 0x24000000-0x27ffffff
[    0.103934] pci 0000:00:04.1: CardBus bridge, secondary bus 0000:06
[    0.103953] pci 0000:00:04.1:   IO window: 0x001800-0x0018ff
[    0.103976] pci 0000:00:04.1:   IO window: 0x001c00-0x001cff
[    0.104085] pci 0000:00:04.1:   PREFETCH window: 0x28000000-0x2bffffff
[    0.104113] pci 0000:00:04.1:   MEM window: 0x2c000000-0x2fffffff
[    0.104184] pci 0000:00:04.0: found PCI INT A -> IRQ 11
[    0.104266] pci 0000:00:04.0: sharing IRQ 11 with 0000:01:00.0
[    0.104318] pci 0000:00:04.1: found PCI INT B -> IRQ 11
[    0.104411] bus: 00 index 0 io port: [0, ffff]
[    0.104429] bus: 00 index 1 mmio: [0, ffffffff]
[    0.104447] bus: 01 index 0 io port: [e000, efff]
[    0.104465] bus: 01 index 1 mmio: [fd000000, fedfffff]
[    0.104483] bus: 01 index 2 mmio: [30000000, 300fffff]
[    0.104501] bus: 01 index 3 mmio: [0, 0]
[    0.104518] bus: 02 index 0 io port: [1000, 10ff]
[    0.104536] bus: 02 index 1 io port: [1400, 14ff]
[    0.104554] bus: 02 index 2 mmio: [20000000, 23ffffff]
[    0.104572] bus: 02 index 3 mmio: [24000000, 27ffffff]
[    0.104591] bus: 06 index 0 io port: [1800, 18ff]
[    0.104609] bus: 06 index 1 io port: [1c00, 1cff]
[    0.104627] bus: 06 index 2 mmio: [28000000, 2bffffff]
[    0.104645] bus: 06 index 3 mmio: [2c000000, 2fffffff]
[    0.104722] NET: Registered protocol family 2
[    0.105941] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.107847] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.108244] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.108575] TCP: Hash tables configured (established 8192 bind 8192)
[    0.108597] TCP reno registered
[    0.109307] NET: Registered protocol family 1
[    0.110152] checking if image is initramfs... it is
[    5.485081] Freeing initrd memory: 8562k freed
[    5.489706] audit: initializing netlink socket (disabled)
[    5.489793] type=2000 audit(1230833272.488:1): initialized
[    5.531624] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    5.556136] VFS: Disk quotas dquot_6.5.1
[    5.557079] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.557976] msgmni has been set to 496
[    5.559134] io scheduler noop registered
[    5.559157] io scheduler anticipatory registered
[    5.559175] io scheduler deadline registered
[    5.559317] io scheduler cfq registered (default)
[    5.559385] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    5.559535] pci 0000:01:00.0: Boot video device
[    5.562145] isapnp: Scanning for PnP cards...
[    5.915593] isapnp: No Plug & Play device found
[    6.357446] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    6.378849] brd: module loaded
[    6.379454] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    6.380551] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    6.394373] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.394422] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.397613] mice: PS/2 mouse device common for all mice
[    6.398917] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    6.398985] rtc0: alarms up to one day
[    6.400097] EISA: Probing bus 0 at eisa.0
[    6.400134] Cannot allocate resource for EISA slot 1
[    6.400165] Cannot allocate resource for EISA slot 3
[    6.400215] Cannot allocate resource for EISA slot 8
[    6.400231] EISA: Detected 0 cards.
[    6.400252] cpuidle: using governor ladder
[    6.400269] cpuidle: using governor menu
[    6.405109] TCP cubic registered
[    6.405360] Using IPI No-Shortcut mode
[    6.407601] registered taskstats version 1
[    6.408152]   Magic number: 9:17:139
[    6.408200] block ram4: hash matches
[    6.408859] rtc_cmos 00:04: setting system clock to 2009-01-01 18:07:54 UTC (1230833274)
[    6.408888] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.408905] EDD information not available.
[    6.411680] Freeing unused kernel memory: 424k freed
[    6.412110] Write protecting the kernel text: 2576k
[    6.412360] Write protecting the kernel read-only data: 936k
[    6.430700] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    6.979196] compcache: Compressed swap size set to: 63680 KB
[    6.981068] TLSF: pool: d080c000, init_size=16384, max_size=0, grow_size=16384
[    7.932758] fuse init (API version 7.9)
[    8.796681] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   11.777846] usbcore: registered new interface driver usbfs
[   11.778008] usbcore: registered new interface driver hub
[   11.782957] usbcore: registered new device driver usb
[   11.820384] SCSI subsystem initialized
[   11.830013] USB Universal Host Controller Interface driver v3.0
[   11.843318] uhci_hcd 0000:00:07.2: found PCI INT D -> IRQ 11
[   11.843451] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   11.843844] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   11.843941] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000fce0
[   11.847399] usb usb1: configuration #1 chosen from 1 choice
[   11.847633] hub 1-0:1.0: USB hub found
[   11.847714] hub 1-0:1.0: 2 ports detected
[   12.062681] libata version 3.00 loaded.
[   12.214589] ata_piix 0000:00:07.1: version 2.12
[   12.220585] scsi0 : ata_piix
[   12.224500] scsi1 : ata_piix
[   12.224948] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xfcd0 irq 14
[   12.224973] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xfcd8 irq 15
[   12.269075] Adding 63676k swap on /dev/ramzswap0.  Priority:100 extents:1 across:63676k
[   12.300899] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   12.389383] ata1.00: ATA-5: TOSHIBA MK3018GAS, Q3.03 E, max UDMA/100
[   12.389414] ata1.00: 58605120 sectors, multi 16: LBA 
[   12.398237] ata1.00: configured for UDMA/33
[   12.453146] usb 1-1: configuration #1 chosen from 1 choice
[   12.561406] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-C2202, 1D13, max MWDMA2
[   12.577465] ata2.00: configured for MWDMA2
[   12.578293] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3018GA Q3.0 PQ: 0 ANSI: 5
[   12.581285] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-C2202 1D13 PQ: 0 ANSI: 5
[   16.157452] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[   16.158093] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   16.198583] usbcore: registered new interface driver libusual
[   16.415166] Initializing USB Mass Storage driver...
[   16.475778] scsi2 : SCSI emulation for USB Mass Storage devices
[   16.476507] usbcore: registered new interface driver usb-storage
[   16.476540] USB Mass Storage support registered.
[   16.476577] usb-storage: device found at 2
[   16.476594] usb-storage: waiting for device to settle before scanning
[   16.529399] Driver 'sd' needs updating - please use bus_type methods
[   16.530094] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[   16.530246] sd 0:0:0:0: [sda] Write Protect is off
[   16.530271] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.530532] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.531039] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[   16.531186] sd 0:0:0:0: [sda] Write Protect is off
[   16.531210] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.531467] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.531506]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   16.611012]  sda1 sda2 < sda5 >
[   16.639440] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.659719] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   16.659758] Uniform CD-ROM driver Revision: 3.20
[   16.660430] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   17.422572] PM: Starting manual resume from disk
[   17.422606] PM: Resume from partition 8:5
[   17.422620] PM: Checking hibernation image.
[   17.423281] PM: Resume from disk failed.
[   17.691642] kjournald starting.  Commit interval 5 seconds
[   17.691725] EXT3-fs: mounted filesystem with ordered data mode.
[   21.476520] usb-storage: device scan complete
[   21.486058] scsi 2:0:0:0: Direct-Access     FUJITSU  MHH2064AT        0811 PQ: 0 ANSI: 0
[   21.499965] sd 2:0:0:0: [sdb] 12685680 512-byte hardware sectors (6495 MB)
[   21.506848] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   21.506917] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   21.513877] sd 2:0:0:0: [sdb] 12685680 512-byte hardware sectors (6495 MB)
[   21.520806] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   21.520851] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   21.521000]  sdb: sdb1
[   21.604545] sd 2:0:0:0: [sdb] Attached SCSI disk
[   21.609105] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   30.587613] udevd version 124 started
[   37.034473] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.142518] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   37.208346] Yenta: CardBus bridge found at 0000:00:04.0 [1028:0085]
[   37.208408] Yenta: Enabling burst memory read transactions
[   37.208432] Yenta: Using CSCINT to route CSC interrupts to PCI
[   37.208450] Yenta: Routing CardBus interrupts to PCI
[   37.208475] Yenta TI: socket 0000:00:04.0, mfunc 0x01021c72, devctl 0x66
[   37.439294] Yenta: ISA IRQ mask 0x06d8, PCI irq 11
[   37.439319] Socket status: 30000006
[   37.479246] Yenta: CardBus bridge found at 0000:00:04.1 [1028:0085]
[   37.479306] Yenta: Using CSCINT to route CSC interrupts to PCI
[   37.479325] Yenta: Routing CardBus interrupts to PCI
[   37.479349] Yenta TI: socket 0000:00:04.1, mfunc 0x01021c72, devctl 0x66
[   37.591095] Linux agpgart interface v0.103
[   37.711308] Yenta: ISA IRQ mask 0x06d8, PCI irq 11
[   37.711332] Socket status: 30000068
[   38.096452] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.375749] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[   38.385391] pccard: CardBus card inserted into slot 1
[   38.385504] PCI: 0000:06:00.0 reg 10 io port: [0, ff]
[   38.385543] PCI: 0000:06:00.0 reg 14 32bit mmio: [0, 1ff]
[   38.385664] pci 0000:06:00.0: supports D1
[   38.385684] pci 0000:06:00.0: supports D2
[   38.385707] pci 0000:06:00.0: PME# supported from D1 D2 D3hot
[   38.385739] pci 0000:06:00.0: PME# disabled
[   38.523458] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   39.342548] piix4_smbus 0000:00:07.3: SMBus Host Controller at 0x2180, revision 0
[   41.307469] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   49.073406] PCI: setting IRQ 5 as level-triggered
[   49.073433] ES1968 (ESS Maestro) 0000:00:08.0: found PCI INT A -> IRQ 5
[   49.073594] es1968: not attempting power management.
[   49.679127] es1968: clocking to 48000
[   50.114478] Linux video capture interface: v2.00
[   53.428357] cs: IO port probe 0x100-0x3af: clean.
[   53.429840] cs: IO port probe 0x3e0-0x4ff: clean.
[   53.430637] cs: IO port probe 0x820-0x8ff: clean.
[   53.432123] cs: IO port probe 0x100-0x3af: clean.
[   53.433607] cs: IO port probe 0x3e0-0x4ff: clean.
[   53.434401] cs: IO port probe 0x820-0x8ff: clean.
[   53.435124] cs: IO port probe 0xc00-0xcf7: clean.
[   53.436884] cs: IO port probe 0xa00-0xaff: clean.
[   53.439071] cs: IO port probe 0xc00-0xcf7: clean.
[   53.440855] cs: IO port probe 0xa00-0xaff: clean.
[   54.202343] 8139too Fast Ethernet driver 0.9.28
[   54.202534] 8139too 0000:06:00.0: enabling device (0000 -> 0003)
[   54.202596] 8139too 0000:06:00.0: setting latency timer to 64
[   54.206960] eth0: RealTek RTL8139 at 0x1800, 00:10:d7:0b:9f:87, IRQ 11
[   54.206985] eth0:  Identified 8139 chip type 'RTL-8139C'
[   55.775464] lp: driver loaded but no devices found
[   57.669541] Adding 746980k swap on /dev/sda5.  Priority:-1 extents:1 across:746980k
[   58.424874] EXT3 FS on sda1, internal journal
[   62.359504] type=1505 audit(1230833330.533:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3645
[   64.030848] type=1505 audit(1230833332.205:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3650
[   64.032784] type=1505 audit(1230833332.209:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3650
[   64.706775] ip_tables: (C) 2000-2006 Netfilter Core Team
[   68.980292] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   68.981532] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   68.986632] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   68.988640] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   72.852689] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   73.113179] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   73.940774] ppdev: user-space parallel port driver
[   79.709888] NET: Registered protocol family 10
[   79.723771] lo: Disabled Privacy Extensions
[   88.387628] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   89.587044] NET: Registered protocol family 17
[   98.913772] eth0: no IPv6 routers present
[ 3795.953537] kjournald starting.  Commit interval 5 seconds
[ 3795.973523] EXT3 FS on sdb1, internal journal
[ 3795.980197] EXT3-fs: mounted filesystem with ordered data mode.
[ 7296.362439] usb 1-1: USB disconnect, address 2
[ 7296.614556] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 7296.778475] usb 1-1: configuration #1 chosen from 1 choice
[ 7296.810968] scsi3 : SCSI emulation for USB Mass Storage devices
[ 7296.815247] usb-storage: device found at 3
[ 7296.815292] usb-storage: waiting for device to settle before scanning
[ 7297.604829] usb 1-1: USB disconnect, address 3
[ 7297.882462] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 7298.044814] usb 1-1: configuration #1 chosen from 1 choice
[ 7298.055022] scsi4 : SCSI emulation for USB Mass Storage devices
[ 7298.067783] usb-storage: device found at 4
[ 7298.067831] usb-storage: waiting for device to settle before scanning
[ 7299.338649] usb 1-1: USB disconnect, address 4
[ 7321.419795] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 7321.587860] usb 1-1: configuration #1 chosen from 1 choice
[ 7321.617303] scsi5 : SCSI emulation for USB Mass Storage devices
[ 7321.621288] usb-storage: device found at 5
[ 7321.621332] usb-storage: waiting for device to settle before scanning
[ 7326.623801] usb-storage: device scan complete
[ 7326.643542] scsi 5:0:0:0: Direct-Access     FUJITSU  MHH2064AT        0811 PQ: 0 ANSI: 0
[ 7326.686814] sd 5:0:0:0: [sdc] 12685680 512-byte hardware sectors (6495 MB)
[ 7326.706791] sd 5:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 7326.706952] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 7326.726660] sd 5:0:0:0: [sdc] 12685680 512-byte hardware sectors (6495 MB)
[ 7326.740816] sd 5:0:0:0: [sdc] Test WP failed, assume Write Enabled
[ 7326.741070] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 7326.747795]  sdc: sdc1
[ 7326.851843] sd 5:0:0:0: [sdc] Attached SCSI disk
[ 7326.859664] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 7330.489982] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[ 7330.497218] Buffer I/O error on device sdb1, logical block 0
[ 7330.497266] lost page write due to I/O error on sdb1
[ 7330.504144] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[ 7330.504617] ------------[ cut here ]------------
[ 7330.504639] WARNING: at /build/buildd/linux-2.6.27/fs/buffer.c:1186 mark_buffer_dirty+0x85/0xa0()
[ 7330.504660] Modules linked in: binfmt_misc af_packet ipv6 ppdev apm cpufreq_conservative cpufreq_powersave cpufreq_stats cpufreq_ondemand cpufreq_userspace freq_table iptable_filter ip_tables x_tables parport_pc lp parport 8139too mii pcmcia radio_maestro videodev v4l1_compat snd_es1968 gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_mpu401_uart snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event serio_raw evdev snd_seq psmouse snd_timer snd_seq_device i2c_piix4 snd intel_agp shpchp i2c_core agpgart yenta_socket pcspkr rsrc_nonstatic pci_hotplug soundcore pcmcia_core ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif usb_storage libusual sg pata_acpi ata_piix ata_generic libata uhci_hcd scsi_mod usbcore dock fbcon tileblit font bitblit softcursor fuse compcache lzo_decompress lzo_compress tlsf
[ 7330.505126] Pid: 5348, comm: Thunar Not tainted 2.6.27-9-generic #1
[ 7330.505147]  [<c037c4b6>] ? printk+0x1d/0x1f
[ 7330.505205]  [<c0131de9>] warn_on_slowpath+0x59/0x90
[ 7330.505257]  [<c0102df6>] ? __switch_to+0xa6/0x160
[ 7330.505291]  [<c01284cb>] ? finish_task_switch+0x2b/0xe0
[ 7330.505322]  [<c037ca49>] ? schedule+0x429/0x790
[ 7330.505353]  [<c01376e6>] ? __do_softirq+0xf6/0x120
[ 7330.505394]  [<c012a18b>] ? __cond_resched+0x1b/0x40
[ 7330.505425]  [<c01d78e5>] mark_buffer_dirty+0x85/0xa0
[ 7330.505463]  [<d09c276b>] ext3_commit_super+0x4b/0x70 [ext3]
[ 7330.505592]  [<d09c4acd>] ext3_handle_error+0x4d/0xc0 [ext3]
[ 7330.505664]  [<c037c4b6>] ? printk+0x1d/0x1f
[ 7330.505702]  [<d09c4c06>] ext3_error+0x56/0x60 [ext3]
[ 7330.505788]  [<d09c0fb4>] ext3_find_entry+0x354/0x3f0 [ext3]
[ 7330.505870]  [<c01c43aa>] ? d_rehash+0x4a/0x60
[ 7330.505914]  [<c01c588e>] ? __d_lookup+0xe/0x120
[ 7330.505958]  [<d09c1092>] ext3_lookup+0x42/0xd0 [ext3]
[ 7330.506023]  [<c037e6dd>] ? _spin_lock+0xd/0x10
[ 7330.506057]  [<c01c60bf>] ? d_alloc+0x13f/0x1a0
[ 7330.506098]  [<c01bb93f>] real_lookup+0xaf/0x110
[ 7330.506126]  [<c01bba2d>] do_lookup+0x8d/0xd0
[ 7330.506151]  [<c01bbfad>] __link_path_walk+0x53d/0xb40
[ 7330.506181]  [<c01bca14>] path_walk+0x54/0xb0
[ 7330.506206]  [<c01bcbc6>] do_path_lookup+0xb6/0x1a0
[ 7330.506232]  [<c01bd7da>] user_path_at+0x4a/0x80
[ 7330.506258]  [<c01954b0>] ? unmap_vmas+0x1a0/0x360
[ 7330.506292]  [<c019cdbc>] ? anon_vma_unlink+0x6c/0x70
[ 7330.506330]  [<c0199434>] ? unlink_file_vma+0x14/0xa0
[ 7330.506360]  [<c01134ea>] ? flush_tlb_mm+0x4a/0xa0
[ 7330.506412]  [<c01b5d03>] vfs_lstat_fd+0x23/0x50
[ 7330.506453]  [<c019911e>] ? remove_vma+0x4e/0x70
[ 7330.506482]  [<c01b5dc6>] vfs_lstat+0x16/0x20
[ 7330.506508]  [<c01b5de9>] sys_lstat64+0x19/0x30
[ 7330.506535]  [<c0199d7a>] ? do_munmap+0x1da/0x230
[ 7330.506565]  [<c014ba38>] ? up_write+0x8/0x20
[ 7330.506606]  [<c0199e1b>] ? sys_munmap+0x4b/0x60
[ 7330.506635]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[ 7330.506665]  [<c0370000>] ? netdev_exit+0x10/0x20
[ 7330.506694]  =======================
[ 7330.506710] ---[ end trace 099892ab01df4e39 ]---
[ 7330.506806] Buffer I/O error on device sdb1, logical block 0
[ 7330.506831] lost page write due to I/O error on sdb1
[ 7332.949104] kjournald starting.  Commit interval 5 seconds
[ 7332.963650] EXT3 FS on sdc1, internal journal
[ 7332.963764] EXT3-fs: recovery complete.
[ 7332.977530] EXT3-fs: mounted filesystem with ordered data mode.


[COLOR="Magenta"]rafael@Inspiron:~$[/COLOR]

---

### Post by Rocket2DMn on 2009-01-01
For future reference you can wrap text in [noparse]```

```[/noparse] tags like I have done above.
The reason that the drive isn't allowing you write permissions is because it is mounted as read only! In fstab you have this line:
```
/dev/sdb1 /media/ntfsdata ntfs [COLOR="Red"]ro[/COLOR],umask=0002,nls=utf8 0 0
```
Normally we don't use fstab entries for external disks, so we'll just comment out the line and let *hal* mount the drive automatically for you.
```
gksudo gedit /etc/fstab
```
Now place a # in front of that line
```
# /dev/sdb1 /media/ntfsdata ntfs ro,umask=0002,nls=utf8 0 0
```
Save and close.  Unmount your external drive, unplug it, and plug it back in.  It should mount automatically.

If you want to label the drive (like say its just being called "disk"), see [uhelp]community/RenameUSBDrive[/uhelp]

---

### Post by mayagrafix on 2009-01-01
I edited the fstab file. When I right clicked the HD icon on the desktop to un-mount it, the options were mount volume and **eject volume**. When I used "eject volume" I got this message:

```
Unable to eject "6G Volume":
An unknown error occured
```

I went ahead and unplugged the USB external drive anyway. It came right back up as promised after I plugged it in. However, when I tried to save a document on it i got this message:

```
Can't open file to write
```

I tried to create a new folder thinking that it needed a place to save the doc and this message came up:

```
The folder contents could not be displayed
Error stating file '/media/disk/documents': No such file or directory
```

Should i re-boot to get the fstab file to work properly?

---

### Post by Rocket2DMn on 2009-01-01
You shouldn't have to reboot or do anything else to fstab.  Why don't you post the fstab file again so I can see your changes, plug the drive in, and post the output of "mount" again so I can see the details of how it is mounted.

You can also try manually mounting
```
sudo mkdir /media/temp
sudo mount -t ext3 /dev/sdb1 /media/temp
```
Post any output back here.
You will have to manually unmount afterward:
```
sudo umount /dev/sdb1
```

The previous mount shows the drive is ext3 formatted, whereas the fstab entry thought it was formatted with ntfs.

---

### Post by mayagrafix on 2009-01-01
```
rafael@Inspiron:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=3921d4ce-e855-405c-845c-9f1fb534e175 / ext3 defaults,errors=remount-ro,relatime 0 1
# Entry for /dev/sda5 :
UUID=3b98928b-8019-4ea8-9877-f5e09877dc2e none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```
```
rafael@Inspiron:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rafael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rafael)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
```

I also notice looking at the **Properties** tabs of the USB HD that the "owner" is **root** (I uploaded two screen shots of the tabs in question).

Does this have anything to do with the no write problem?

Thanks for all your help so far!!

---

### Post by mayagrafix on 2009-01-01
I also did the second group of commands 
```
rafael@Inspiron:~$ sudo mkdir /media/temp
[sudo] password for rafael: 
rafael@Inspiron:~$ sudo mount -t ext3 /dev/sdb1 /media/temp
rafael@Inspiron:~$ 
```
and not much happened. Here is a screenshot of the file manager:

---

### Post by joukez on 2009-01-01
Just " alt+F2" a small window will appear type there gksu nautilus then enter
then it asks your password. Now you are GUI logged in as root 
go from there and give user permit so user can R/W.

                     gr. Jouke

Sorry did not notice it is xfce,don't if it works there, well you can try it it won' t bite!

---

### Post by mc4man on 2009-01-01
Your going to have to chown the drive to write to it, one of the reason ext2/3 isn't always the best choice for external drives.

To do so unmount the drive but _leave connected_ (easiest is to just r.click on the icon -> unmount or run 
```
sudo umount /dev/sdb1
```

Then 
```
sudo mkdir /media/temp
```

```
sudo mount /dev/sdb1 /media/temp
```

```
sudo chown -R rafael:rafael /media/temp
```

replace rafael if your user name is different

```
sudo umount /dev/sdb1
```

Then remove the drive, plug in back in and you should have write permission to it.


Edit: after your done (you've umounted the drive) you can remove the temp folder if you wish with

```
gksudo nautilus
```

And navigate to filesystem -> media and delete it.

---

### Post by Rocket2DMn on 2009-01-01
Sorry for the delay, I'm watching the Rose Bowl (go Trojans!!).  Chowning the mount point should help as has been said, since ext3 has linux permissions (unlike NTFS or FAT32).  Be careful with that rm command above, but you can also use the -R option with chown.
```
sudo chown -R <yourusername>:<yourusername> /media/temp
```
Assuming /media/temp is still your mount point.  (Don't actually include the angled brackets in the chown command.)

---

### Post by mayagrafix on 2009-01-01
> **mc4man said:**
> Your going to have to chown the drive to write to it, one of the reason ext2/3 isn't always the best choice for external drives.

Just out of curiosity, since the drive is empty and I can easily re-format it, what is the recommended choice format for an external HD other than ext3?

---

### Post by mayagrafix on 2009-01-01
> **Rocket2DMn said:**
> Sorry for the delay, I'm watching the Rose Bowl (go Trojans!!)

I'm a Bruins fan personally but Ill give cheer for the hometown team :popcorn:

---

### Post by mayagrafix on 2009-01-01
Thank you very much people :D I now has permissions to R/W cheeseburger drive sdb1

---

### Post by Rocket2DMn on 2009-01-01
> **mayagrafix said:**
> I'm a Bruins fan personally but Ill give cheer for the hometown team :popcorn:

LOL get out...
No I'm kidding, in other news the PAC-10 is 5-0 in bowl games this year :)  Beat that everybody else!

> **mayagrafix said:**
> Thank you very much people :D I now has permissions to R/W cheeseburger drive sdb1

Sweet, glad you got it working.

---

### Post by mc4man on 2009-01-02
> Just out of curiosity, since the drive is empty and I can easily re-format it, what is the recommended choice format for an external HD other than ext3?

As a small follow up, if there is any intention of having other user names write to the drive (from this install or any other linux install) or for use with another Os then I'd format it to either 'FAT32' or 'NTFS'

As it stands now on any linux install only users named rafael (or whatever you used) will have write permissions without repeating the process for a different user name

---

