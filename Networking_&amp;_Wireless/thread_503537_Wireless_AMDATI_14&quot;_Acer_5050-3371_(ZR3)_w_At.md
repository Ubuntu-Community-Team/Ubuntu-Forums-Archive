---
title: "Wireless AMD/ATI 14&quot; Acer 5050-3371 (ZR3) w/ Atheros AR5BXB63 using Ndiswrapper"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by aubreyisland on 2007-07-18
[COLOR="Red"]**Gusty Users, Please note Drivers:  [#post3882693]("http://ubuntuforums.org/showthread.php?p=3882693#post3882693")**[/COLOR]

So I'm going to let you in on about twenty minutes of my life. I was trying to delete a file in Vista when I hit 'More Details' and it said, "Speed: 0kb/second."

What?

So along with wireless problems and that happening consistently I decided to give _***Ubuntu Feisty Fawn 7.04***_ another try. I had installed in when I bought the computer, but didn't have the time to fix the wireless, plus I wanted to give Vista a fair try.

So how did I get wireless working? Alright, when Ubuntu Feisty Fawn booted for the first time I was made aware that a restricted driver "Atheros Hardware Access Layer (Hal)" was enabled for something to work, I disabled it assuming it was Ubuntu's default driver for the card, which did not work.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=38506&stc=1&d=1184735390[/IMG]

So I opted to use Ndiswrapper, but to make sure I had an Atheros card I typed ***lspci*** and found I had an " Atheros Communications, Inc. Unknown device 001c."

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=38507&stc=1&d=1184735495[/IMG]

I, at that point I referred to a number of How To's that were aimed at installing the Broadcom Driver, and I finally realized what I hadn't done before, install the Atheros Windows Driver, not the Broadcom! Doih!

So, next I downloaded the Acer 5070's Atheros Wireless Card Drivers (XP) from [this site.]("http://support.acer-euro.com/drivers/notebook/as_5570.html") I'd include the driver here, but I'm sure there's some legalities about it, so hopefully the link lasts out.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=38508&stc=1&d=1184735793[/IMG]

Then, of course, I extracted the files to the desktop...

Now I needed to blacklist Ubuntu's default Atheros Driver by typing the following in the terminal...

```
sudo echo "ath_pci" >> /etc/modprobe.d/blacklist
```Next, disable the driver by typing in the following in the terminal...

```
sudo rmmod ath_pci
```Next I needed to install Ndiswrapper...

```
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```Then I installed the Windows Drivers...

```
sudo ndiswrapper -i Desktop/Wireless\ Lan\ Driver\ 802abg\ Atheros\ Ver.5.3.0.45.zip_FILES/XP32_WHQL_5-3-0-45_\(Negative-Pole\)70510/***net5211.inf ***
```I got the following when I typed ***ndiswrapper -l***

```
aubrey@aubrey-laptop:~$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
aubrey@aubrey-laptop:~$ 
```Next I made sure the driver would load each time I started Ubuntu...

```
sudo modprobe ndiswrapper
sudo echo "ndiswrapper" >> /etc/modules
```Then I typed ***sudo gedit /etc/network/interfaces*** and edit the file to look something like...

```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```A quick reboot and walla' I could [use the Network Manager to select wireless networks]("http://ubuntuforums.org/attachment.php?attachmentid=38509&stc=1&d=1184736633"), I'm here at Village Inn using their open network...

One quirky think I found with the Network Manager, before you get to frustrated, was that I had to***_ select the network I wanted to connect to twice to get it to connect..._*** Wierd, but it works. I think it's because the roaming commands might not be the same as the commands executed when you actually select the network from the Network Manager Dropdown.

[SIZE=4]Hope it helps, please post your success stories below.[/SIZE]

My ***lspci***:
```

aubrey@aubrey-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
aubrey@aubrey-laptop:~$ 
aubrey@aubrey-laptop:~$ 


```My ***dmesg***:

```
aubrey@aubrey-laptop:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009dc00 end: 000000000009dc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009dc00 size: 0000000000002400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 0000000000030000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003bd90000 end: 000000003be90000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003be90000 size: 000000000000c000 end: 000000003be9c000 type: 3
[    0.000000] copy_e820_map() start: 000000003be9c000 size: 0000000000064000 end: 000000003bf00000 type: 4
[    0.000000] copy_e820_map() start: 000000003bf00000 size: 0000000004100000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003be90000 (usable)
[    0.000000]  BIOS-e820: 000000003be90000 - 000000003be9c000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003be9c000 - 000000003bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 62MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8a50
[    0.000000] Entering add_active_range(0, 0, 245392) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245392
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245392
[    0.000000] On node 0 totalpages: 245392
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 125 pages used for memmap
[    0.000000]   HighMem zone: 15891 pages, LIFO batch:3
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f8a20
[    0.000000] ACPI: RSDT (v001 ACRSYS ACRPRDCT 0x06040000  LTP 0x00000000) @ 0x3be94bec
[    0.000000] ACPI: FADT (v001 ATI    Bowfin   0x06040000 ATI  0x000f4240) @ 0x3be9bc36
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x3be9bcaa
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x3be9bde0
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x3be9be26
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3be9be62
[    0.000000] ACPI: SLIC (v001 ACRSYS ACRPRDCT 0x06040000 acer 0x00000000) @ 0x3be9be8a
[    0.000000] ACPI: DSDT (v001    ATI    SB460 0x06040000 MSFT 0x02000002) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 2200.271 MHz processor.
[   12.625957] Built 1 zonelists.  Total pages: 243475
[   12.625959] Kernel command line: root=UUID=5c6bf400-360d-49f9-b8c6-7e39b4cb00ed ro quiet splash
[   12.626072] mapped APIC to ffffd000 (fee00000)
[   12.626075] mapped IOAPIC to ffffc000 (fec00000)
[   12.626077] Enabling fast FPU save and restore... done.
[   12.626079] Enabling unmasked SIMD FPU exception support... done.
[   12.626085] Initializing CPU#0
[   12.626141] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   12.627071] Console: colour VGA+ 80x25
[   12.627343] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.627648] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.641371] Memory: 961716k/981568k available (1992k kernel code, 19176k reserved, 893k data, 328k init, 64064k highmem)
[   12.641380] virtual kernel memory layout:
[   12.641381]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   12.641382]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.641383]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   12.641384]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   12.641385]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   12.641386]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   12.641387]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   12.641390] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.718064] Calibrating delay using timer specific routine.. 4410.19 BogoMIPS (lpj=8820383)
[   12.718096] Security Framework v1.0.0 initialized
[   12.718101] SELinux:  Disabled at boot.
[   12.718113] Mount-cache hash table entries: 512
[   12.718216] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001d
[   12.718223] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.718225] CPU: L2 Cache: 512K (64 bytes/line)
[   12.718228] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001d
[   12.718236] Compat vDSO mapped to ffffe000.
[   12.718239] Remapping vsyscall page to ffffe000
[   12.718247] Checking 'hlt' instruction... OK.
[   12.734151] SMP alternatives: switching to UP code
[   12.734307] Freeing SMP alternatives: 11k freed
[   12.734467] Early unpacking initramfs... done
[   12.995699] ACPI: Core revision 20060707
[   12.999113] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   13.472795] CPU0: AMD Turion(tm) 64 Mobile Technology MK-38 stepping 02
[   13.472812] Total of 1 processors activated (4410.19 BogoMIPS).
[   13.472976] ENABLING IO-APIC IRQs
[   13.473155] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   13.617256] Brought up 1 CPUs
[   13.617414] Booting paravirtualized kernel on bare hardware
[   13.617491] Time:  4:45:53  Date: 06/18/107
[   13.617512] NET: Registered protocol family 16
[   13.617572] EISA bus registered
[   13.617575] ACPI: bus type pci registered
[   13.633269] PCI: BIOS BUG #81[49435000] found
[   13.633311] PCI: Using configuration type 1
[   13.633313] Setting up standard PCI resources
[   13.639334] ACPI: Interpreter enabled
[   13.639337] ACPI: Using IOAPIC for interrupt routing
[   13.639664] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.639668] PCI: Probing PCI hardware (bus 00)
[   13.641225] Boot video device is 0000:01:05.0
[   13.642116] PCI: Transparent bridge - 0000:00:14.4
[   13.642183] PCI: Bus #09 (-#0c) is hidden behind transparent bridge #08 (-#09) (try 'pci=assign-busses')
[   13.642185] Please report the result to linux-kernel to fix this permanently
[   13.642223] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.644570] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   13.644742] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   13.644911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   13.645126] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   13.646261] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   13.646472] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   13.646682] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   13.646891] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   13.647101] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   13.647312] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   13.647522] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   13.647731] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   13.647940] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   13.668685] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   13.668920] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   13.669354] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.669361] pnp: PnP ACPI init
[   13.671557] pnp: PnP ACPI: found 10 devices
[   13.671560] PnPBIOS: Disabled by ACPI PNP
[   13.671596] PCI: Using ACPI for IRQ routing
[   13.671598] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.671604] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   13.671605] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   13.671608] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[   13.671610] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[   13.671612] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[   13.671614] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
[   13.671711] NET: Registered protocol family 8
[   13.671712] NET: Registered protocol family 20
[   13.671907] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   13.671910] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   13.672094] PCI: Bridge: 0000:00:01.0
[   13.672096]   IO window: 9000-9fff
[   13.672099]   MEM window: d0100000-d01fffff
[   13.672102]   PREFETCH window: d4000000-d7ffffff
[   13.672105] PCI: Bridge: 0000:00:04.0
[   13.672106]   IO window: disabled.
[   13.672108]   MEM window: d0200000-d02fffff
[   13.672110]   PREFETCH window: disabled.
[   13.672113] PCI: Bridge: 0000:00:05.0
[   13.672114]   IO window: disabled.
[   13.672116]   MEM window: disabled.
[   13.672118]   PREFETCH window: disabled.
[   13.672120] PCI: Bridge: 0000:00:06.0
[   13.672121]   IO window: disabled.
[   13.672123]   MEM window: disabled.
[   13.672125]   PREFETCH window: disabled.
[   13.672127] PCI: Bridge: 0000:00:07.0
[   13.672129]   IO window: disabled.
[   13.672131]   MEM window: disabled.
[   13.672132]   PREFETCH window: disabled.
[   13.672145] PCI: Bus 9, cardbus bridge: 0000:08:01.0
[   13.672147]   IO window: 0000a400-0000a4ff
[   13.672152]   IO window: 0000a800-0000a8ff
[   13.672158]   PREFETCH window: 50000000-53ffffff
[   13.672163]   MEM window: 58000000-5bffffff
[   13.672168] PCI: Bridge: 0000:00:14.4
[   13.672171]   IO window: a000-afff
[   13.672177]   MEM window: d0300000-d03fffff
[   13.672182]   PREFETCH window: 50000000-53ffffff
[   13.672198] PCI: Enabling device 0000:00:04.0 (0000 -> 0002)
[   13.672202] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   13.672208] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   13.672214] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   13.672220] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   13.672243] PCI: Enabling device 0000:08:01.0 (0000 -> 0003)
[   13.672251] ACPI: PCI Interrupt 0000:08:01.0[A] -> GSI 23 (level, low) -> IRQ 16
[   13.672278] NET: Registered protocol family 2
[   13.709196] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.709314] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.709903] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.710166] TCP: Hash tables configured (established 131072 bind 65536)
[   13.710168] TCP reno registered
[   13.721228] checking if image is initramfs... it is
[   14.233298] Freeing initrd memory: 7005k freed
[   14.233421] Simple Boot Flag at 0x36 set to 0x1
[   14.233614] audit: initializing netlink socket (disabled)
[   14.233624] audit(1184733953.220:1): initialized
[   14.233667] highmem bounce pool size: 64 pages
[   14.233716] VFS: Disk quotas dquot_6.5.1
[   14.233731] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.233770] io scheduler noop registered
[   14.233772] io scheduler anticipatory registered
[   14.233773] io scheduler deadline registered
[   14.233783] io scheduler cfq registered (default)
[   14.233962] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   14.233981] assign_interrupt_mode Found MSI capability
[   14.233983] Allocate Port Service[0000:00:04.0:pcie00]
[   14.234005] Allocate Port Service[0000:00:04.0:pcie02]
[   14.234057] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   14.234074] assign_interrupt_mode Found MSI capability
[   14.234076] Allocate Port Service[0000:00:05.0:pcie00]
[   14.234126] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   14.234143] assign_interrupt_mode Found MSI capability
[   14.234145] Allocate Port Service[0000:00:06.0:pcie00]
[   14.234196] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   14.234214] assign_interrupt_mode Found MSI capability
[   14.234216] Allocate Port Service[0000:00:07.0:pcie00]
[   14.234305] isapnp: Scanning for PnP cards...
[   14.590886] isapnp: No Plug & Play device found
[   14.612988] Real Time Clock Driver v1.12ac
[   14.613020] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.613597] mice: PS/2 mouse device common for all mice
[   14.613947] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.614100] input: Macintosh mouse button emulation as /class/input/input0
[   14.614124] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.614127] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.614347] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   14.616953] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.619948] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.619951] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.619953] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.619955] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.619957] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.620047] EISA: Probing bus 0 at eisa.0
[   14.620055] Cannot allocate resource for EISA slot 1
[   14.620081] Cannot allocate resource for EISA slot 8
[   14.620082] EISA: Detected 0 cards.
[   14.650129] TCP cubic registered
[   14.650134] NET: Registered protocol family 1
[   14.650150] Using IPI No-Shortcut mode
[   14.650194] ACPI: (supports S0 S3 S4 S5)
[   14.650231]   Magic number: 15:16:768
[   14.650322]   hash matches device ptyp4
[   14.650524] Freeing unused kernel memory: 328k freed
[   14.652263] Time: tsc clocksource has been installed.
[   14.667129] input: AT Translated Set 2 keyboard as /class/input/input1
[   15.865127] Capability LSM initialized
[   15.897409] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   15.901025] ACPI: Thermal Zone [THRM] (35 C)
[   16.357705] usbcore: registered new interface driver usbfs
[   16.357722] usbcore: registered new interface driver hub
[   16.357737] usbcore: registered new device driver usb
[   16.358243] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.358270] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[   16.358282] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   16.358385] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   16.358406] ohci_hcd 0000:00:13.0: irq 17, io mem 0xd0005000
[   16.392534] SCSI subsystem initialized
[   16.396082] libata version 2.20 loaded.
[   16.438774] usb usb1: configuration #1 chosen from 1 choice
[   16.438794] hub 1-0:1.0: USB hub found
[   16.438808] hub 1-0:1.0: 4 ports detected
[   16.490730] 8139too Fast Ethernet driver 0.9.28
[   16.546500] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[   16.546515] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   16.546533] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   16.546548] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd0006000
[   16.606443] usb usb2: configuration #1 chosen from 1 choice
[   16.606464] hub 2-0:1.0: USB hub found
[   16.606475] hub 2-0:1.0: 4 ports detected
[   16.714775] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[   16.714787] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   16.714806] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   16.714850] ehci_hcd 0000:00:13.2: irq 17, io mem 0xd0007000
[   16.714862] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.714918] usb usb3: configuration #1 chosen from 1 choice
[   16.714938] hub 3-0:1.0: USB hub found
[   16.714943] hub 3-0:1.0: 8 ports detected
[   16.823954] sata_sil 0000:00:12.0: version 2.2
[   16.823978] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[   16.823986] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[   16.825049] ata1: SATA max UDMA/100 cmd 0xf8862080 ctl 0xf886208a bmdma 0xf8862000 irq 18
[   16.828103] ata2: SATA max UDMA/100 cmd 0xf88620c0 ctl 0xf88620ca bmdma 0xf8862008 irq 18
[   16.828124] scsi0 : sata_sil
[   17.297682] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   17.310266] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   17.310270] ata1.00: ATA-7: SAMSUNG HM080HI, AB100-16, max UDMA/100
[   17.310273] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   17.322245] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   17.322248] ata1.00: configured for UDMA/100
[   17.322260] scsi1 : sata_sil
[   17.637320] ata2: SATA link down (SStatus 0 SControl 310)
[   17.637406] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM080HI  AB10 PQ: 0 ANSI: 5
[   17.638447] ACPI: PCI Interrupt 0000:08:02.0[A] -> GSI 20 (level, low) -> IRQ 19
[   17.639160] eth0: RealTek RTL8139 at 0xf8852c00, 00:16:36:fe:df:be, IRQ 19
[   17.639162] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   17.641486] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   17.643475] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   17.643496] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 20
[   17.643505] ATIIXP: chipset revision 128
[   17.643507] ATIIXP: not 100% native mode: will probe irqs later
[   17.643515]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[   17.643529] ATIIXP: simplex device: DMA disabled
[   17.643531] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
[   17.643534] Probing IDE interface ide0...
[   17.660625] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   17.660635] sda: Write Protect is off
[   17.660637] sda: Mode Sense: 00 3a 00 00
[   17.660648] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.660684] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   17.660691] sda: Write Protect is off
[   17.660692] sda: Mode Sense: 00 3a 00 00
[   17.660702] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.660705]  sda: sda1 sda2 < sda5 >
[   18.224331] sd 0:0:0:0: Attached scsi disk sda
[   18.227813] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.381036] hda: HL-DT-ST DVDRAM GSA-T10N, ATAPI CD/DVD-ROM drive
[   18.472578] Attempting manual resume
[   18.472581] swsusp: Resume From Partition 8:5
[   18.472582] PM: Checking swsusp image.
[   18.472827] PM: Resume from disk failed.
[   18.484497] EXT3-fs: INFO: recovery required on readonly filesystem.
[   18.484500] EXT3-fs: write access will be enabled during recovery.
[   18.721132] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   18.724572] Probing IDE interface ide1...
[   19.296280] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   19.296287] Uniform CD-ROM driver Revision: 3.20
[   21.303987] kjournald starting.  Commit interval 5 seconds
[   21.304000] EXT3-fs: recovery complete.
[   21.304859] EXT3-fs: mounted filesystem with ordered data mode.
[   30.430223] Linux agpgart interface v0.102 (c) Dave Jones
[   30.449949] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.451916] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.865341] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   30.883540] Yenta: CardBus bridge found at 0000:08:01.0 [1025:010f]
[   30.883570] Yenta: Using CSCINT to route CSC interrupts to PCI
[   30.883571] Yenta: Routing CardBus interrupts to PCI
[   30.883577] Yenta TI: socket 0000:08:01.0, mfunc 0x00001202, devctl 0x44
[   31.061122] sdhci: Secure Digital Host Controller Interface driver
[   31.061125] sdhci: Copyright(c) Pierre Ossman
[   31.116929] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   31.116939] Socket status: 30000006
[   31.116942] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[   31.116948] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   31.116950] cs: IO port probe 0xa000-0xafff: clean.
[   31.117174] pcmcia: parent PCI bridge Memory window: 0xd0300000 - 0xd03fffff
[   31.117176] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   31.131509] sdhci: SDHCI controller found at 0000:08:01.2 [1524:0550] (rev 1)
[   31.131533] ACPI: PCI Interrupt 0000:08:01.2[b] -> GSI 22 (level, low) -> IRQ 18
[   31.131625] mmc0: SDHCI at 0xd0301400 irq 18 DMA
[   31.371882] input: PC Speaker as /class/input/input2
[   31.540928] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 20
[   31.693856] cs: IO port probe 0x100-0x3af: clean.
[   31.697249] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[   31.698204] cs: IO port probe 0x820-0x8ff: clean.
[   31.699066] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   31.699916] cs: IO port probe 0xa00-0xaff: clean.
[   31.783072] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   31.832574] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   31.993594] fuse init (API version 7.8)
[   32.044028] lp: driver loaded but no devices found
[   32.082057] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   32.235745] ndiswrapper: driver net5211 (,05/02/2007,5.3.0.45) loaded
[   32.262942] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   32.262949] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   32.262988] ndiswrapper (ZwClose:2467): closing handle 0xdf9d37a8 not implemented
[   32.263140] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   32.678767] ndiswrapper: using IRQ 20
[   33.183214] wlan0: ethernet device 00:19:7e:29:3f:a0 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: '', 168C:001C.5.conf
[   33.183232] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   33.192761] usbcore: registered new interface driver ndiswrapper
[   33.219330] Adding 2835432k swap on /dev/disk/by-uuid/5118d40d-c61f-4e03-95ef-d8e444c05001.  Priority:-1 extents:1 across:2835432k
[   33.338765] EXT3 FS on sda1, internal journal
[   33.749329] Using specific hotkey driver
[   33.774181] ACPI: AC Adapter [ACAD] (off-line)
[   33.837868] ibm_acpi: ec object not found
[   33.929284] input: Power Button (FF) as /class/input/input4
[   33.932339] ACPI: Power Button (FF) [PWRF]
[   33.958117] input: Power Button (CM) as /class/input/input5
[   33.961091] ACPI: Power Button (CM) [PWRB]
[   33.986865] input: Lid Switch as /class/input/input6
[   33.989799] ACPI: Lid Switch [LID]
[   34.016001] input: Sleep Button (CM) as /class/input/input7
[   34.018949] ACPI: Sleep Button (CM) [SLPB]
[   34.032577] No dock devices found.
[   34.063198] ACPI: Battery Slot [BAT1] (battery present)
[   34.088702] wmi_add device=c1942000
[   34.088705] calling WQBA
[   34.102829] pcc_acpi: loading...
[   34.311269] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-38 processors (version 2.00.00)
[   34.311305] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xd
[   34.311307] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xf
[   34.311309] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x11
[   34.311311] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0x13
[   34.311313] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x18
[   37.131511] eth0: link down
[   38.464137] [fglrx] Maximum main memory to use for locked dma buffers: 865 MBytes.
[   38.464402] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   38.467654] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 21
[   39.100410] ppdev: user-space parallel port driver
[   40.276924] [fglrx] total      GART = 130023424
[   40.276930] [fglrx] free       GART = 114032640
[   40.276932] [fglrx] max single GART = 114032640
[   40.276934] [fglrx] total      LFB  = 67108864
[   40.276935] [fglrx] free       LFB  = 52719616
[   40.276937] [fglrx] max single LFB  = 52719616
[   40.276939] [fglrx] total      Inv  = 0
[   40.276940] [fglrx] free       Inv  = 0
[   40.276941] [fglrx] max single Inv  = 0
[   40.276943] [fglrx] total      TIM  = 0
[   40.301554] apm: BIOS not found.
[   40.570481] Bluetooth: Core ver 2.11
[   40.570721] NET: Registered protocol family 31
[   40.570723] Bluetooth: HCI device and connection manager initialized
[   40.570727] Bluetooth: HCI socket layer initialized
[   40.652461] Bluetooth: L2CAP ver 2.8
[   40.652464] Bluetooth: L2CAP socket layer initialized
[   40.786325] Bluetooth: RFCOMM socket layer initialized
[   40.786336] Bluetooth: RFCOMM TTY layer initialized
[   40.786338] Bluetooth: RFCOMM ver 1.8
[   27.624000] Time: acpi_pm clocksource has been installed.
[   31.748000] hda-intel: Invalid position buffer, using LPIB read method instead.
[   38.812000] NET: Registered protocol family 10
[   38.812000] lo: Disabled Privacy Extensions
[   38.812000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.728000] wlan0: no IPv6 routers present
[  100.772000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  100.812000] NET: Registered protocol family 17
[  105.180000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  106.084000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  122.380000] wlan0: no IPv6 routers present
[ 1182.092000] atkbd.c: Unknown key pressed (translated set 2, code 0xb3 on isa0060/serio0).
[ 1182.092000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
[ 1182.240000] atkbd.c: Unknown key released (translated set 2, code 0xb3 on isa0060/serio0).
[ 1182.240000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
[ 1968.672000] atkbd.c: Unknown key pressed (translated set 2, code 0xb4 on isa0060/serio0).
[ 1968.672000] atkbd.c: Use 'setkeycodes e034 <keycode>' to make it known.
[ 1968.784000] atkbd.c: Unknown key released (translated set 2, code 0xb4 on isa0060/serio0).
[ 1968.784000] atkbd.c: Use 'setkeycodes e034 <keycode>' to make it known.

```Note: The end of this dmesg shows when I flip the wireless trigger in front of the lappy, which kind of shows up as a keystroke that is unrecognised. Flipping it does nothing to the wireless...

---

### Post by jarrett on 2007-07-18
you need to use the acerchk driver to turn the wireless on:
[http://code.google.com/p/aceracpi/]("http://code.google.com/p/aceracpi/") .. download drivers from there, and then install them using this guide: [http://ubuntuforums.org/showpost.php?p=2999631&postcount=1595]("http://ubuntuforums.org/showpost.php?p=2999631&postcount=1595")

---

### Post by aubreyisland on 2007-07-18
No Thankyou, this way worked!

---

### Post by BudaAlien on 2007-09-26
After many headaches and surfing the threads here, many of which are very good, THIS one was the one to fix the wifi. Thank you aubreyisland, for you have made my night! I have an acer aspire 3680-2633 and with the inclusion of this how-to I have almost everything working. ...

Yes almost.

My sound is inextricably linked, front + headphones. I have alsa mixer running, surround checked and added a line to /etc/modprobe.d/alsa-base to make it 6ch. The front + headphones work, together, in 2ch mode, while only the headphones work in 6ch mode. Anyone have any ideas? Once again thank you very much for the wifi fix!

---

