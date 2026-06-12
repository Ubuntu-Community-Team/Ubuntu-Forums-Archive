---
title: "Wireless : OK only after restart computer !"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by GwadaBreizh on 2007-01-17
Hello,

I've a laptop "ACER Aspire 5020" with Edgy.

The wireless card is a BCM4318. I use bcm43xx-fwcutter and [acer_acpi]("http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html").

When i start my computer :
```

~$ iwlist eth1 scan
No scan result
```

and after restart the laptop:
```
~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:07:CB:55:73:73
                    ESSID:"MONESSID"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-42 dBm  
                    Extra: Last beacon: 24ms ago
```

I have to restart my computer to use wireless, what is the problem ?:confused: 

Thanks

---

### Post by dmizer on 2007-01-17
try this command:
```
sudo /etc/init.d/networking restart
iwlist eth1 scan
```
or ...
```
sudo ifdown eth1&& sudo ifup eth1
iwlist eth1 scan
```

and post the contents of this file: /etc/network/interfaces

---

### Post by GwadaBreizh on 2007-01-17
Thank for your help.

the first command :

```
~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]
```
and
```
~$ iwlist eth1 scan
No scan result
```

And with this command :
```
sudo ifdown eth1&& sudo ifup eth1
```
but the LED :idea:  on the laptop light on and after few seconds light off
```
~$ iwlist eth1 scan
No scan result
```

i've installed wifi-radar. When i load wifi-radar the LED light on and i can see SSID. And the command :
```
~$ iwlist eth1 scan
eth 1    scan completed
           Cell 01 - Adress: 00:13:F7:33:AF:0D
           ESSID "NameOfEssid"
           etc .....
           .
           .
           .

```

I'dont understand why i can't have wireless connection after the first start, unless load wifi-radar ?

Thanks for help

---

### Post by dmizer on 2007-01-17
i think i may see the problem, but i'll need the contents of /etc/network/interfaces as requested previously.

while you're at it, post the contents of one of the following two commands.
1) if your card is a pcmcia or an internal pci card, post the output of:
lspci

2) if your card is a usb adapter, post the output of:
lsusb

---

### Post by GwadaBreizh on 2007-01-17
OK, sorry i didn't read well your last post.

My card is a internal card.

So, the content of /etc/network/interfaces is :
> auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.0.102
netmask 255.255.255.0
gateway 192.168.0.254
wireless-essid GWADANETAIR
wireless-key XXXXXXXXXX

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

