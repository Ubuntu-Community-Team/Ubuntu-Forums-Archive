---
title: "Weird network problem"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by jesse_adkins on 2007-09-07
Greetings, everyone.

I've had this tricky problem for a while now, and i've exausted every possible idea I can think of as to how it can be fixed. Since I don't have a clue as to what exactly is causing it, i'm posting here.


The first time I boot my computer, everything is normal. I dual-boot Windows and Linux, pick Linux and everything loads fine. I login without a problem, and then cruise the web. Everything is perfect. It's only when I shut down that everything goes funny.

When it reverts to a text screen, I usually get some message about 'nm_print_sockets failed to close' and HAL failing to shutdown. There's also an error with cat (Something about failing to copy to cpu_frequency or something like that. I think it's because of a double / in the path.). After that, everything seems to shut down fine.

It's when I turn on the computer the next time that the problem starts. It boots up normally like before, etc, etc. However, the internet won't connect. Odd. I go to the little internet icon and tell it to reload. That doesn't work. I try it a few times, and still nothing.

Later on, I get the idea to try a command-line way of doing it. 'sudo sh /etc/init.d/networking force-restart'. This is where it gets interesting. See, now i'm getting messages about the DHCP server hanging and the port failing to connect. Ironically, it still manages to print that little box saying everything's okay at the end.

Some time goes by and I learn about ifconfig, since i'm still new to this. New tool in hand, I decide to check the status before and after. This is where the problem gets really strange, I think. See, everything is perfect before and after. MTU is the same, and so are all of the other numbers I don't really understand. Except for one. One item has changed.

The base address of the device is something completely different. I've no idea how to fix this or why it's happening. Looking through the web hasn't helped at all.

Out of curiosity, I decided to see if Windows had the problem too. Well, maybe more desperation than curiosity. Sure enough, Windows has problems with this too. This leads me to the BIOS, since it is the only thing which appears as if it can be the cause.

Here I find what is probably the root cause. I notice that when Linux boots then shuts down, a setting in my BIOS is gone. Not moved around to another submenu or hidden, but gone. I can't load it back in unless I insert/remove a PCI card or flip the BIOS. 

My question to all of you is this : How do I fix this? I'm tired of having to reset my BIOS every time I boot Linux. I have no idea how to fix it, nor what tool could be causing this.

Specs :
	Processor : Intel Core 2 Duo E6300
	Motherboard : ECS P4M800Pro-M
	BIOS : v 02.59 by American Megatrends
	Router : Motorola SB5100 Surfboard

---

### Post by noob12 on 2007-09-07
What is the setting that is going away in the BIOS?

The answer might be in the boot flag arcana controlling ACPI behavior.

---

### Post by jesse_adkins on 2007-09-08
The missing setting is 'Ethernet Device', which has a default of being enabled. It has a subentry called 'OnBoard LAN Boot Rom' which is usually disabled.

---

### Post by noob12 on 2007-09-08
I suggest you try booting once with the flag **acpi=off**.  That's a broad hammer approach to seeing if ACPI is causing the issue.  If it is we may be able to narrow down to specific flags to address your issue.

To set options for a one-time boot.  While the grub boot menu is displaying during the boot sequence, hit **e**.  Arrow down to the **kernel** line.  Hit **e** again.  Enter a space and the options.  Hit Enter and **b** to boot.

Running
```

dmesg | grep 'Kernel command line'

```
after your boot will verify whether you correctly applied the option or not.

---

### Post by jesse_adkins on 2007-09-08
Tried that just now, but it didn't work. I did the code you suggested to make sure I had done it right and acpi=off was at the end.

I noticed that when I shutdown with acpi=off set, my computer froze after the 'will now halt' message. Didn't seem to hurt anything though.

With it on, the problem was just like before.Fine for the first boot, but after booting up again and checking the BIOS entry and subentry were gone again.

---

### Post by noob12 on 2007-09-08
OK.  If you did that all right, and that didn't do anything, then I am not sure how to stop the behavior you're seeing with the BIOS entry disappearing.  Maybe another forum reader can chime in?

---

### Post by noob12 on 2007-09-09
> 
With it on, the problem was just like before.Fine for the first boot, but after booting up again and checking the BIOS entry and subentry were gone again.


I just noticed this line that I may not have interpreted correctly.  The boot flag you added is only supposed to work for the one boot you did it on.  So are you saying that this solved the problem in that one boot, but not on subsequent ones?  That's what I was hoping for, because it then does indicate we need to look for an appropriate ACPI boot flag to use.  Otherwise, I am out of ideas.

