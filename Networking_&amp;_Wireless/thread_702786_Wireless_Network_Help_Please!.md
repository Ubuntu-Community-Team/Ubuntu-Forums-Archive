---
title: "Wireless Network Help Please!"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by commucom on 2008-02-20
Hey Guys,

I am new to Ubuntu, i have recently duel booted it with Vista. I am trying to use Ubuntu as my work OS, as my new work place uses it and recommends it.

I have a Wireless Network, which currently has no encription on it, i use a Wireless USB card from belkin, the router is also of belkin make. My wireless card's model is f5d7050.

The problem is, when i start UBUNTU on some occations with manager shows there to be surrounding networks, which is the case, but it never shows mine, on other occations no networks are displayed. I have tried using connect to other network and typing the ssid in, i have also tried manual config, neither of these have worked.

Can anyone suggest why this is and how to fix it?

BTW: if you need any more infomation then just say and will try and get you it, however i am new and not fully competent using the consol yet.

Many Thanks
:KS

Adam

---

### Post by spd106 on 2008-02-22
Hello, it's always nice to hear that there are Linux friendly companies out there encouraging it's employees to try something different from Windows.

Now about the wireless router, have you tried using any other Linux/Ubuntu machine or a different network card to connect to it?

Also it might be worth checking that the router is set to broadcast it's SSID. This is a common problem with some wifi cards and their drivers. While some people have reported it working, I never seem to be able to connect to hidden networks.

If you have access to a terminal and sudo, then you can try scanning manually with this command.
```
sudo iwlist eth1 scan
```
where eth1 is your wireless interface.

If it says scanning not support then it might have a different name e.g. ra0

---

### Post by jblackthorne on 2008-02-22
Hello and welcome to the wonderful world of Ubuntu.  Gutsy Gibbon is an amazing release that will surely win you over.  Well, once you get it up and running that is.  

I am not familiar with the the Belkin f5d7050 adapter personally.  Though, a little bit of searching shows that particular model ships with two different chipsets and consequently has different drivers depending on the hardware revision:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29)

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29)

The good news is that it appears both drivers are already included in Gutsy.  Thus, you hopefully don't need to install anything just yet.  To be sure which chipset you have, please type:

sudo lspci -vv

in a console window and included the output in this post.  That lspci command shows hardware details of devices installed on the USB bus.  

Next up, networking scanning is kind of hit or miss for a variety of reasons.  Some driver developers simply don't implement all the features.  Other times, environmental noise can interfere.  You mention that you are dual booting. If you can connect to the wireless in Windows, then you can connect to it in Gutsy.  

The previous poster suggested a command line scan.  The only problem is that his syntax assumes the wireless device is named, “eth1”.  That is not necessarily a constant.  To find out the interface name, type:

sudo ifconfig

ifconfig is the network configuration tool in Linux.   The output of that will most likely show, “eth0” (your ethernet port), “lo” (your loopback), and something else,  My other interface for example is “wlan0”.

Try a command line scan with:

sudo iwlist <your ethernet device name> scan.

also, try 

netstat -rn

to see the complete routing table.  With all that said, the best way to test yoru wireless is to do the following:

1.reboot fresh into Gutsy
2.Click the Network Applet in the upper corner of the panel (also called nm-applet in posts)
3.Choose “Connect to Other Wireless Network”
4.Manually put in the network ESSID and connection details.
5.When the lights stop moving it will eithe work or not.  If it does not work, then please type:
1.sudo dmesg in a console and post the results.  That is a debugging interface, called the “Kernel Ring Buffer” that shows detailed info about the wireless driver interfacing with the kernel.

Good luck!

---