And :
```
$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 5a39
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
**06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

I hope it can help you. Thanks

---

### Post by dmizer on 2007-01-17
sorry, two more things i need to ask for.  please post the output of:
dmesg

and
lsmod

---

### Post by GwadaBreizh on 2007-01-18
OK, output of dmesg :
```
:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[17179569.184000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fea0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fea0000 - 000000001feae000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001feae000 - 000000001ff00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 510MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6df0
[17179569.184000] On node 0 totalpages: 130720
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126624 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6db0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1fea81ce
[17179569.184000] ACPI: FADT (v001 ATI    Piranha  0x06040000 ATI  0x000f4240) @ 0x1feade41
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x1feadeb5
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x1feadf6a
[17179569.184000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x1feadfc4
[17179569.184000] ACPI: DSDT (v001    ATI    SB400 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash locale=fr_FR
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1600.254 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.784000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.784000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.796000] Memory: 508632k/522880k available (1910k kernel code, 13596k reserved, 1069k data, 308k init, 0k highmem)
[17179572.796000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.876000] Calibrating delay using timer specific routine.. 3205.46 BogoMIPS (lpj=6410937)
[17179572.876000] Security Framework v1.0.0 initialized
[17179572.876000] SELinux:  Disabled at boot.
[17179572.876000] Mount-cache hash table entries: 512
[17179572.876000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179572.876000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179572.876000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.876000] CPU: L2 Cache: 1024K (64 bytes/line)
[17179572.876000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179572.876000] Checking 'hlt' instruction... OK.
[17179572.892000] SMP alternatives: switching to UP code
[17179572.892000] Freeing SMP alternatives: 16k freed
[17179572.892000] checking if image is initramfs... it is
[17179573.448000] Freeing initrd memory: 5322k freed
[17179573.448000] ACPI: Core revision 20060707
[17179573.452000] ACPI: Looking for DSDT ... not found!
[17179573.456000] CPU0: AMD Turion(tm) 64 Mobile Technology ML-30 stepping 02
[17179573.456000] Total of 1 processors activated (3205.46 BogoMIPS).
[17179573.456000] ENABLING IO-APIC IRQs
[17179573.456000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.456000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17179573.456000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[17179573.456000] ...trying to set up timer as Virtual Wire IRQ... works.
[17179573.640000] Brought up 1 CPUs
[17179573.640000] migration_cost=0
[17179573.640000] NET: Registered protocol family 16
[17179573.640000] EISA bus registered
[17179573.640000] ACPI: bus type pci registered
[17179573.640000] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[17179573.640000] PCI: Not using MMCONFIG.
[17179573.644000] PCI: PCI BIOS revision 2.10 entry at 0xfd63c, last bus=6
[17179573.644000] PCI: Using configuration type 1
[17179573.644000] Setting up standard PCI resources
[17179573.648000] ACPI: Interpreter enabled
[17179573.648000] ACPI: Using IOAPIC for interrupt routing
[17179573.652000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.652000] PCI: Probing PCI hardware (bus 00)
[17179573.656000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179573.656000] Boot video device is 0000:01:00.0
[17179573.656000] PCI: Transparent bridge - 0000:00:14.4
[17179573.656000] PCI: Bus #07 (-#08) is hidden behind transparent bridge #06 (-#06) (try 'pci=assign-busses')
[17179573.656000] Please report the result to linux-kernel to fix this permanently
[17179573.656000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.660000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179573.660000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179573.660000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179573.660000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179573.660000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179573.660000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179573.660000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179573.660000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179573.664000] ACPI: Embedded Controller [EC0] (gpe 3) interrupt mode.
[17179573.696000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[17179573.696000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[17179573.696000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[17179573.696000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179573.700000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.700000] pnp: PnP ACPI init
[17179573.708000] pnp: PnP ACPI: found 11 devices
[17179573.708000] PnPBIOS: Disabled by ACPI PNP
[17179573.708000] PCI: Using ACPI for IRQ routing
[17179573.708000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.708000] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[17179573.708000] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[17179573.708000] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[17179573.708000] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
[17179573.728000] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[17179573.728000] pnp: 00:08: ioport range 0x1200-0x120f has been reserved
[17179573.728000] pnp: 00:08: ioport range 0x500-0x51f has been reserved
[17179573.728000] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[17179573.728000] PCI: Bridge: 0000:00:02.0
[17179573.728000]   IO window: 9000-9fff
[17179573.728000]   MEM window: c0100000-c01fffff
[17179573.728000]   PREFETCH window: c8000000-cfffffff
[17179573.728000] PCI: Bridge: 0000:00:06.0
[17179573.728000]   IO window: disabled.
[17179573.728000]   MEM window: disabled.
[17179573.728000]   PREFETCH window: disabled.
[17179573.728000] PCI: Bridge: 0000:00:07.0
[17179573.728000]   IO window: disabled.
[17179573.728000]   MEM window: disabled.
[17179573.728000]   PREFETCH window: disabled.
[17179573.728000] PCI: Bus 7, cardbus bridge: 0000:06:06.0
[17179573.728000]   IO window: 0000a400-0000a4ff
[17179573.728000]   IO window: 0000a800-0000a8ff
[17179573.728000]   PREFETCH window: 30000000-31ffffff
[17179573.728000]   MEM window: 34000000-35ffffff
[17179573.728000] PCI: Bridge: 0000:00:14.4
[17179573.728000]   IO window: a000-afff
[17179573.728000]   MEM window: c0200000-c02fffff
[17179573.728000]   PREFETCH window: 30000000-32ffffff
[17179573.728000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179573.728000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179573.728000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179573.728000] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179573.728000] NET: Registered protocol family 2
[17179573.764000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.764000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179573.764000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.764000] TCP: Hash tables configured (established 16384 bind 8192)
[17179573.764000] TCP reno registered
[17179573.764000] audit: initializing netlink socket (disabled)
[17179573.764000] audit(1169157959.764:1): initialized
[17179573.764000] VFS: Disk quotas dquot_6.5.1
[17179573.764000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.764000] Initializing Cryptographic API
[17179573.764000] io scheduler noop registered
[17179573.764000] io scheduler anticipatory registered
[17179573.764000] io scheduler deadline registered
[17179573.764000] io scheduler cfq registered (default)
[17179573.764000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179573.764000] pcie_portdrv_probe->Dev[5a34:1002] has invalid IRQ. Check vendor BIOS
[17179573.764000] assign_interrupt_mode Found MSI capability
[17179573.764000] Allocate Port Service[0000:00:02.0:pcie00]
[17179573.764000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179573.764000] pcie_portdrv_probe->Dev[5a38:1002] has invalid IRQ. Check vendor BIOS
[17179573.764000] assign_interrupt_mode Found MSI capability
[17179573.764000] Allocate Port Service[0000:00:06.0:pcie00]
[17179573.764000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179573.764000] pcie_portdrv_probe->Dev[5a39:1002] has invalid IRQ. Check vendor BIOS
[17179573.764000] assign_interrupt_mode Found MSI capability
[17179573.764000] Allocate Port Service[0000:00:07.0:pcie00]
[17179573.764000] isapnp: Scanning for PnP cards...
[17179574.120000] isapnp: No Plug & Play device found
[17179574.140000] Real Time Clock Driver v1.12ac
[17179574.140000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.140000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.140000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 217
[17179574.140000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[17179574.140000] mice: PS/2 mouse device common for all mice
[17179574.140000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.140000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.140000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.140000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.156000] i8042.c: Detected active multiplexing controller, rev 1.9.
[17179574.160000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179574.160000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179574.164000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179574.164000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179574.164000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.168000] EISA: Probing bus 0 at eisa.0
[17179574.168000] Cannot allocate resource for EISA slot 1
[17179574.168000] Cannot allocate resource for EISA slot 8
[17179574.168000] EISA: Detected 0 cards.
[17179574.168000] TCP bic registered
[17179574.168000] NET: Registered protocol family 1
[17179574.168000] NET: Registered protocol family 8
[17179574.168000] NET: Registered protocol family 20
[17179574.168000] Using IPI No-Shortcut mode
[17179574.168000] ACPI: (supports S0 S3 S4 S5)
[17179574.168000] Freeing unused kernel memory: 308k freed
[17179575.288000] Capability LSM initialized
[17179575.320000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179575.368000] ACPI: Thermal Zone [TZS0] (61 C)
[17179575.420000] ACPI: Thermal Zone [TZS1] (57 C)
[17179575.472000] ACPI: Thermal Zone [TZSV] (64 C)
[17179575.812000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179575.812000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 225
[17179575.812000] ATIIXP: chipset revision 0
[17179575.812000] ATIIXP: not 100% native mode: will probe irqs later
[17179575.812000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[17179575.812000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[17179575.812000] Probing IDE interface ide0...
[17179576.100000] hda: ST9100822A, ATA DISK drive
[17179576.772000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.772000] Probing IDE interface ide1...
[17179577.512000] hdc: MATSHITAUJ-845D, ATAPI CD/DVD-ROM drive
[17179577.848000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.860000] hda: max request size: 512KiB
[17179577.864000] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.864000] hda: cache flushes supported
[17179577.864000]  hda: hda1 hda2 hda3 hda4
[17179577.900000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.900000] Uniform CD-ROM driver Revision: 3.20
[17179578.252000] usbcore: registered new driver usbfs
[17179578.252000] usbcore: registered new driver hub
[17179578.252000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.252000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 233
[17179578.252000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179578.252000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179578.476000] ieee1394: Initialized config rom entry `ip1394'
[17179578.488000] ohci_hcd 0000:00:13.0: irq 233, io mem 0xc0000000
[17179578.548000] usb usb1: configuration #1 chosen from 1 choice
[17179578.548000] hub 1-0:1.0: USB hub found
[17179578.548000] hub 1-0:1.0: 4 ports detected
[17179578.652000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 233
[17179578.652000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179578.652000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179578.868000] ohci_hcd 0000:00:13.1: irq 233, io mem 0xc0001000
[17179578.928000] usb usb2: configuration #1 chosen from 1 choice
[17179578.928000] hub 2-0:1.0: USB hub found
[17179578.928000] hub 2-0:1.0: 4 ports detected
[17179579.032000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 233
[17179579.032000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179579.032000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[17179579.032000] ehci_hcd 0000:00:13.2: irq 233, io mem 0xc0002000
[17179579.032000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.032000] usb usb3: configuration #1 chosen from 1 choice
[17179579.032000] hub 3-0:1.0: USB hub found
[17179579.032000] hub 3-0:1.0: 8 ports detected
[17179579.136000] ACPI: PCI Interrupt 0000:06:06.2[C] -> GSI 22 (level, low) -> IRQ 50
[17179579.192000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[50]  MMIO=[c0208000-c02087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179579.248000] Attempting manual resume
[17179579.284000] kjournald starting.  Commit interval 5 seconds
[17179579.284000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.400000] ohci_hcd 0000:00:13.1: wakeup
[17179579.784000] usb 2-2: new low speed USB device using ohci_hcd and address 2
[17179579.992000] usb 2-2: configuration #1 chosen from 1 choice
[17179580.464000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[1234567812345678]
[17179588.488000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.536000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.948000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.220000] input: PC Speaker as /class/input/input0
[17179589.392000] irda_init()
[17179589.392000] NET: Registered protocol family 23
[17179589.524000] ieee80211_crypt: registered algorithm 'NULL'
[17179589.536000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179589.536000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
**[17179589.572000] bcm43xx driver**
[17179589.576000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 21 (level, low) -> IRQ 169
[17179589.636000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17179589.636000] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 23 (level, low) -> IRQ 58
[17179589.640000] eth1: Identified chip type is 'RTL8169s/8110s'.
[17179589.640000] eth1: RTL8169 at 0xe0992400, 00:0a:e4:e4:24:f2, IRQ 58
[17179589.656000] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179589.656000] Yenta: CardBus bridge found at 0000:06:06.0 [1025:0080]
[17179589.656000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179589.656000] Yenta: Routing CardBus interrupts to PCI
[17179589.656000] Yenta TI: socket 0000:06:06.0, mfunc 0x010a1b22, devctl 0x64
[17179589.800000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179589.800000] sdhci: Copyright(c) Pierre Ossman
[17179589.888000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 177
[17179589.888000] Socket status: 30000006
[17179589.888000] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #08
[17179589.888000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179589.888000] cs: IO port probe 0xa000-0xafff: clean.
[17179589.888000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[17179589.888000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x32ffffff
[17179589.888000] sdhci: SDHCI controller found at 0000:06:06.4 [104c:8034] (rev 0)
[17179589.892000] ACPI: PCI Interrupt 0000:06:06.4[A] -> GSI 20 (level, low) -> IRQ 177
[17179589.892000] mmc0: SDHCI at 0xc0209000 irq 177 DMA
[17179589.892000] mmc1: SDHCI at 0xc0208c00 irq 177 DMA
[17179589.892000] mmc2: SDHCI at 0xc0208800 irq 177 DMA
[17179589.964000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 217
[17179590.000000] ieee80211_crypt: registered algorithm 'WEP'
[17179590.056000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[17179590.088000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179590.088000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179590.088000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[17179590.088000] nsc-ircc, chip->init
[17179590.088000] nsc-ircc, Found chip at base=0x02e
[17179590.088000] nsc-ircc, driver loaded (Dag Brattli)
[17179590.088000] nsc_ircc_open(), can't get iobase of 0x2f8
[17179590.088000] nsc-ircc, Found chip at base=0x02e
[17179590.088000] nsc-ircc, driver loaded (Dag Brattli)
[17179590.088000] nsc_ircc_open(), can't get iobase of 0x2f8
[17179590.092000] pnp: Device 00:0a disabled.
[17179590.420000] ts: Compaq touchscreen protocol output
[17179590.484000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 217
[17179590.596000] MC'97 1 converters and GPIO not ready (0xff00)
[17179590.596000] ACPI: PCI Interrupt 0000:06:06.3[A] -> GSI 20 (level, low) -> IRQ 177
[17179590.676000] cs: IO port probe 0x100-0x3af: clean.
[17179590.676000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179590.680000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[17179590.680000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179590.680000] cs: IO port probe 0xa00-0xaff: clean.
[17179590.712000] usbcore: registered new driver hiddev
[17179590.724000] input: HID 1241:1177 as /class/input/input2
[17179590.724000] input: USB HID v1.10 Mouse [HID 1241:1177] on usb-0000:00:13.1-2
[17179590.724000] usbcore: registered new driver usbhid
[17179590.724000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179591.356000] lp: driver loaded but no devices found
[17179591.404000] SCSI subsystem initialized
[17179591.416000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179591.416000] ieee1394: sbp2: Try serialize_io=0 for better performance
**[17179591.440000] acer_acpi: Acer Laptop ACPI Extras version 0.3**
[17179591.480000] Adding 1052248k swap on /dev/disk/by-uuid/57b055b3-1b3d-4251-b57a-841b0a14ad10.  Priority:-1 extents:1 across:1052248k
[17179591.592000] EXT3 FS on hda3, internal journal
[17179600.132000] kjournald starting.  Commit interval 5 seconds
[17179600.140000] EXT3 FS on hda4, internal journal
[17179600.140000] EXT3-fs: mounted filesystem with ordered data mode.
**[17179600.420000] acer_acpi: Wireless value 1**
[17179601.688000] NET: Registered protocol family 17
[17179604.956000] ACPI: AC Adapter [ADP1] (on-line)
[17179605.172000] ACPI: Battery Slot [BAT0] (battery present)
[17179605.624000] ACPI: Power Button (FF) [PWRF]
[17179605.624000] ACPI: Lid Switch [LID0]
[17179605.624000] ACPI: Sleep Button (CM) [SLPB]
[17179605.684000] ACPI: ACPI Dock Station Driver 
[17179605.756000] ibm_acpi: ec object not found
[17179605.788000] pcc_acpi: loading...
[17179605.888000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179605.888000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179606.104000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179606.104000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4 (1450 mV)
[17179606.104000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[17179606.104000] cpu_init done, current fid 0x8, vid 0x4
[17179607.784000] [drm] Initialized drm 1.0.1 20051102
[17179607.792000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 66
[17179607.792000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179608.544000] [drm] Setting GART location based on new memory map
[17179608.548000] [drm] Loading R300 Microcode
[17179608.548000] [drm] writeback test succeeded in 1 usecs
**[17179612.260000] acer_acpi: Wireless value 1**
[17179612.320000] apm: BIOS not found.
[17179613.876000] input: AT Translated Set 2 keyboard as /class/input/input3
[17179614.848000] ttyS1: LSR safety check engaged!
[17179616.912000] NET: Registered protocol family 10
[17179616.912000] lo: Disabled Privacy Extensions
[17179616.912000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179616.912000] IPv6 over IPv4 tunneling driver
[17179617.568000] Bluetooth: Core ver 2.8
[17179617.568000] NET: Registered protocol family 31
[17179617.568000] Bluetooth: HCI device and connection manager initialized
[17179617.568000] Bluetooth: HCI socket layer initialized
[17179617.604000] Bluetooth: L2CAP ver 2.8
[17179617.604000] Bluetooth: L2CAP socket layer initialized
[17179617.624000] Bluetooth: RFCOMM socket layer initialized
[17179617.624000] Bluetooth: RFCOMM TTY layer initialized
[17179617.624000] Bluetooth: RFCOMM ver 1.7
[17179618.224000] vmmon: module license 'unspecified' taints kernel.
[17179618.228000] /dev/vmmon[4733]: Module vmmon: registered with major=10 minor=165
[17179618.228000] /dev/vmmon[4733]: Module vmmon: initialized
[17179618.800000] /dev/vmnet: open called by PID 4760 (vmnet-bridge)
[17179618.800000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179618.800000] /dev/vmnet: port on hub 0 successfully opened
[17179618.800000] bridge-eth0: peer interface eth0 not found, will wait for it to come up
[17179618.800000] bridge-eth0: attached
[17179618.912000] /dev/vmnet: open called by PID 4776 (vmnet-natd)
[17179618.912000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179618.912000] /dev/vmnet: port on hub 8 successfully opened
[17179619.232000] /dev/vmnet: open called by PID 4803 (vmnet-netifup)
[17179619.232000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179619.232000] /dev/vmnet: port on hub 1 successfully opened
[17179619.240000] /dev/vmnet: open called by PID 4804 (vmnet-netifup)
[17179619.240000] /dev/vmnet: port on hub 8 successfully opened
[17179619.828000] /dev/vmnet: open called by PID 4845 (vmnet-dhcpd)
[17179619.828000] /dev/vmnet: port on hub 8 successfully opened
[17179620.428000] /dev/vmnet: open called by PID 4846 (vmnet-dhcpd)
[17179620.428000] /dev/vmnet: port on hub 1 successfully opened
[17179622.436000] ttyS1: LSR safety check engaged!
**[COLOR="Red"][17179624.716000] bcm43xx: IRQ_READY timeout[/COLOR]**
[17179629.496000] vmnet1: no IPv6 routers present
[17179629.756000] vmnet8: no IPv6 routers present

```
and output of lsmod:
```
:~$ lsmod
Module                  Size  Used by
vmnet                  41900  12 
vmmon                 118668  0 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  17 
radeon                118816  2 
drm                    74644  3 radeon
powernow_k8            15008  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dock                    8716  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
af_packet              24584  0 
nls_iso8859_1           5248  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
**acer_acpi               7428  0 **
sbp2                   24584  0 
scsi_mod              144648  1 sbp2
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
usbhid                 45152  0 
joydev                 11200  0 
tsdev                   9152  0 
pcmcia                 40380  0 
tifm_7xx1               9472  0 
snd_atiixp_modem       17800  0 
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
arc4                    3200  2 
snd_seq_midi            9984  0 
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
ieee80211_crypt_wep     6528  1 
snd_atiixp             21388  1 
snd_ac97_codec         97696  2 snd_atiixp_modem,snd_atiixp
snd_ac97_bus            3456  1 snd_ac97_codec
sdhci                  20108  0 
mmc_core               32136  1 sdhci
tifm_core              10496  1 tifm_7xx1
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
r1000                  17792  0 
r8169                  32136  0 
**bcm43xx               127252  0 **
**ieee80211softmac       33792  1 bcm43xx**[B]
ieee80211              35272  2 bcm43xx,ieee80211softmac[/B]
ieee80211_crypt         7552  2 ieee80211_crypt_wep,ieee80211
snd_pcm                84612  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_seq,snd_pcm
irda                  214332  0 
psmouse                41352  0 
serio_raw               8452  0 
evdev                  11392  2 
pcspkr                  4352  0 
snd                    58372  13 snd_atiixp_modem,snd_seq_oss,snd_rawmidi,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  3 snd_atiixp_modem,snd_atiixp,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ati_agp                10636  0 
agpgart                34888  2 drm,ati_agp
crc_ccitt               3200  1 irda
ext3                  142728  2 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ohci_hcd               22532  0 
usbcore               134912  4 usbhid,ehci_hcd,ohci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  5 
generic                 6276  0 
atiixp                  7824  1 
thermal                15624  0 
processor              31560  2 powernow_k8,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

thanks for your help

---

### Post by GwadaBreizh on 2007-01-20
Any ideas ?

---