---

### Post by jesse_adkins on 2007-09-09
I reset my BIOS before doing the whole test, then set the flag and booted Ubuntu. Everything went down like normal, with network being available. It's after the first shutdown that the BIOS entries get wiped.

After shutting down, I checked on the settings and everything was like normal. The acpi=off flag didn't stop those BIOS settings from getting cleared.

Perhaps I could try using acpi=off after the BIOS settings have been cleared, to see if it helps any.

---

### Post by noob12 on 2007-09-09
Sure, you could try that, maybe we'll be pleasantly surprised.  I was really hoping for the BIOS setting to be left intact on the acpi=off boot, but it sounds like it wasn't, so my original theory is blown.  I have no real idea of what is going on in this case.

---

### Post by noob12 on 2007-09-09
Can you post your full **dmesg** after a normal (no special flags) boot?  Maybe we'll see something interesting.

---

### Post by jesse_adkins on 2007-09-09
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e6000 size: 000000000001a000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001dec0000 end: 000000001dfc0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001dfc0000 size: 000000000000e000 end: 000000001dfce000 type: 3
[    0.000000] copy_e820_map() start: 000000001dfce000 size: 0000000000022000 end: 000000001dff0000 type: 4
[    0.000000] copy_e820_map() start: 000000001dff0000 size: 0000000000010000 end: 000000001e000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dfc0000 (usable)
[    0.000000]  BIOS-e820: 000000001dfc0000 - 000000001dfce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001dfce000 - 000000001dff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 122816) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   122816
[    0.000000]   HighMem    122816 ->   122816
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   122816
[    0.000000] On node 0 totalpages: 122816
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 927 pages used for memmap
[    0.000000]   Normal zone: 117793 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f8760
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x07000619 MSFT 0x00000097) @ 0x1dfc0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x07000619 MSFT 0x00000097) @ 0x1dfc0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x07000619 MSFT 0x00000097) @ 0x1dfc0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x07000619 MSFT 0x00000097) @ 0x1dfce040
[    0.000000] ACPI: DSDT (v001  12345 12345123 0x00000123 INTL 0x20051117) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
[    0.000000] Detected 1863.051 MHz processor.
[   29.517321] Built 1 zonelists.  Total pages: 121857
[   29.517326] Kernel command line: root=UUID=80952c30-90a0-4bf5-8ffb-8991924ef26c ro quiet splash
[   29.517470] mapped APIC to ffffd000 (fee00000)
[   29.517472] mapped IOAPIC to ffffc000 (fec00000)
[   29.517475] Enabling fast FPU save and restore... done.
[   29.517477] Enabling unmasked SIMD FPU exception support... done.
[   29.517486] Initializing CPU#0
[   29.517587] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   29.518849] Console: colour VGA+ 80x25
[   29.519021] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   29.519170] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   29.531580] Memory: 475960k/491264k available (1993k kernel code, 14720k reserved, 900k data, 328k init, 0k highmem)
[   29.531588] virtual kernel memory layout:
[   29.531589]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   29.531590]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   29.531591]     vmalloc : 0xde800000 - 0xff7fe000   ( 527 MB)
[   29.531592]     lowmem  : 0xc0000000 - 0xddfc0000   ( 479 MB)
[   29.531593]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   29.531594]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   29.531595]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   29.531598] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   29.609494] Calibrating delay using timer specific routine.. 3730.73 BogoMIPS (lpj=7461467)
[   29.609527] Security Framework v1.0.0 initialized
[   29.609532] SELinux:  Disabled at boot.
[   29.609545] Mount-cache hash table entries: 512
[   29.609652] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   29.609659] monitor/mwait feature present.
[   29.609661] using mwait in idle threads.
[   29.609664] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.609666] CPU: L2 cache: 2048K
[   29.609669] CPU: Physical Processor ID: 0
[   29.609670] CPU: Processor Core ID: 0
[   29.609672] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   29.609679] Compat vDSO mapped to ffffe000.
[   29.609682] Remapping vsyscall page to ffffe000
[   29.609692] Checking 'hlt' instruction... OK.
[   29.625550] SMP alternatives: switching to UP code
[   29.625815] Early unpacking initramfs... done
[   29.907548] ACPI: Core revision 20060707
[   29.907758] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   29.909744] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[   29.909760] SMP alternatives: switching to SMP code
[   29.909846] Booting processor 1/1 eip 3000
[   29.920311] Initializing CPU#1
[   30.001055] Calibrating delay using timer specific routine.. 3726.34 BogoMIPS (lpj=7452691)
[   30.001061] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   30.001066] monitor/mwait feature present.
[   30.001068] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.001070] CPU: L2 cache: 2048K
[   30.001072] CPU: Physical Processor ID: 0
[   30.001073] CPU: Processor Core ID: 1
[   30.001074] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   30.001494] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[   30.001516] Total of 2 processors activated (7457.07 BogoMIPS).
[   30.002266] ENABLING IO-APIC IRQs
[   30.002591] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   30.148902] checking TSC synchronization across 2 CPUs: passed.
[    0.004000] Brought up 2 CPUs
[    0.392266] migration_cost=230
[    0.392500] Booting paravirtualized kernel on bare hardware
[    0.392601] Time:  9:28:07  Date: 08/09/107
[    0.392624] NET: Registered protocol family 16
[    0.392698] EISA bus registered
[    0.392702] ACPI: bus type pci registered
[    0.392839] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=1
[    0.392841] PCI: Using configuration type 1
[    0.392842] Setting up standard PCI resources
[    0.400688] ACPI: Interpreter enabled
[    0.400690] ACPI: Using IOAPIC for interrupt routing
[    0.401240] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.401244] PCI: Probing PCI hardware (bus 00)
[    0.402372] Boot video device is 0000:01:00.0
[    0.402422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.415601] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.424787] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.425001] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.425215] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.425427] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.425693] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.425907] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.426119] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.426331] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.426442] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.426454] pnp: PnP ACPI init
[    0.432126] pnp: PnP ACPI: found 13 devices
[    0.432130] PnPBIOS: Disabled by ACPI PNP
[    0.432170] PCI: Using ACPI for IRQ routing
[    0.432172] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.437741] NET: Registered protocol family 8
[    0.437743] NET: Registered protocol family 20
[    0.438488] pnp: 00:09: ioport range 0xa00-0xa0f has been reserved
[    0.438490] pnp: 00:09: ioport range 0x290-0x29f has been reserved
[    0.438493] pnp: 00:09: ioport range 0xa20-0xa2f has been reserved
[    0.438495] pnp: 00:09: ioport range 0xa30-0xa3f has been reserved
[    0.438744] PCI: Bridge: 0000:00:01.0
[    0.438745]   IO window: disabled.
[    0.438750]   MEM window: fca00000-feafffff
[    0.438754]   PREFETCH window: eff00000-f7efffff
[    0.438771] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.438794] NET: Registered protocol family 2
[    0.479498] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.479569] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.479633] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.479663] TCP: Hash tables configured (established 16384 bind 8192)
[    0.479666] TCP reno registered
[    0.491537] checking if image is initramfs... it is
[    1.050065] Freeing initrd memory: 6751k freed
[    1.050743] audit: initializing netlink socket (disabled)
[    1.050768] audit(1189330087.760:1): initialized
[    1.050968] VFS: Disk quotas dquot_6.5.1
[    1.050993] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.051056] io scheduler noop registered
[    1.051058] io scheduler anticipatory registered
[    1.051060] io scheduler deadline registered
[    1.051070] io scheduler cfq registered (default)
[    1.051150] PCI: Bypassing VIA 8237 APIC De-Assert Message
[    1.051383] isapnp: Scanning for PnP cards...
[    1.404873] isapnp: No Plug & Play device found
[    1.424018] Real Time Clock Driver v1.12ac
[    1.424079] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.424195] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.424311] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.424821] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.424999] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.425163] mice: PS/2 mouse device common for all mice
[    1.425724] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.425870] input: Macintosh mouse button emulation as /class/input/input0
[    1.425903] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.425906] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.426181] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.426183] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    1.427182] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.427186] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.427273] EISA: Probing bus 0 at eisa.0
[    1.427313] EISA: Detected 0 cards.
[    1.457457] TCP cubic registered
[    1.457467] NET: Registered protocol family 1
[    1.457488] Starting balanced_irq
[    1.457495] Using IPI No-Shortcut mode
[    1.457626] ACPI: (supports S0 S1 S3 S4 S5)
[    1.457664]   Magic number: 7:572:474
[    1.458046] Freeing unused kernel memory: 328k freed
[    1.458373] Time: tsc clocksource has been installed.
[    2.622880] Capability LSM initialized
[    2.653178] ACPI: Processor [CPU1] (supports 16 throttling states)
[    2.653243] ACPI: Processor [CPU2] (supports 16 throttling states)
[    2.653251] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.653257] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.654032] ACPI: Thermal Zone [THRM] (30 C)
[    2.947160] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[    2.947193] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
[    2.947209] VP_IDE: chipset revision 6
[    2.947212] VP_IDE: not 100% native mode: will probe irqs later
[    2.947223] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[    2.947234]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[    2.947244]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[    2.947250] Probing IDE interface ide0...
[    2.959839] usbcore: registered new interface driver usbfs
[    2.959868] usbcore: registered new interface driver hub
[    2.989032] usbcore: registered new device driver usb
[    2.990010] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[    2.995107] SCSI subsystem initialized
[    2.999815] libata version 2.20 loaded.
[    3.001661] USB Universal Host Controller Interface driver v3.0
[    3.524048] Probing IDE interface ide1...
[    4.096100] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 17
[    4.100192] eth0: VIA Rhine II at 0x1c400, 00:19:21:09:46:67, IRQ 17.
[    4.100908] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[    4.102947] sata_via 0000:00:0f.0: version 2.1
[    4.102964] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
[    4.102979] sata_via 0000:00:0f.0: routed to hard irq line 11
[    4.103033] ata1: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e882 bmdma 0x0001e400 irq 16
[    4.103055] ata2: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e482 bmdma 0x0001e408 irq 16
[    4.103070] scsi0 : sata_via
[    4.307165] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    4.317771] ATA: abnormal status 0x7F on port 0x0001ec07
[    4.317785] scsi1 : sata_via
[    4.522923] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.693374] ATA: abnormal status 0x7F on port 0x0001e807
[    4.704012] ATA: abnormal status 0x7F on port 0x0001e807
[    4.756004] ata2.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
[    4.756009] ata2.00: ATA-7: ST3300620AS, 3.AAE, max UDMA/133
[    4.756011] ata2.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.822543] ata2.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
[    4.822546] ata2.00: configured for UDMA/133
[    4.823312] scsi 1:0:0:0: Direct-Access     ATA      ST3300620AS      3.AA PQ: 0 ANSI: 5
[    4.824084] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 18
[    4.824095] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    4.824252] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    4.824279] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000dc00
[    4.824393] usb usb1: configuration #1 chosen from 1 choice
[    4.824416] hub 1-0:1.0: USB hub found
[    4.824423] hub 1-0:1.0: 2 ports detected
[    4.830108] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[    4.830118] sda: Write Protect is off
[    4.830120] sda: Mode Sense: 00 3a 00 00
[    4.830133] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.830174] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[    4.830181] sda: Write Protect is off
[    4.830183] sda: Mode Sense: 00 3a 00 00
[    4.830195] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.830197]  sda: sda1 sda2 sda3
[    4.862230] sd 1:0:0:0: Attached scsi disk sda
[    4.865311] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    4.930622] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 18
[    4.930636] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    4.930662] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    4.930684] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000d880
[    4.930769] usb usb2: configuration #1 chosen from 1 choice
[    4.930797] hub 2-0:1.0: USB hub found
[    4.930802] hub 2-0:1.0: 2 ports detected
[    5.038473] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 18
[    5.038487] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    5.038512] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    5.038536] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000d800
[    5.038623] usb usb3: configuration #1 chosen from 1 choice
[    5.038651] hub 3-0:1.0: USB hub found
[    5.038656] hub 3-0:1.0: 2 ports detected
[    5.146331] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 18
[    5.146344] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    5.146363] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    5.146384] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000d480
[    5.146460] usb usb4: configuration #1 chosen from 1 choice
[    5.146487] hub 4-0:1.0: USB hub found
[    5.146492] hub 4-0:1.0: 2 ports detected
[    5.174196] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    5.254272] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 18
[    5.254283] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    5.254303] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    5.254331] ehci_hcd 0000:00:10.4: irq 18, io mem 0xfebfec00
[    5.254337] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.254406] usb usb5: configuration #1 chosen from 1 choice
[    5.254427] hub 5-0:1.0: USB hub found
[    5.254443] hub 5-0:1.0: 8 ports detected
[    5.709593] usb 1-1: device not accepting address 2, error -71
[    7.271846] usb 1-1: new low speed USB device using uhci_hcd and address 4
[    7.457301] usb 1-1: configuration #1 chosen from 1 choice
[    7.707354] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    7.885311] usb 2-2: configuration #1 chosen from 1 choice
[   12.164160] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   13.119986] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.121457] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.141821] input: PC Speaker as /class/input/input1
[   13.155090] Linux agpgart interface v0.102 (c) Dave Jones
[   13.156411] agpgart: Detected VIA VT3314 chipset
[   13.160115] agpgart: AGP aperture is 64M @ 0xf8000000
[   13.402440] parport: PnPBIOS parport detected.
[   13.402510] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   13.476983] NET: Registered protocol family 17
[   13.493867] usbcore: registered new interface driver hiddev
[   13.521714] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 19
[   13.613668] input: Logitech USB Receiver as /class/input/input2
[   13.613711] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:10.0-1
[   13.643644] input: Logitech USB Receiver as /class/input/input3
[   13.643739] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:10.0-1
[   13.756710] input: Logitech USB RECEIVER as /class/input/input4
[   13.756799] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:10.1-2
[   13.756812] usbcore: registered new interface driver usbhid
[   13.756815] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   13.756896] usbcore: registered new interface driver lmpcm_usb
[   13.756899] ubuntu/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   14.276043] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   14.783625] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   14.783634] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   14.783702] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 19
[   14.783840] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   15.435533] fuse init (API version 7.8)
[   15.455896] lp0: using parport0 (interrupt-driven).
[   16.985346] NET: Registered protocol family 10
[   16.985436] lo: Disabled Privacy Extensions
[   20.710865] input: Power Button (FF) as /class/input/input5
[   20.710893] ACPI: Power Button (FF) [PWRF]
[   20.710953] input: Sleep Button (CM) as /class/input/input6
[   20.710971] ACPI: Sleep Button (CM) [SLPB]
[   20.711000] input: Power Button (CM) as /class/input/input7
[   20.711016] ACPI: Power Button (CM) [PWRB]
[   20.764738] Using specific hotkey driver
[   20.815653] No dock devices found.
[   20.844729] ibm_acpi: ec object not found
[   20.974511] pcc_acpi: loading...
[   26.138050] ppdev: user-space parallel port driver
[   26.658207] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   26.658212] apm: disabled - APM is not SMP safe.
[   26.801980] Bluetooth: Core ver 2.11
[   26.802036] NET: Registered protocol family 31
[   26.802039] Bluetooth: HCI device and connection manager initialized
[   26.802042] Bluetooth: HCI socket layer initialized
[   26.821228] Bluetooth: L2CAP ver 2.8
[   26.821234] Bluetooth: L2CAP socket layer initialized
[   26.896789] Bluetooth: RFCOMM socket layer initialized
[   26.896801] Bluetooth: RFCOMM TTY layer initialized
[   26.896803] Bluetooth: RFCOMM ver 1.8
[   38.444888] eth0: no IPv6 routers present