### Post by commucom on 2008-02-24
> [    0.000000] ACPI: DSDT 6FFB0610, 4D49 (r1     RC    RC415        0 INTL 20051117)
[    0.000000] ACPI: FACS 6FFBE000, 0040
[    0.000000] ACPI: APIC 6FFB0390, 006C (r1 PacBel OEMAPIC  11000716 MSFT       97)
[    0.000000] ACPI: MCFG 6FFB0400, 003C (r1 PacBel OEMMCFG  11000716 MSFT       97)
[    0.000000] ACPI: SLIC 6FFB0440, 0176 (r1 PacBel PBDTNB00 11000716 MSFT       97)
[    0.000000] ACPI: WDRT 6FFB05C0, 0047 (r1 PacBel OEMWDRT  11000716 MSFT       97)
[    0.000000] ACPI: OEMB 6FFBE040, 0060 (r1 PacBel AMI_OEM  11000716 MSFT       97)
[    0.000000] ACPI: EPTH 6FFB5360, 0038 (r1 PacBel OEMHPET  11000716 MSFT       97)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 70000000:8ee00000)
[    0.000000] Built 1 zonelists.  Total pages: 455089
[    0.000000] Kernel command line: root=UUID=a664f646-5e2e-458a-82fc-73b82a78c050 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2992.713 MHz processor.
[   23.652939] Console: colour VGA+ 80x25
[   23.653850] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.654571] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.736294] Memory: 1806992k/1834688k available (2015k kernel code, 26420k reserved, 916k data, 364k init, 917184k highmem)
[   23.736307] virtual kernel memory layout:
[   23.736308]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   23.736309]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.736310]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.736311]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.736312]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   23.736313]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   23.736314]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   23.736318] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.736379] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   23.816373] Calibrating delay using timer specific routine.. 5991.58 BogoMIPS (lpj=11983168)
[   23.816421] Security Framework v1.0.0 initialized
[   23.816430] SELinux:  Disabled at boot.
[   23.816446] Mount-cache hash table entries: 512
[   23.816644] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e49d 00000000 00000001
[   23.816654] monitor/mwait feature present.
[   23.816656] using mwait in idle threads.
[   23.816664] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.816667] CPU: L2 cache: 2048K
[   23.816670] CPU: Physical Processor ID: 0
[   23.816672] CPU: Processor Core ID: 0
[   23.816675] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e49d 00000000 00000001
[   23.816690] Compat vDSO mapped to ffffe000.
[   23.816710] Checking 'hlt' instruction... OK.
[   23.832557] SMP alternatives: switching to UP code
[   23.833331] Early unpacking initramfs... done
[   24.130308] ACPI: Core revision 20070126
[   24.130369] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.133511] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[   24.133532] SMP alternatives: switching to SMP code
[   24.133674] Booting processor 1/1 eip 3000
[   24.144038] Initializing CPU#1
[   24.224169] Calibrating delay using timer specific routine.. 5985.58 BogoMIPS (lpj=11971178)
[   24.224180] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e49d 00000000 00000001
[   24.224185] monitor/mwait feature present.
[   24.224192] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   24.224194] CPU: L2 cache: 2048K
[   24.224196] CPU: Physical Processor ID: 0
[   24.224198] CPU: Processor Core ID: 1
[   24.224200] CPU: After all inits, caps: bfebfbff 20000000 00000000 0000b180 0000e49d 00000000 00000001
[   24.224724] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[   24.224759] Total of 2 processors activated (11977.17 BogoMIPS).
[   24.224926] ENABLING IO-APIC IRQs
[   24.225116] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.372188] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   24.392215] Brought up 2 CPUs
[   24.688877] migration_cost=3883
[   24.689054] Booting paravirtualized kernel on bare hardware
[   24.689138] Time: 15:44:09  Date: 01/23/108
[   24.689161] NET: Registered protocol family 16
[   24.689264] EISA bus registered
[   24.689270] ACPI: bus type pci registered
[   24.689387] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[   24.689389] PCI: Using configuration type 1
[   24.689391] Setting up standard PCI resources
[   24.704695] ACPI: EC: Look up EC in DSDT
[   24.727584] ACPI: Interpreter enabled
[   24.727588] ACPI: (supports S0 S1 S3 S4 S5)
[   24.727614] ACPI: Using IOAPIC for interrupt routing
[   24.737607] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.737622] PCI: Probing PCI hardware (bus 00)
[   24.738942] PCI: Transparent bridge - 0000:00:14.4
[   24.738981] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.739114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   24.739236] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[   24.752031] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[   24.752160] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
[   24.752287] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 10 11 12 14 15)
[   24.752416] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[   24.752541] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 *7 10 11 12 14 15)
[   24.752700] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[   24.752823] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
[   24.752952] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   24.753067] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.753083] pnp: PnP ACPI init
[   24.753092] ACPI: bus type pnp registered
[   24.757429] pnp: PnP ACPI: found 11 devices
[   24.757432] ACPI: ACPI bus type pnp unregistered
[   24.757437] PnPBIOS: Disabled by ACPI PNP
[   24.757488] PCI: Using ACPI for IRQ routing
[   24.757492] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.757499] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   24.765053] NET: Registered protocol family 8
[   24.765056] NET: Registered protocol family 20
[   24.765235] pnp: 00:05: iomem range 0xffb80000-0xffbfffff could not be reserved
[   24.765239] pnp: 00:05: iomem range 0xfff80000-0xffffffff could not be reserved
[   24.765246] pnp: 00:07: ioport range 0xa00-0xa0f has been reserved
[   24.765249] pnp: 00:07: ioport range 0xa10-0xa1f has been reserved
[   24.765252] pnp: 00:07: ioport range 0xa20-0xa2f has been reserved
[   24.765254] pnp: 00:07: ioport range 0xa30-0xa3f has been reserved
[   24.765260] pnp: 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[   24.765263] pnp: 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[   24.765269] pnp: 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[   24.765274] pnp: 00:0a: iomem range 0x0-0x9ffff could not be reserved
[   24.765277] pnp: 00:0a: iomem range 0xc0000-0xcffff could not be reserved
[   24.765280] pnp: 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[   24.765283] pnp: 00:0a: iomem range 0x100000-0x6fffffff could not be reserved
[   24.768555] Time: tsc clocksource has been installed.
[   24.795637] PCI: Bridge: 0000:00:01.0
[   24.795640]   IO window: a000-afff
[   24.795645]   MEM window: ff400000-ff4fffff
[   24.795649]   PREFETCH window: bff00000-dfefffff
[   24.795653] PCI: Bridge: 0000:00:14.4
[   24.795657]   IO window: b000-bfff
[   24.795664]   MEM window: ff500000-ff5fffff
[   24.795669]   PREFETCH window: disabled.
[   24.795701] NET: Registered protocol family 2
[   24.832589] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.832714] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   24.833651] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.834031] TCP: Hash tables configured (established 131072 bind 65536)
[   24.834035] TCP reno registered
[   24.844773] checking if image is initramfs... it is
[   25.296125] Switched to high resolution mode on CPU 1
[   25.296335] Switched to high resolution mode on CPU 0
[   25.434365] Freeing initrd memory: 7350k freed
[   25.435175] audit: initializing netlink socket (disabled)
[   25.435193] audit(1203781449.412:1): initialized
[   25.435380] highmem bounce pool size: 64 pages
[   25.438625] VFS: Disk quotas dquot_6.5.1
[   25.438701] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.438819] io scheduler noop registered
[   25.438823] io scheduler anticipatory registered
[   25.438825] io scheduler deadline registered
[   25.438846] io scheduler cfq registered (default)
[   25.438860] PCI: MSI quirk detected. MSI deactivated.
[   25.612119] Boot video device is 0000:01:05.0
[   25.612353] isapnp: Scanning for PnP cards...
[   25.963855] isapnp: No Plug & Play device found
[   26.002462] Real Time Clock Driver v1.12ac
[   26.002622] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.004311] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.004498] input: Macintosh mouse button emulation as /class/input/input0
[   26.004614] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   26.004618] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   26.005007] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.005016] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.005245] mice: PS/2 mouse device common for all mice
[   26.005397] EISA: Probing bus 0 at eisa.0
[   26.005445] EISA: Detected 0 cards.
[   26.005561] TCP cubic registered
[   26.005575] NET: Registered protocol family 1
[   26.005603] Using IPI No-Shortcut mode
[   26.005802]   Magic number: 12:976:740
[   26.006623] Freeing unused kernel memory: 364k freed
[   26.026054] input: AT Translated Set 2 keyboard as /class/input/input1
[   27.226632] AppArmor: AppArmor initialized<5>audit(1203781450.912:2):  type=1505 info="AppArmor initialized" pid=1205
[   27.235504] fuse init (API version 7.8)
[   27.240690] Failure registering capabilities with primary security module.
[   27.272531] ACPI: duty_cycle spans bit 4
[   27.272767] ACPI: SSDT 6FFBE0A0, 01D2 (r1    AMI   CPU1PM        1 INTL 20051117)
[   27.273062] ACPI: duty_cycle spans bit 4
[   27.273241] ACPI: SSDT 6FFBE280, 0143 (r1    AMI   CPU2PM        1 INTL 20051117)
[   27.273458] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.273472] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.274518] ACPI: Thermal Zone [THRM] (-270 C)
[   27.742770] usbcore: registered new interface driver usbfs
[   27.742801] usbcore: registered new interface driver hub
[   27.742829] usbcore: registered new device driver usb
[   27.743606] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.743646] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.743662] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   27.743812] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   27.743830] ohci_hcd 0000:00:13.0: irq 16, io mem 0xff6fe000
[   27.753760] SCSI subsystem initialized
[   27.759177] libata version 2.21 loaded.
[   27.823573] usb usb1: configuration #1 chosen from 1 choice
[   27.823610] hub 1-0:1.0: USB hub found
[   27.823626] hub 1-0:1.0: 2 ports detected
[   27.856883] 8139too Fast Ethernet driver 0.9.28
[   27.927238] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   27.927259] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   27.927398] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   27.927421] ohci_hcd 0000:00:13.1: irq 17, io mem 0xff6fd000
[   27.987154] usb usb2: configuration #1 chosen from 1 choice
[   27.987300] hub 2-0:1.0: USB hub found
[   27.987314] hub 2-0:1.0: 2 ports detected
[   28.091129] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[   28.091142] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   28.091280] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   28.091297] ohci_hcd 0000:00:13.2: irq 18, io mem 0xff6fc000
[   28.151054] usb usb3: configuration #1 chosen from 1 choice
[   28.151205] hub 3-0:1.0: USB hub found
[   28.151218] hub 3-0:1.0: 2 ports detected
[   28.255038] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   28.255050] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   28.255198] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   28.255214] ohci_hcd 0000:00:13.3: irq 17, io mem 0xff6fb000
[   28.315003] usb usb4: configuration #1 chosen from 1 choice
[   28.315168] hub 4-0:1.0: USB hub found
[   28.315179] hub 4-0:1.0: 2 ports detected
[   28.406586] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   28.418975] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[   28.418987] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   28.419150] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   28.419164] ohci_hcd 0000:00:13.4: irq 18, io mem 0xff6fa000
[   28.482678] usb usb5: configuration #1 chosen from 1 choice
[   28.482714] hub 5-0:1.0: USB hub found
[   28.482727] hub 5-0:1.0: 2 ports detected
[   28.586951] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 19
[   28.587235] ahci 0000:00:12.0: version 2.2
[   28.587289] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 20
[   28.587315] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   28.587833] eth0: RealTek RTL8139 at 0xf88c0c00, 00:1b:b9:bf:8a:29, IRQ 19
[   28.587837] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   28.590426] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   28.798516] usb 2-1: configuration #1 chosen from 1 choice
[   29.110206] usb 2-2: new low speed USB device using ohci_hcd and address 3
[   29.334206] usb 2-2: configuration #1 chosen from 1 choice
[   29.589996] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   29.590003] ahci 0000:00:12.0: flags: ncq ilck led clo pmp pio slum part 
[   29.590527] scsi0 : ahci
[   29.590611] scsi1 : ahci
[   29.590676] scsi2 : ahci
[   29.590756] scsi3 : ahci
[   29.590871] ata1: SATA max UDMA/133 cmd 0xf88c2d00 ctl 0x00000000 bmdma 0x00000000 irq 20
[   29.590877] ata2: SATA max UDMA/133 cmd 0xf88c2d80 ctl 0x00000000 bmdma 0x00000000 irq 20
[   29.590882] ata3: SATA max UDMA/133 cmd 0xf88c2e00 ctl 0x00000000 bmdma 0x00000000 irq 20
[   29.590887] ata4: SATA max UDMA/133 cmd 0xf88c2e80 ctl 0x00000000 bmdma 0x00000000 irq 20
[   29.645922] usb 3-1: new full speed USB device using ohci_hcd and address 2
[   29.866913] usb 3-1: configuration #1 chosen from 1 choice
[   29.868985] usbcore: registered new interface driver hiddev
[   30.073689] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   30.111707] ata1.00: ATA-7: ST3160215AS, 3.AAC, max UDMA/133
[   30.111712] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   30.169979] ata1.00: configured for UDMA/133
[   30.177630] usb 4-1: new full speed USB device using ohci_hcd and address 2
[   30.398625] usb 4-1: configuration #1 chosen from 1 choice
[   30.413759] input: HID 04d9:1133 as /class/input/input2
[   30.413787] input: USB HID v1.10 Mouse [HID 04d9:1133] on usb-0000:00:13.1-2
[   30.413811] usbcore: registered new interface driver usbhid
[   30.413818] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.413893] usbcore: registered new interface driver libusual
[   30.420748] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.420753] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.422664] Initializing USB Mass Storage driver...
[   30.422738] scsi4 : SCSI emulation for USB Mass Storage devices
[   30.422795] usb-storage: device found at 2
[   30.422797] usb-storage: waiting for device to settle before scanning
[   30.422841] scsi5 : SCSI emulation for USB Mass Storage devices
[   30.422880] usb-storage: device found at 2
[   30.422883] usb-storage: waiting for device to settle before scanning
[   30.422894] usbcore: registered new interface driver usb-storage
[   30.422897] USB Mass Storage support registered.
[   30.477481] ata2: SATA link down (SStatus 0 SControl 300)
[   30.789312] ata3: SATA link down (SStatus 0 SControl 300)
[   31.109133] ata4: SATA link down (SStatus 0 SControl 300)
[   31.109298] scsi 0:0:0:0: Direct-Access     ATA      ST3160215AS      3.AA PQ: 0 ANSI: 5
[   31.110427] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 21
[   31.110446] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   31.111588] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   31.111633] ehci_hcd 0000:00:13.5: debug port 1
[   31.111654] ehci_hcd 0000:00:13.5: irq 21, io mem 0xff6ff800
[   31.111667] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.111762] usb 3-1: USB disconnect, address 2
[   31.111806] usb usb6: configuration #1 chosen from 1 choice
[   31.111849] hub 6-0:1.0: USB hub found
[   31.111860] hub 6-0:1.0: 10 ports detected
[   31.121869] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   31.121888] sd 0:0:0:0: [sda] Write Protect is off
[   31.121891] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.121912] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.121978] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   31.121991] sd 0:0:0:0: [sda] Write Protect is off
[   31.121994] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.122013] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.122019]  sda: sda1 sda2 sda3 < sda5 > sda4
[   31.162240] sd 0:0:0:0: [sda] Attached SCSI disk
[   31.167294] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.214842] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[   31.214864] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   31.214881] SB600_PATA: chipset revision 0
[   31.214884] SB600_PATA: not 100% native mode: will probe irqs later
[   31.214898]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:pio
[   31.214912] Probing IDE interface ide0...
[   31.237181] usb 2-1: USB disconnect, address 2
[   31.369013] usb 2-2: USB disconnect, address 3
[   31.496966] usb 4-1: USB disconnect, address 2
[   31.601224] kjournald starting.  Commit interval 5 seconds
[   31.601237] EXT3-fs: mounted filesystem with ordered data mode.
[   31.868732] usb 6-3: new high speed USB device using ehci_hcd and address 2
[   31.953095] hda: ATAPI DVD A DH18A1P, ATAPI CD/DVD-ROM drive
[   32.172473] usb 6-3: configuration #1 chosen from 1 choice
[   32.596343] usb 6-5: new high speed USB device using ehci_hcd and address 4
[   32.632334] hda: selected mode 0x44
[   32.632723] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   32.734727] usb 6-5: configuration #1 chosen from 1 choice
[   32.734974] scsi6 : SCSI emulation for USB Mass Storage devices
[   32.735118] usb-storage: device found at 4
[   32.735120] usb-storage: waiting for device to settle before scanning
[   33.283973] usb 2-2: new low speed USB device using ohci_hcd and address 4
[   33.503913] usb 2-2: configuration #1 chosen from 1 choice
[   33.516028] input: HID 04d9:1133 as /class/input/input3
[   33.516056] input: USB HID v1.10 Mouse [HID 04d9:1133] on usb-0000:00:13.1-2
[   33.827683] usb 4-1: new full speed USB device using ohci_hcd and address 3
[   34.052710] usb 4-1: configuration #1 chosen from 1 choice
[   34.054699] scsi7 : SCSI emulation for USB Mass Storage devices
[   34.054849] usb-storage: device found at 3
[   34.054851] usb-storage: waiting for device to settle before scanning
[   37.729807] usb-storage: device scan complete
[   37.731316] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[   37.735665] sd 6:0:0:0: [sdb] 2007040 512-byte hardware sectors (1028 MB)
[   37.736288] sd 6:0:0:0: [sdb] Write Protect is off
[   37.736291] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   37.736293] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   37.738409] sd 6:0:0:0: [sdb] 2007040 512-byte hardware sectors (1028 MB)
[   37.739035] sd 6:0:0:0: [sdb] Write Protect is off
[   37.739038] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   37.739039] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   37.739045]  sdb: sdb1
[   37.739909] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   37.739985] sd 6:0:0:0: Attached scsi generic sg1 type 0
[   38.555017] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.565515] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.576637] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   38.966136] input: PC Speaker as /class/input/input4
[   38.978190] Linux agpgart interface v0.102 (c) Dave Jones
[   39.049859] usb-storage: device scan complete
[   39.055864] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   39.061866] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   39.067856] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   39.074149] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   39.086895] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   39.086954] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   39.094193] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   39.094203] Uniform CD-ROM driver Revision: 3.20
[   39.096913] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[   39.096968] sd 7:0:0:1: Attached scsi generic sg3 type 0
[   39.107934] sd 7:0:0:2: [sde] Attached SCSI removable disk
[   39.108015] sd 7:0:0:2: Attached scsi generic sg4 type 0
[   39.116876] sd 7:0:0:3: [sdf] Attached SCSI removable disk
[   39.116949] sd 7:0:0:3: Attached scsi generic sg5 type 0
[   39.363090] p54: LM86 firmware
[   39.518311] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   39.716596] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   41.359765] prism54usb: firmware upload failed!
[   41.359809] prism54usb: probe of 6-3:1.0 failed with error -110
[   41.359837] usbcore: registered new interface driver prism54usb
[   41.615454] ieee80211_init: failed to initialize WME (err=-17)
[   41.640228] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   41.640272] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   41.640310] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   41.640372] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   41.640789] wmaster0: Selected rate control algorithm 'simple'
[   41.710969] usbcore: registered new interface driver rt2500usb
[   41.732189] usbcore: registered new interface driver rt73usb
[   42.319128] lp: driver loaded but no devices found
[   42.700394] EXT3 FS on sda4, internal journal
[   44.138648] No dock devices found.
[   44.220182] input: Power Button (FF) as /class/input/input5
[   44.220209] ACPI: Power Button (FF) [PWRF]
[   44.220311] input: Power Button (CM) as /class/input/input6
[   44.220331] ACPI: Power Button (CM) [PWRB]
[   45.459748] ppdev: user-space parallel port driver
[   45.626457] audit(1203781470.067:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5107 profile="/usr/sbin/cupsd"
[   45.665186] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   45.665192] apm: disabled - APM is not SMP safe.
[   45.751003] eth0: link down
[   46.039522] Failure registering capabilities with primary security module.
[   46.347474] Bluetooth: Core ver 2.11
[   46.347566] NET: Registered protocol family 31
[   46.347569] Bluetooth: HCI device and connection manager initialized
[   46.347575] Bluetooth: HCI socket layer initialized
[   46.363566] Bluetooth: L2CAP ver 2.8
[   46.363576] Bluetooth: L2CAP socket layer initialized
[   46.475825] Bluetooth: RFCOMM socket layer initialized
[   46.475856] Bluetooth: RFCOMM TTY layer initialized
[   46.475873] Bluetooth: RFCOMM ver 1.8
[   54.729115] hda-intel: Invalid position buffer, using LPIB read method instead.
[  141.865559] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x04d0 with error -110.
[  165.236303] NET: Registered protocol family 10
[  165.236415] lo: Disabled Privacy Extensions
[  165.236482] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  165.236529] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  231.817097] NET: Registered protocol family 17
[  232.642183] wlan0: Initial auth_alg=0
[  232.642191] wlan0: authenticate with AP 00:30:f1:fd:ee:09
[  232.649437] wlan0: RX authentication from 00:30:f1:fd:ee:09 (alg=0 transaction=2 status=0)
[  232.649441] wlan0: authenticated
[  232.649445] wlan0: associate with AP 00:30:f1:fd:ee:09
[  232.848559] wlan0: associate with AP 00:30:f1:fd:ee:09
[  233.048453] wlan0: associate with AP 00:30:f1:fd:ee:09
[  233.248345] wlan0: association with AP 00:30:f1:fd:ee:09 timed out
[  314.086995] ADDRCONF(NETDEV_UP): wlan0: link is not ready
adampotts@adampotts-desktop:~$ 



