---
title: "Terrible startup when offline"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by JC Cheloven on 2008-08-28
Hi everybody,

In my toshiba laptop (see specs below), Ubuntu always had a very slow startup when not connected to the internet. It leaves the nice orange progress bar and gets into verbose mode. This occurs even when online, but startup is quick in this case (some 90 secs). Anyway, let's focus on what happens when offline:

- Spend about 40 secs at the point of 'Starting cups'
- Spend about 4 min (!!) at the point of 'Starting MTA'

This was the 'usual' situation when offline, with nothing special being done to the OS (as far as I can remember), other than ubuntu updates. But things are getting worse. I installed NetworManager7, as I heard [somewhere]("http://ubuntuforums.org/showthread.php?t=843973&highlight=huawei+e220+usb+modem") that it would manage well the Huawei E220 USB modem. This is a testing version yet. The modem didn't work anyway, and I uninstalled NM7, and installed NM6 again (except for the panel icon). I also did something else in the meanwhile: installing ssh server, using it for some file transfers between my computers, and uninstalling it afterwards. The situation by now is:

- When online, ubuntu starts fine, as always.
- When offline, I get the very slow startup (cups & mta) again, AND the gnome desktop lasts 5 or even 10 more minutes (!!) to get a usable state, and sometimes it doesn't reach such a state at all. The panels appear and disappear a couple of times, and the following message pops in a window:
> There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in.
After that, the system is sometimes usable, sometimes don't. As a bonus, sometimes I get my keyboard layout changed. To speed up startup, I disabled mta at that runlevel by renaming /etc/rc2.d/S20exim to /.../K20exim, as told [here]("http://ubuntuforums.org/showthread.php?t=625896"), which solved the 4 min of 'starting mta'. But the (main) problem of the gnome desktop is there.

To sum up: no problem would be noticed if connected to the internet at startup, but I use this computer in three different places, two of them with fixed ip's, and a third one (a friend's place, who I convinced to switch to linux) with no internet at all. I try to setup the settings of the next place I'll turn on my laptop before turning it off, but it's quite annoying, and not always possible. Also it's a bit hard for me to show my 'converted' friends how the system I recommended isn't working properly even for me. 

After reading some horror tales [like this]("http://ubuntuforums.org/showthread.php?t=899529"), I start considering the possibility of my system being compromised, as I was connected to the internet when using ssh for 2 hours or so. Perhaps a fresh reinstall is the safest solution (hmmm, like in windoz), but I'd rather to learn from this, and being able to help myself and to others in the future ;-)

Any help would be appreciated.

______________________
My laptop:
Toshiba SA50-110  /  Pentium M (0.09) 1596MHz  /  1.1 Cache =64K, 19704 MB/s  /  1.2 cache=2048K, 8674 MB/s  /  Memory=1007Mb 1039Mb/s
Chipset: Intel i855GM/GME/F SB  99MHz Mobile platform  /  Settings: RAM=165MHz (DDR330) / CAS=2.5-3-3-7
_______________________

---

### Post by JC Cheloven on 2008-08-29
Bump. Any ideas?

---

### Post by Cheesehead on 2008-08-29
Consider weeding (uninstalling) your unused packages.

Weed known problem packages -MTA and cups- you can always reinstall them.

You don't, by chance, have the netatalk (appletalk) package installed? It always used to hang my system while it searched for an appletalk network. 

Why on earth are you running an MTA on your laptop?

If that doesn't help, post your dmesg here.

---

### Post by JC Cheloven on 2008-08-30
Thanks for your answer! 

Some new info: when I plan to be offline, I can start session  in safe terminal mode, and disable the device (ifdown eth0). Then Gnome starts fine. I think MTA, cups, the gnome error, etc, are only symptoms of a hidden problem, related to something in my system trying to desesperately connect to the internet at startup (whenever it sees eth0 or eth1 enabled), and leading to confusion to everything else that would potentially need network access to work.

> Consider weeding (uninstalling) your unused packages.
Weed known problem packages -MTA and cups- you can always reinstall them. 
Why on earth are you running an MTA on your laptop?
I did prevent MTA from starting (in the way I told in the OP), which saved several minutes of startup time when offline. I don't know what MTA does exactly, I thought it was something preinstalled in Ubuntu :confused:  
As for cups, I need printing. Disabling or uninstalling cups would be too inconvenient.