First boot, no special flags.

---

### Post by noob12 on 2007-09-09
And now a second boot when the network stops working...

---

### Post by jesse_adkins on 2007-09-09
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e6000 size: 000000000001a000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001dec0000 end: 000000001dfc0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001dfc0000 size: 000000000000e000 end: 000000001dfce000 type: 3
[    0.000000] copy_e820_map() start: 000000001dfce000 size: 0000000000022000 end: 000000001dff0000 type: 4
[    0.000000] copy_e820_map() start: 000000001dff0000 size: 0000000000010000 end: 000000001e000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dfc0000 (usable)
[    0.000000]  BIOS-e820: 000000001dfc0000 - 000000001dfce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001dfce000 - 000000001dff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 122816) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   122816
[    0.000000]   HighMem    122816 ->   122816
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   122816
[    0.000000] On node 0 totalpages: 122816
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 927 pages used for memmap
[    0.000000]   Normal zone: 117793 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f8760
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x07000619 MSFT 0x00000097) @ 0x1dfc0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x07000619 MSFT 0x00000097) @ 0x1dfc0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x07000619 MSFT 0x00000097) @ 0x1dfc0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x07000619 MSFT 0x00000097) @ 0x1dfce040
[    0.000000] ACPI: DSDT (v001  12345 12345123 0x00000123 INTL 0x20051117) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
[    0.000000] Detected 1863.071 MHz processor.
[   20.876368] Built 1 zonelists.  Total pages: 121857
[   20.876373] Kernel command line: root=UUID=80952c30-90a0-4bf5-8ffb-8991924ef26c ro quiet splash
[   20.876517] mapped APIC to ffffd000 (fee00000)
[   20.876519] mapped IOAPIC to ffffc000 (fec00000)
[   20.876522] Enabling fast FPU save and restore... done.
[   20.876525] Enabling unmasked SIMD FPU exception support... done.
[   20.876533] Initializing CPU#0
[   20.876635] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   20.877898] Console: colour VGA+ 80x25
[   20.878071] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.878218] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.891154] Memory: 475960k/491264k available (1993k kernel code, 14720k reserved, 900k data, 328k init, 0k highmem)
[   20.891162] virtual kernel memory layout:
[   20.891163]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   20.891164]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.891165]     vmalloc : 0xde800000 - 0xff7fe000   ( 527 MB)
[   20.891166]     lowmem  : 0xc0000000 - 0xddfc0000   ( 479 MB)
[   20.891167]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   20.891168]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   20.891169]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   20.891172] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.968543] Calibrating delay using timer specific routine.. 3730.73 BogoMIPS (lpj=7461475)
[   20.968576] Security Framework v1.0.0 initialized
[   20.968581] SELinux:  Disabled at boot.
[   20.968594] Mount-cache hash table entries: 512
[   20.968702] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   20.968709] monitor/mwait feature present.
[   20.968710] using mwait in idle threads.
[   20.968714] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.968716] CPU: L2 cache: 2048K
[   20.968719] CPU: Physical Processor ID: 0
[   20.968720] CPU: Processor Core ID: 0
[   20.968722] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   20.968729] Compat vDSO mapped to ffffe000.
[   20.968732] Remapping vsyscall page to ffffe000
[   20.968742] Checking 'hlt' instruction... OK.
[   20.984598] SMP alternatives: switching to UP code
[   20.984861] Early unpacking initramfs... done
[   21.266606] ACPI: Core revision 20060707
[   21.266816] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   21.268792] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[   21.268810] SMP alternatives: switching to SMP code
[   21.268888] Booting processor 1/1 eip 3000
[   21.279355] Initializing CPU#1
[   21.360104] Calibrating delay using timer specific routine.. 3726.33 BogoMIPS (lpj=7452663)
[   21.360110] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   21.360115] monitor/mwait feature present.
[   21.360118] CPU: L1 I cache: 32K, L1 D cache: 32K
[   21.360119] CPU: L2 cache: 2048K
[   21.360121] CPU: Physical Processor ID: 0
[   21.360123] CPU: Processor Core ID: 1
[   21.360124] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   21.360540] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[   21.360562] Total of 2 processors activated (7457.06 BogoMIPS).
[   21.361302] ENABLING IO-APIC IRQs
[   21.361627] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.507955] checking TSC synchronization across 2 CPUs: passed.
[    0.004000] Brought up 2 CPUs
[    0.473416] migration_cost=239
[    0.473651] Booting paravirtualized kernel on bare hardware
[    0.473751] Time: 10:43:49  Date: 08/09/107
[    0.473774] NET: Registered protocol family 16
[    0.473848] EISA bus registered
[    0.473852] ACPI: bus type pci registered
[    0.473987] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=1
[    0.473989] PCI: Using configuration type 1
[    0.473990] Setting up standard PCI resources
[    0.481859] ACPI: Interpreter enabled
[    0.481861] ACPI: Using IOAPIC for interrupt routing
[    0.482408] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.482412] PCI: Probing PCI hardware (bus 00)
[    0.483497] Boot video device is 0000:01:00.0
[    0.483547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.496004] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.505202] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.505416] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.505634] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.505847] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.506113] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.506325] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.506539] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.506753] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.506862] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.506870] pnp: PnP ACPI init
[    0.512561] pnp: PnP ACPI: found 13 devices
[    0.512566] PnPBIOS: Disabled by ACPI PNP
[    0.512609] PCI: Using ACPI for IRQ routing
[    0.512611] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.517779] NET: Registered protocol family 8
[    0.517781] NET: Registered protocol family 20
[    0.518511] pnp: 00:09: ioport range 0xa00-0xa0f has been reserved
[    0.518514] pnp: 00:09: ioport range 0x290-0x29f has been reserved
[    0.518516] pnp: 00:09: ioport range 0xa20-0xa2f has been reserved
[    0.518518] pnp: 00:09: ioport range 0xa30-0xa3f has been reserved
[    0.518767] PCI: Bridge: 0000:00:01.0
[    0.518769]   IO window: disabled.
[    0.518774]   MEM window: fca00000-feafffff
[    0.518778]   PREFETCH window: eff00000-f7efffff
[    0.518795] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.518819] NET: Registered protocol family 2
[    0.559370] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.559437] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.559520] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.559547] TCP: Hash tables configured (established 16384 bind 8192)
[    0.559550] TCP reno registered
[    0.571409] checking if image is initramfs... it is
[    1.130270] Freeing initrd memory: 6751k freed
[    1.130964] audit: initializing netlink socket (disabled)
[    1.130992] audit(1189334629.844:1): initialized
[    1.131166] VFS: Disk quotas dquot_6.5.1
[    1.131192] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.131256] io scheduler noop registered
[    1.131258] io scheduler anticipatory registered
[    1.131260] io scheduler deadline registered
[    1.131270] io scheduler cfq registered (default)
[    1.131350] PCI: Bypassing VIA 8237 APIC De-Assert Message
[    1.131578] isapnp: Scanning for PnP cards...
[    1.485071] isapnp: No Plug & Play device found
[    1.504267] Real Time Clock Driver v1.12ac
[    1.504328] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.504443] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.504559] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.505067] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.505246] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.505410] mice: PS/2 mouse device common for all mice
[    1.505965] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.506110] input: Macintosh mouse button emulation as /class/input/input0
[    1.506143] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.506147] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.506453] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.506455] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    1.507388] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.507391] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.507501] EISA: Probing bus 0 at eisa.0
[    1.507543] EISA: Detected 0 cards.
[    1.537690] TCP cubic registered
[    1.537699] NET: Registered protocol family 1
[    1.537720] Starting balanced_irq
[    1.537726] Using IPI No-Shortcut mode
[    1.537842] ACPI: (supports S0 S1 S3 S4 S5)
[    1.537881]   Magic number: 7:437:729
[    1.538283] Time: tsc clocksource has been installed.
[    1.538300] Freeing unused kernel memory: 328k freed
[    2.706666] Capability LSM initialized
[    2.736953] ACPI: Processor [CPU1] (supports 16 throttling states)
[    2.737019] ACPI: Processor [CPU2] (supports 16 throttling states)
[    2.737026] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.737031] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.737823] ACPI: Thermal Zone [THRM] (30 C)
[    3.030353] usbcore: registered new interface driver usbfs
[    3.030378] usbcore: registered new interface driver hub
[    3.030405] usbcore: registered new device driver usb
[    3.031163] USB Universal Host Controller Interface driver v3.0
[    3.031234] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 16
[    3.031247] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    3.031424] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    3.031454] uhci_hcd 0000:00:10.0: irq 16, io base 0x0000dc00
[    3.031547] usb usb1: configuration #1 chosen from 1 choice
[    3.031569] hub 1-0:1.0: USB hub found
[    3.031574] hub 1-0:1.0: 2 ports detected
[    3.136406] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 16
[    3.136422] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    3.136447] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    3.136470] uhci_hcd 0000:00:10.1: irq 16, io base 0x0000d880
[    3.136572] usb usb2: configuration #1 chosen from 1 choice
[    3.136597] hub 2-0:1.0: USB hub found
[    3.136602] hub 2-0:1.0: 2 ports detected
[    3.244184] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 16
[    3.244193] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    3.244211] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    3.244230] uhci_hcd 0000:00:10.2: irq 16, io base 0x0000d800
[    3.244305] usb usb3: configuration #1 chosen from 1 choice
[    3.244327] hub 3-0:1.0: USB hub found
[    3.244331] hub 3-0:1.0: 2 ports detected
[    3.348058] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 16
[    3.348066] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    3.348084] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    3.348103] uhci_hcd 0000:00:10.3: irq 16, io base 0x0000d480
[    3.348177] usb usb4: configuration #1 chosen from 1 choice
[    3.348200] hub 4-0:1.0: USB hub found
[    3.348205] hub 4-0:1.0: 2 ports detected
[    3.375957] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    3.456925] SCSI subsystem initialized
[    3.461229] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 16
[    3.461248] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    3.461290] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    3.461326] ehci_hcd 0000:00:10.4: irq 16, io mem 0xfebfec00
[    3.461332] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.461435] usb usb5: configuration #1 chosen from 1 choice
[    3.461469] hub 5-0:1.0: USB hub found
[    3.461475] hub 5-0:1.0: 8 ports detected
[    3.461688] libata version 2.20 loaded.
[    3.569783] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[    3.569811] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 17
[    3.569823] VP_IDE: chipset revision 6
[    3.569825] VP_IDE: not 100% native mode: will probe irqs later
[    3.569835] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[    3.569843]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[    3.569853]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[    3.569858] Probing IDE interface ide0...
[    3.911313] usb 1-1: device not accepting address 2, error -71
[    4.139044] Probing IDE interface ide1...
[    4.711056] sata_via 0000:00:0f.0: version 2.1
[    4.711081] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 17
[    4.711098] sata_via 0000:00:0f.0: routed to hard irq line 11
[    4.711148] ata1: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e882 bmdma 0x0001e400 irq 17
[    4.711169] ata2: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e482 bmdma 0x0001e408 irq 17
[    4.711186] scsi0 : sata_via
[    4.918111] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    4.928716] ATA: abnormal status 0x7F on port 0x0001ec07
[    4.928733] scsi1 : sata_via
[    5.133852] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.300290] ATA: abnormal status 0x7F on port 0x0001e807
[    5.310905] ATA: abnormal status 0x7F on port 0x0001e807
[    5.363717] ata2.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
[    5.363722] ata2.00: ATA-7: ST3300620AS, 3.AAE, max UDMA/133
[    5.363725] ata2.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.430258] ata2.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
[    5.430262] ata2.00: configured for UDMA/133
[    5.431024] scsi 1:0:0:0: Direct-Access     ATA      ST3300620AS      3.AA PQ: 0 ANSI: 5
[    5.435747] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[    5.435758] sda: Write Protect is off
[    5.435760] sda: Mode Sense: 00 3a 00 00
[    5.435773] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.435816] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[    5.435824] sda: Write Protect is off
[    5.435825] sda: Mode Sense: 00 3a 00 00
[    5.435838] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.435840]  sda: sda1 sda2 sda3
[    5.469943] sd 1:0:0:0: Attached scsi disk sda
[    5.472972] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    5.489437] usb 1-1: new low speed USB device using uhci_hcd and address 4
[    5.670475] usb 1-1: configuration #1 chosen from 1 choice
[    5.912920] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    6.091129] usb 2-2: configuration #1 chosen from 1 choice
[    6.094130] usbcore: registered new interface driver hiddev
[    6.107975] input: Logitech USB Receiver as /class/input/input1
[    6.107986] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:10.0-1
[    6.137952] input: Logitech USB Receiver as /class/input/input2
[    6.137977] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:10.0-1
[    6.156040] input: Logitech USB RECEIVER as /class/input/input3
[    6.156058] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:10.1-2
[    6.156065] usbcore: registered new interface driver usbhid
[    6.156068] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   13.602839] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.604190] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.721126] Linux agpgart interface v0.102 (c) Dave Jones
[   13.722360] agpgart: Detected VIA VT3314 chipset
[   13.726021] agpgart: AGP aperture is 64M @ 0xf8000000
[   13.808861] parport: PnPBIOS parport detected.
[   13.808930] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   13.841834] input: PC Speaker as /class/input/input4
[   13.949499] usbcore: registered new interface driver lmpcm_usb
[   13.949504] ubuntu/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   14.121110] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 18
[   14.874200] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   15.377799] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   15.377805] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   15.377910] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 18
[   15.378043] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   16.001304] fuse init (API version 7.8)
[   16.022042] lp0: using parport0 (interrupt-driven).
[   17.445980] NET: Registered protocol family 17
[   22.509596] input: Power Button (FF) as /class/input/input5
[   22.509717] ACPI: Power Button (FF) [PWRF]
[   22.537321] input: Sleep Button (CM) as /class/input/input6
[   22.539797] ACPI: Sleep Button (CM) [SLPB]
[   22.542139] input: Power Button (CM) as /class/input/input7
[   22.542270] ACPI: Power Button (CM) [PWRB]
[   22.555639] Using specific hotkey driver
[   22.594831] No dock devices found.
[   22.624180] ibm_acpi: ec object not found
[   22.733736] pcc_acpi: loading...
[   27.757843] ppdev: user-space parallel port driver
[   28.222445] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   28.222450] apm: disabled - APM is not SMP safe.
[   28.374788] Bluetooth: Core ver 2.11
[   28.374849] NET: Registered protocol family 31
[   28.374850] Bluetooth: HCI device and connection manager initialized
[   28.374853] Bluetooth: HCI socket layer initialized
[   28.384632] Bluetooth: L2CAP ver 2.8
[   28.384636] Bluetooth: L2CAP socket layer initialized
[   28.461321] Bluetooth: RFCOMM socket layer initialized
[   28.461336] Bluetooth: RFCOMM TTY layer initialized
[   28.461338] Bluetooth: RFCOMM ver 1.8
[   42.070519] NET: Registered protocol family 10
[   42.070613] lo: Disabled Privacy Extensions

And now, the second boot with the BIOS settings gone.

---

### Post by noob12 on 2007-09-10
I'm really sorry, but I don't see anything.  :( 

I tried to engage another user (volksolwagen57) whose signature indicates he is using the same mobo, but no response; you might try to PM him yourself.   He didn't mention any similar problem, so I'm guessing his might be working ok.  Maybe he's running a different BIOS version, or has somewhat different settings.  You could also try to post a new thread specifically asking for P4M800PRO-M users that might know what to do about this or at least be willing to share what their settings are.

---