> adampotts@adampotts-desktop:~$ sudo lspci -vv
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
        Subsystem: Unknown device 1631:e02d
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 64
        Region 3: Memory at <ignored> (64-bit, non-prefetchable)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: ff400000-ff4fffff
        Prefetchable memory behind bridge: bff00000-dfefffff
        Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: [b0] Subsystem: Unknown device 1631:e02d

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: I/O ports at e800 [size=8]
        Region 1: I/O ports at e400 [size=4]
        Region 2: I/O ports at e000 [size=8]
        Region 3: I/O ports at dc00 [size=4]
        Region 4: I/O ports at d800 [size=16]
        Region 5: Memory at ff6ffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [70] #12 [0010]

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at ff6fe000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at ff6fd000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin C routed to IRQ 18
        Region 0: Memory at ff6fc000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at ff6fb000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin C routed to IRQ 18
        Region 0: Memory at ff6fa000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 128 bytes
        Interrupt: pin D routed to IRQ 21
        Region 0: Memory at ff6ff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
                Bridge: PM- B3+
        Capabilities: [e4] Debug port

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Region 0: I/O ports at 0b00 [size=16]
        Region 1: Memory at 80000000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at ff00 [size=16]
        Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Unknown device 1631:e02d
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin ? routed to IRQ 16
        Region 0: Memory at ff6f4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: ff500000-ff5fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200] (prog-if 00 [VGA])
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (2000ns min), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Region 1: I/O ports at a800 [size=256]
        Region 2: Memory at ff4f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at ff4c0000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Unknown device 1631:e02d
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at b800 [size=256]
        Region 1: Memory at ff5ffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