> You don't, by chance, have the netatalk (appletalk) package installed? It always used to hang my system while it searched for an appletalk network.
No, I don't, as far as I know :-)

> If that doesn't help, post your dmesg here. 
Here you are (below). Some notes: 

- Three messages with "PCI: Cannot allocate resource region 4 of device..." can be seen. This happens since Gutsy, either online and offline. I suspect that my laptop has some handicap running linux because of this. It seems usb-related. I don't think in this as the cause of my present problems anyway.
- This is dmesg after booting offline (so 10 min to boot, 30 secs to start a terminal, and so on). I compared it side by side to dmesg after booting online, and the only differences I noticed are as follows:
-- lines 235 & 236 "Hash matches...". These didn't appear when online
-- some lines "ext3_orphan_cleanup..." and "ext3_fs..." appear here, but it is due to the fact that I had to hard-shutdown previously. It happens half of the times with my laptop.
-- line 402 "eth0: link is not ready" (should that be normal?)

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ef40000 (usable)
[    0.000000]  BIOS-e820: 000000003ef40000 - 000000003ef50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ef50000 - 000000003f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 111MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 257856) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   257856
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   257856
[    0.000000] On node 0 totalpages: 257856
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 222 pages used for memmap
[    0.000000]   HighMem zone: 28258 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F0180 checksum 0
[    0.000000] ACPI: RSDP 000F0180, 0014 (r0 TOSHIB)
[    0.000000] ACPI: RSDT 3EF40000, 0038 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: FACP 3EF40060, 0084 (r2 TOSHIB 750      20030101 TASM  4010000)
[    0.000000] ACPI: DSDT 3EF40118, 44B9 (r1 TOSHIB A0015    20040426 MSFT  100000E)
[    0.000000] ACPI: FACS 000EEE00, 0040
[    0.000000] ACPI: SSDT 3EF445D1, 0231 (r1 TOSHIB LNK10SS  20040226 MSFT  100000E)
[    0.000000] ACPI: DBGP 3EF400E4, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: BOOT 3EF40038, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: SSDT 3EF44802, 06C4 (r1 TOSHIB A0015    20040226 MSFT  100000E)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f000000:bfc10000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 00000000000ee000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ee000 - 00000000000ef000
[    0.000000] swsusp: Registered nosave memory region: 000000060000ef000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 255842
[    0.000000] Kernel command line: root=UUID=ed568681-153a-4feb-ad80-c4075d76d3ce ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (017ef000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.031 MHz processor.
[    9.713903] Console: colour VGA+ 80x25
[    9.713907] console [tty0] enabled
[    9.714301] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.714794] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.751647] Memory: 1010408k/1031424k available (2177k kernel code, 20316k reserved, 1006k data, 368k init, 113920k highmem)
[    9.751656] virtual kernel memory layout:
[    9.751657]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    9.751658]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.751660]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    9.751661]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    9.751662]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    9.751664]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[    9.751665]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[    9.751669] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.751708] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    9.831659] Calibrating delay using timer specific routine.. 3194.24 BogoMIPS (lpj=6388483)
[    9.831686] Security Framework initialized
[    9.831694] SELinux:  Disabled at boot.
[    9.831710] AppArmor: AppArmor initialized
[    9.831714] Failure registering capabilities with primary security module.
[    9.831723] Mount-cache hash table entries: 512
[    9.831857] Initializing cgroup subsys ns
[    9.831863] Initializing cgroup subsys cpuacct
[    9.831874] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[    9.831886] CPU: L1 I cache: 32K, L1 D cache: 32K
[    9.831889] CPU: L2 cache: 2048K
[    9.831892] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000 00000000
[    9.831902] Compat vDSO mapped to ffffe000.
[    9.831915] Checking 'hlt' instruction... OK.
[    9.848058] SMP alternatives: switching to UP code
[    9.850054] Freeing SMP alternatives: 11k freed
[    9.850168] Early unpacking initramfs... done
[   10.235824] ACPI: Core revision 20070126
[   10.235893] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.237777] ACPI: setting ELCR to 0200 (from 0e00)
[   10.238208] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
[   10.238214] SMP motherboard not detected.
[   10.238217] Local APIC not detected. Using dummy APIC emulation.
[   10.238264] Brought up 1 CPUs
[   10.238283] CPU0 attaching sched-domain:
[   10.238286]  domain 0: span 01
[   10.238288]   groups: 01
[   10.238473] net_namespace: 64 bytes
[   10.238482] Booting paravirtualized kernel on bare hardware
[   10.238961] Time: 18:11:20  Date: 08/30/08
[   10.238987] NET: Registered protocol family 16
[   10.239240] EISA bus registered
[   10.239254] ACPI: bus type pci registered
[   10.239461] PCI: PCI BIOS revision 2.10 entry at 0xfd480, last bus=3
[   10.239463] PCI: Using configuration type 1
[   10.239473] Setting up standard PCI resources
[   10.242028] ACPI: EC: Look up EC in DSDT
[   10.245124] ACPI: Interpreter enabled
[   10.245127] ACPI: (supports S0 S3 S4 S5)
[   10.245140] ACPI: Using PIC for interrupt routing
[   10.249105] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.249554] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
[   10.249558] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
[   10.249908] PCI: Transparent bridge - 0000:00:1e.0
[   10.249966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.250017] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   10.251892] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[   10.252023] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[   10.252152] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[   10.252280] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[   10.252408] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[   10.252535] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[   10.252663] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[   10.252791] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[   10.252979] ACPI: Power Resource [PFAN] (off)
[   10.253024] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.253055] pnp: PnP ACPI init
[   10.253062] ACPI: bus type pnp registered
[   10.254608] pnpacpi: exceeded the max number of IO resources: 40 
[   10.254971] pnp: PnP ACPI: found 9 devices
[   10.254973] ACPI: ACPI bus type pnp unregistered
[   10.254977] PnPBIOS: Disabled by ACPI PNP
[   10.255191] PCI: Using ACPI for IRQ routing
[   10.255194] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.255205] PCI: Cannot allocate resource region 4 of device 0000:00:1d.0
[   10.255208] PCI: Cannot allocate resource region 4 of device 0000:00:1d.1
[   10.255212] PCI: Cannot allocate resource region 4 of device 0000:00:1d.2
[   10.267303] NET: Registered protocol family 8
[   10.267305] NET: Registered protocol family 20
[   10.267365] AppArmor: AppArmor Filesystem Enabled
[   10.271269] Time: tsc clocksource has been installed.
[   10.279299] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   10.279302] system 00:00: iomem range 0xe0000-0xeffff could not be reserved
[   10.279306] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   10.279309] system 00:00: iomem range 0x100000-0x3ef3ffff could not be reserved
[   10.279313] system 00:00: iomem range 0x3ef40000-0x3ef4ffff could not be reserved
[   10.279316] system 00:00: iomem range 0x3ef50000-0x3effffff could not be reserved
[   10.279319] system 00:00: iomem range 0xfec10000-0xfec1ffff could not be reserved
[   10.279323] system 00:00: iomem range 0xfeda0000-0xfedbffff could not be reserved
[   10.279326] system 00:00: iomem range 0xffb80000-0xffbfffff could not be reserved
[   10.279329] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[   10.279338] system 00:08: ioport range 0x1e0-0x1e7 has been reserved
[   10.279341] system 00:08: ioport range 0x480-0x48f has been reserved
[   10.279344] system 00:08: ioport range 0x680-0x6ff has been reserved
[   10.279347] system 00:08: ioport range 0xd800-0xd87f has been reserved
[   10.279350] system 00:08: ioport range 0xd880-0xd89f has been reserved
[   10.279353] system 00:08: ioport range 0xd8a0-0xd8bf has been reserved
[   10.279356] system 00:08: ioport range 0xe000-0xe07f has been reserved
[   10.279359] system 00:08: ioport range 0xe080-0xe0ff has been reserved
[   10.279362] system 00:08: ioport range 0xe400-0xe47f has been reserved
[   10.279365] system 00:08: ioport range 0xe480-0xe4ff has been reserved
[   10.279368] system 00:08: ioport range 0xe800-0xe87f has been reserved
[   10.279372] system 00:08: ioport range 0xe880-0xe8ff has been reserved
[   10.279375] system 00:08: ioport range 0xec00-0xec7f has been reserved
[   10.279378] system 00:08: ioport range 0xec80-0xecff has been reserved
[   10.279381] system 00:08: ioport range 0xeeac-0xeeac has been reserved
[   10.279384] system 00:08: ioport range 0xeeb0-0xeebf has been reserved
[   10.279387] system 00:08: ioport range 0xeec0-0xeeff has been reserved
[   10.309811] PCI: Bus 2, cardbus bridge: 0000:01:0b.0
[   10.309814]   IO window: 0000c000-0000c0ff
[   10.309818]   IO window: 0000c400-0000c4ff
[   10.309822]   PREFETCH window: 4c000000-4fffffff
[   10.309826]   MEM window: 50000000-53ffffff
[   10.309830] PCI: Bridge: 0000:00:1e.0
[   10.309833]   IO window: c000-cfff
[   10.309838]   MEM window: cff00000-cfffffff
[   10.309842]   PREFETCH window: disabled.
[   10.309853] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.309867] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
[   10.310049] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   10.310052] PCI: setting IRQ 11 as level-triggered
[   10.310055] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.310070] NET: Registered protocol family 2
[   10.347266] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.347511] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.348428] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.349012] TCP: Hash tables configured (established 131072 bind 65536)
[   10.349016] TCP reno registered
[   10.359373] checking if image is initramfs... it is
[   10.810812] Switched to high resolution mode on CPU 0
[   11.110083] Freeing initrd memory: 7305k freed
[   11.110325] Simple Boot Flag at 0x7c set to 0x1
[   11.110719] audit: initializing netlink socket (disabled)
[   11.110737] audit(1220119880.364:1): initialized
[   11.110928] highmem bounce pool size: 64 pages
[   11.112922] VFS: Disk quotas dquot_6.5.1
[   11.113005] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.113158] io scheduler noop registered
[   11.113161] io scheduler anticipatory registered
[   11.113163] io scheduler deadline registered
[   11.113175] io scheduler cfq registered (default)
[   11.113192] Boot video device is 0000:00:02.0
[   11.113245] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   11.113543] isapnp: Scanning for PnP cards...
[   11.465919] isapnp: No Plug & Play device found
[   11.494428] Real Time Clock Driver v1.12ac
[   11.494545] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.495180] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[   11.495385] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   11.495389] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   11.495399] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   11.496045] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.496118] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   11.496216] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.501251] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.501256] serio: i8042 AUX port at 0x60,0x64 irq 12
[   11.506168] mice: PS/2 mouse device common for all mice
[   11.506279] EISA: Probing bus 0 at eisa.0
[   11.506286] Cannot allocate resource for EISA slot 1
[   11.506304] EISA: Detected 0 cards.
[   11.506307] cpuidle: using governor ladder
[   11.506310] cpuidle: using governor menu
[   11.506411] NET: Registered protocol family 1
[   11.506441] Using IPI No-Shortcut mode
[   11.506475] registered taskstats version 1
[   11.506585]   Magic number: 4:792:191
[   11.506610]   hash matches device ttys3
[   11.506683]   hash matches device device:1d
[   11.506695] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   11.506698] EDD information not available.
[   11.507007] Freeing unused kernel memory: 368k freed
[   11.530077] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   12.731181] fuse init (API version 7.9)
[   12.746472] ACPI: Transitioning device [FAN] to D3
[   12.746475] ACPI: Transitioning device [FAN] to D3
[   12.746479] ACPI: Fan [FAN] (off)
[   12.751602] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   12.752760] ACPI: Thermal Zone [THRM] (71 C)
[   13.380613] usbcore: registered new interface driver usbfs
[   13.380639] usbcore: registered new interface driver hub
[   13.389553] usbcore: registered new device driver usb
[   13.404941] USB Universal Host Controller Interface driver v3.0
[   13.405255] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   13.405258] PCI: setting IRQ 10 as level-triggered
[   13.405262] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   13.405275] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.405279] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.405700] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.405725] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
[   13.405872] usb usb1: configuration #1 chosen from 1 choice
[   13.405896] hub 1-0:1.0: USB hub found
[   13.405902] hub 1-0:1.0: 2 ports detected
[   13.477889] SCSI subsystem initialized
[   13.508469] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   13.508475] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   13.508487] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.508492] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.508523] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.508547] uhci_hcd 0000:00:1d.1: irq 11, io base 0x000018e0
[   13.508670] usb usb2: configuration #1 chosen from 1 choice
[   13.508696] hub 2-0:1.0: USB hub found
[   13.508701] hub 2-0:1.0: 2 ports detected
[   13.556071] libata version 3.00 loaded.
[   13.587582] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   13.587586] e100: Copyright(c) 1999-2006 Intel Corporation
[   13.612120] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.612134] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.612139] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.612164] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.612186] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001c00
[   13.612301] usb usb3: configuration #1 chosen from 1 choice
[   13.612326] hub 3-0:1.0: USB hub found
[   13.612331] hub 3-0:1.0: 2 ports detected
[   13.716117] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[   13.716360] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   13.716364] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   13.716379] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.716383] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.716410] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   13.720310] ehci_hcd 0000:00:1d.7: debug port 1
[   13.720316] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.720325] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x48080000
[   13.747891] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   13.759870] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.760000] usb usb4: configuration #1 chosen from 1 choice
[   13.760026] hub 4-0:1.0: USB hub found
[   13.760033] hub 4-0:1.0: 6 ports detected
[   13.864227] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   13.864232] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   13.888184] e100: eth0: e100_probe: addr 0xcfffe000, irq 11, MAC addr 00:0e:7b:06:0d:2c
[   13.888198] ata_piix 0000:00:1f.1: version 2.12
[   13.888212] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.888250] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.889251] scsi0 : ata_piix
[   13.889755] scsi1 : ata_piix
[   13.890177] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[   13.890180] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[   14.052104] ata1.00: ATA-6: FUJITSU MHT2040AT, 0022, max UDMA/100
[   14.052108] ata1.00: 78140160 sectors, multi 16: LBA 
[   14.067989] ata1.00: configured for UDMA/100
[   14.351290] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   14.529622] usb 1-1: configuration #1 chosen from 1 choice
[   14.543480] ata2.00: ATAPI: MATSHITADVD-RAM UJ-820S, 1.00, max UDMA/33
[   14.549337] usbcore: registered new interface driver hiddev
[   14.561793] input: Genius       NetScroll+Mini Traveler as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2
[   14.571102] input,hidraw0: USB HID v1.10 Mouse [Genius       NetScroll+Mini Traveler] on usb-0000:00:1d.0-1
[   14.571114] usbcore: registered new interface driver usbhid
[   14.571117] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   14.715236] ata2.00: configured for UDMA/33
[   14.715385] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2040A 0022 PQ: 0 ANSI: 5
[   14.717383] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-820S  1.00 PQ: 0 ANSI: 5
[   14.719710] PCI: Enabling device 0000:01:07.0 (0000 -> 0002)
[   14.719948] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[   14.719952] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[   14.769672] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[cff05000-cff057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   14.783957] Driver 'sd' needs updating - please use bus_type methods
[   14.784042] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   14.784056] sd 0:0:0:0: [sda] Write Protect is off
[   14.784058] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.784075] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.784125] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   14.784136] sd 0:0:0:0: [sda] Write Protect is off
[   14.784138] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.784154] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.784158]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   14.858069]  sda1 sda2 sda3 < sda5 sda6 sda7 >
[   14.907430] sd 0:0:0:0: [sda] Attached SCSI disk
[   14.913452] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.913472] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   14.919238] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   14.919243] Uniform CD-ROM driver Revision: 3.20
[   14.919290] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   16.041746] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00003900005bf439]
[   20.454451] EXT3-fs: INFO: recovery required on readonly filesystem.
[   20.454455] EXT3-fs: write access will be enabled during recovery.
[   21.052504] kjournald starting.  Commit interval 5 seconds
[   21.052522] EXT3-fs: sda5: orphan cleanup on readonly fs
[   21.052529] ext3_orphan_cleanup: deleting unreferenced inode 171754
[   21.052567] ext3_orphan_cleanup: deleting unreferenced inode 650328
[   21.052573] EXT3-fs: sda5: 2 orphan inodes deleted
[   21.052575] EXT3-fs: recovery complete.
[   21.073314] EXT3-fs: mounted filesystem with ordered data mode.
[   39.462702] Linux agpgart interface v0.102
[   39.598574] iTCO_vendor_support: vendor-support=0
[   39.654533] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   39.654626] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xd860)
[   39.654657] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   39.743244] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.806442] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.898341] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   40.043117] agpgart: Detected an Intel 855GM Chipset.
[   40.043737] agpgart: Detected 16252K stolen memory.
[   40.053869] agpgart: AGP aperture is 128M @ 0xd8000000
[   40.201967] intel_rng: FWH not detected
[   40.389904] input: Power Button (FF) as /devices/virtual/input/input4
[   40.405763] ACPI: Power Button (FF) [PWRF]
[   40.405854] input: Lid Switch as /devices/virtual/input/input5
[   40.405926] ACPI: Lid Switch [LID]
[   40.405973] input: Power Button (CM) as /devices/virtual/input/input6
[   40.417747] ACPI: Power Button (CM) [PWRB]
[   40.442474] ACPI: Battery Slot [BAT1] (battery present)
[   40.529806] ACPI: AC Adapter [ADP1] (on-line)
[   40.995587] ieee80211_crypt: registered algorithm 'NULL'
[   41.027311] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   41.027315] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   41.437448] input: PS/2 Mouse as /devices/virtual/input/input7
[   41.475457] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   41.724517] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   41.724522] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   41.724846] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[   41.724850] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[   41.764241] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   42.012673] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input9
[   42.040193] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   43.806716] ipw2200: Radio Frequency Kill Switch is On:
[   43.806719] Kill switch must be turned off for wireless networking to work.
[   43.807411] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   43.807448] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
[   43.934942] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   43.934947] Socket status: 30000007
[   43.934951] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   43.934955] cs: IO port probe 0xc000-0xcfff: clean.
[   43.935193] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
[   43.938707] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
[   43.938715] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   43.938736] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   44.307124] cs: IO port probe 0x100-0x3af: clean.
[   44.307950] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   44.308293] cs: IO port probe 0x820-0x8ff: clean.
[   44.308594] cs: IO port probe 0xc00-0xcf7: clean.
[   44.309022] cs: IO port probe 0xa00-0xaff: clean.
[   44.451216] NET: Registered protocol family 10
[   44.451443] lo: Disabled Privacy Extensions
[   44.451811] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.765483] intel8x0_measure_ac97_clock: measured 55451 usecs
[   44.765488] intel8x0: clocking to 48000
[   45.924155] lp: driver loaded but no devices found
[   46.194283] Adding 947792k swap on /dev/sda7.  Priority:-1 extents:1 across:947792k
[   46.759233] EXT3 FS on sda5, internal journal
[   50.724052] ip_tables: (C) 2000-2006 Netfilter Core Team
[   51.299871] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   51.299876] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[   51.300258] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   51.300261] toshiba_acpi: ktoshkeyd will check 2 times per second
[   51.300583] toshiba_acpi: Dropped 0 keys from the queue on startup
[   51.334348] No dock devices found.
[   53.100135] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   53.100140] apm: overridden by ACPI.
[   53.223529] ppdev: user-space parallel port driver
[   73.604577] audit(1220112743.930:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5099 profile="/usr/sbin/cupsd" namespace="default"
[  250.352007] Marking TSC unstable due to: cpufreq changes.
[  250.362590] Time: acpi_pm clocksource has been installed.
[  250.738408] Clocksource tsc unstable (delta = -241632148 ns)
[  254.824184] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  255.220792] Bluetooth: Core ver 2.11
[  255.221806] NET: Registered protocol family 31
[  255.221814] Bluetooth: HCI device and connection manager initialized
[  255.221823] Bluetooth: HCI socket layer initialized
[   95.771860] Bluetooth: L2CAP ver 2.9
[   95.771865] Bluetooth: L2CAP socket layer initialized
[   95.830377] Bluetooth: RFCOMM socket layer initialized
[   95.830394] Bluetooth: RFCOMM TTY layer initialized
[   95.830396] Bluetooth: RFCOMM ver 1.8
[   98.429835] [drm] Initialized drm 1.1.0 20060810
[   98.433417] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   98.433426] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   98.433490] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   98.433499] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
[   98.433504] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   98.433547] [drm] Initialized i915 1.6.0 20060119 on minor 1
```

---

### Post by Cheesehead on 2008-08-31
Ewww. (I hate reading through dmesg)

Again, try uninstalling CUPS and MTA (if you don't know what it is, you don't need it) and anything else you don't recognize...
...as long it's not a dependency of something you do recognize, of course.

I recommend using Synaptic so you have a record of your uninstalls in the File->History section.

Does that make a difference in your boot?

---