adampotts@adampotts-desktop:~$ 



These are the things you asked me to run... im non the wiser to what it means lol! hpefully u cn translate in ;)

Also my home network is called 'Wayside' if that helps you, it has no encription and is broadcasting my ssid

Adam

---

### Post by jblackthorne on 2008-02-24
That information helps a lot. Though, one of the commands I asked for was incorrect. I forgot that your wireless adapter is a USB adapter and not internal.  Thus, instead of :

sudo lspci --vv
please run and provide:
sudo lsusb -vv

The dmesg info is very helpful too.  The most important parts are:

[ 232.642183] wlan0: Initial auth_alg=0
[ 232.642191] wlan0: authenticate with AP 00:30:f1:fd:ee:09
[ 232.649437] wlan0: RX authentication from 00:30:f1:fd:ee:09 (alg=0 transaction=2 status=0)
[ 232.649441] wlan0: authenticated
[ 232.649445] wlan0: associate with AP 00:30:f1:fd:ee:09
[ 232.848559] wlan0: associate with AP 00:30:f1:fd:ee:09
[ 233.048453] wlan0: associate with AP 00:30:f1:fd:ee:09
[ 233.248345] wlan0: association with AP 00:30:f1:fd:ee:09 timed out
[ 314.086995] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Those lines tell us:

* Your ifconfig devicde is "wlan0"
* The wireless driver is installed and working correctly
* Your wireless driver found your wireless network (your ESSID). It even authenticated correctly and read the mac address.
* The problem is that the wireless was unable to join the network for some reason.

* This leads me to suggest that you check:
- Do you by chance have MAC address filtering enabled on your router?  If so, then you need to add the mac address from wlan0 (run ifconfig to get this)
- Are you sure encryption is really disabled? This really looks to me like you actually have some sort of security enabled, such as WEP.
- validate that there are not any "turbo" or extension  type settings enabled on the router that maybe the wireless driver does not support

In summary, it looks like Gutsy is working just fine.  Thus, I would suggest you recheck all your wireless settings.  Just for the heck of it, maybe make the ESSID "Wayside" something all in lower case?

Please try the above, run sudo lsusb -vv, and provide as many details back as possible.  I suspect that with a little bit of checking wireless settings, you will work it out.

Good luck!

---

