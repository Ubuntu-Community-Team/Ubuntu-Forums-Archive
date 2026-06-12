---
title: "Unable to detect my PCMCIA network card"
date: 2005-04-22
forum: Networking &amp; Wireless
---

### Post by niigatapeter on 2005-04-22
I installed Ubuntu on my laptop the other day, and since this is my first contact with Linux ever, I'm pretty much lost.  I'm using and old Toshiba Dynabook laptop with a PCMCIA network card called "Ether II PCC-TD" by the manufacturer Corega. According to Corega's homepage, this card works with Linux. The instructions for this are few though; they only refer to /etc/pcmcia/config   and  the lines   

card "corega EtherII PCC-TD"
version "corega K.K.", "corega EtherII PCC-TD"
bind "pcnet_cs" 

and then reactivation of the network by # /etc/rc.d/init.d/pcmcia restart 
Unfortunately this is all greek to me...

My situation at the moment is that the card comes to live at boot up, and starts sending packets with something called "lo loop interface"... But when I check in   System Administration>>>Network Settings      no  network card is found,  only the built in modem.  I had a look at the forum and figured that I should check if the "pcnet_cs" module was loaded or not, which it wasn't.  So I added the line pcnet_cs into   /etc/modules.   Now if I write  lsmod in the terminal, I find that the module is loaded, but "used by 0"   if I understood it correctly...   

Also, I tried to enter the following lines into   /etc/network/interfaces :
auto eth0
iface eth0 inet dhcp

, but that didn't help either.   If I type ifup eth0 in the terminal  I get the following result:

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth0.

I'm stuck at this point, and I can't seem to find any information on the forum that could give me a clue how to fix it.  If any kind person could help me with this, I would really appreciate it.

/Cheers    Peter

---

### Post by notzac on 2005-04-23
Hi Peter,

I can't give you an instant fix, but what is the output of you running the command 'lspci'? Does anything resembling your ethernet card show up there?

Also seeing as it's a PCMCIA card - what is the output of 'cardctl status' and 'cardctl info'?

---

### Post by niigatapeter on 2005-04-23
Hello Notzac, and thank you for helping!

The command 'lspci' doesn't seem to produce anything about my card. The output is:

0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 11)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BAM ISA Bridge (LPC) (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801BAM IDE U100 (rev 03)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 03)
0000:00:1f.6 Modem: Intel Corp. Intel 537 [82801BA/BAM AC'97 Modem] (rev 03)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
0000:02:02.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:02:0a.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 31)
0000:02:0a.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 31)


The 'cardctl status' command results in:

root@ubuntu:/ # cardctl status
Socket 0:
  no card
Socket 1:
  5V 16-bit PC Card
  function 0: [ready], [wp]
root@ubuntu:/ #



The  'cardctl info' , however, gives the following, very interesting info:

root@ubuntu:/ # cardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="corega K.K."
PRODID_2="corega EtherII PCC-TD"
PRODID_3=""
PRODID_4=""
MANFID=1234,5678
FUNCID=6
root@ubuntu:/ #

---

### Post by notzac on 2005-04-23
Interesting indeed. From what you've written, your card should be being identified correctly and the correct drivers loaded in without further ado - Ubuntu already has everything in  /etc/pcmcia/config that it should need to bring the card up. Odd that it doesn't appear to do much in the way of useful for you :/

Have you tried it in the other pcmcia slot at all? Also, if you issue these two commands:

sudo cardctl reset
sudo cardctl insert

and then run 'dmesg' .. does anything show up about the card?

---

### Post by niigatapeter on 2005-04-23
Hello Noztac, and once again, thank you for helping!

I've tried   the 

sudo cardctl eject
sudo cardctl reset
sudo cardctl insert

commands, and the system responds as one could anticipate. After "sudo cardctl eject", the card "died".  I tried the "cardctl info" command, and certainly the card was gone. I continued with "sudo cardctl insert" and voilà it was there again, with the LED lamps blinking again....   So it does seem like the system finds and indeed handles the card, but it's like it doesn't recognize it as a network card..?

Also,  the card does work. I'm dualbooting with Windows XP (I only have one computer) and of course I'm using this card to access the internet with XP. Also, there isn't anything strange with my internet connection (such as a dialup ADSL modem).   When I connect to internet, I just plug into the wall and recieve an IP number automatically. 

I've tried the card in both PCMCIA slots, and it's the same result. The system finds it, and identifies it correctly as "Corega EtherII..."  when I type "cardctl info". But  when I enter the System Administration>>>Network Settings , only the built in modem is found, and I can't  connect to the internet.

Do you think I should add something to  /etc/network/interfaces ?    I've already added the lines:

auto eth0
iface eth0 inet dhcp

earlier, but...   is eth0 incorrect?  Should I use something else instead of "eth" since it's a  PCMCIA card?       Is there some way for me to "point" at the PCMCIA card?


The "dmesg" command didn't seem to  reveal anything about the card.  The output was:

root@ubuntu:/ # dmesg
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
 BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
 BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000000bff0000 (usable)
 BIOS-e820: 000000000bff0000 - 000000000c000000 (ACPI data)
 BIOS-e820: 00000000feea0000 - 00000000feec0000 (reserved)
 BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
 BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
191MB LOWMEM available.
On node 0 totalpages: 49136
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 45040 pages, LIFO batch:10
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.3 present.
ACPI: RSDP (v000 TOSHIB                                ) @ 0x000f0170
ACPI: RSDT (v001 TOSHIB V1465CCC 0x20010119 TASM 0x04010000) @ 0x0bff0000
ACPI: FADT (v002 TOSHIB V1465CCC 0x20010119 TASM 0x04010000) @ 0x0bff0058
ACPI: DBGP (v001 TOSHIB V1465CCC 0x20010119 TASM 0x04010000) @ 0x0bff00dc
ACPI: BOOT (v001 TOSHIB V1465CCC 0x20010119 TASM 0x04010000) @ 0x0bff0030
ACPI: DSDT (v001 TOSHIB V1465CCC 0x20010402 MSFT 0x0100000a) @ 0x00000000
ACPI: PM-Timer IO Port: 0xee08
Built 1 zonelists
Kernel command line: root=/dev/hda2 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01183000)
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 16384 bytes)
Detected 697.881 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 187292k/196544k available (1436k kernel code, 8648k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1380.35 BogoMIPS (lpj=690176)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 128K
CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000
CPU: Intel Celeron (Coppermine) stepping 0a
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0e00)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfcd6d, last bus=4
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
ACPI: Power Resource [PFN0] (off)
ACPI: Power Resource [PFN1] (off)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 10 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
Simple Boot Flag at 0x7c set to 0x1
audit: initializing netlink socket (disabled)
audit(1114329341.432:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 11 (level, low) -> IRQ 11
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 1024 buckets, 8Kbytes
TCP: Hash tables configured (established 16384 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
CBC0 CBC1 AMDM  LID
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Fan [FAN0] (off)
ACPI: Fan [FAN1] (off)
ACPI: CPU0 (power states: C1[C1] C2[C2])
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Thermal Zone [THRM] (47 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH2M: IDE controller at PCI slot 0000:00:1f.1
ICH2M: chipset revision 3
ICH2M: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xeff0-0xeff7, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xeff8-0xefff, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: TOSHIBA MK2016GAP, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 39070080 sectors (20003 MB), CHS=38760/16/63, UDMA(66)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 >
Probing IDE interface ide1...
hdc: CD-W24E, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda2, internal journal
hdc: ATAPI 24X CD-ROM CD-R/RW drive, 1280kB Cache
Uniform CD-ROM driver Revision: 3.20
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
input: PS/2 Generic Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
input: PC Speaker
Real Time Clock Driver v1.12
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel i815 Chipset.
agpgart: Maximum main memory to use for agp memory: 149M
agpgart: AGP aperture is 64M @ 0xf0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
hw_random hardware driver 1.0.0 loaded
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1f.2[D] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1f.2: Intel Corp. 82801BA/BAM USB (Hub #1)
PCI: Setting latency timer of device 0000:00:1f.2 to 64
uhci_hcd 0000:00:1f.2: irq 11, io base 0xef80
uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 49138 usecs
intel8x0: clocking to 48000
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
PCI: Enabling device 0000:02:02.0 (0000 -> 0002)
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:02:02.0 to 64
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Runaway loop while stopping context: ...
ohci1394: fw-host0: Runaway loop while stopping context: ...
ohci1394: fw-host0: Runaway loop while stopping context: ...
ohci1394: fw-host0: Runaway loop while stopping context: ...
ohci1394: fw-host0: OHCI-1394 165.165 (PCI): IRQ=[10]  MMIO=[10000000-100007ff]  Max Packet=[65536]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to setting max_packet_size to 512 bytes
PCI: Enabling device 0000:02:0a.0 (0000 -> 0002)
ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
ACPI: PCI interrupt 0000:02:0a.0[A] -> GSI 10 (level, low) -> IRQ 10
Yenta: CardBus bridge found at 0000:02:0a.0 [1179:0001]
Yenta: ISA IRQ mask 0x00b8, PCI irq 10
Socket status: 30000011
PCI: Enabling device 0000:02:0a.1 (0000 -> 0002)
ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
ACPI: PCI interrupt 0000:02:0a.1[B] -> GSI 11 (level, low) -> IRQ 11
Yenta: CardBus bridge found at 0000:02:0a.1 [1179:0001]
Yenta: ISA IRQ mask 0x00b8, PCI irq 11
Socket status: 30000007
ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
NET: Registered protocol family 17
ACPI: AC Adapter [ADP1] (on-line)
ACPI: Battery Slot [BAT1] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ibm_acpi: ec object not found
toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a
toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
toshiba_acpi: Toshiba hotkeys are sent as ACPI events
toshiba_acpi: ktoshkeyd will check 2 times per second
toshiba_acpi: Dropped 0 keys from the queue on startup
ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
apm: BIOS not found.
cs: IO port probe 0x0100-0x04ff: excluding 0x1e0-0x1e7 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
cs: memory probe 0xa0000000-0xa0ffffff: clean.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
root@ubuntu:/ #

---

### Post by dethwulf on 2005-06-18
I've been searching all morning, and this post is the closest I've gotten to my problem. So, I appologize for bringing up old threads, but most of my problem is very similar to his.

In my case, I'm attempting to use a Gateway Solo 2500 with a Network Everywhere Fast Ethernet 10/100 PC Card.

Everything shows up fine on cardctl commands. On dmesg, I get the following when I pull the card myself, or use cardctl eject/reset/insert:

```
... dozens of lines of stuff
pcnet_cs: this is an AX88190 card!
pcnet_cs: use axnet_cs instead.
pcnet_cs: unable to read hardare net address for io base 0x300
```
So, following the instructions of the almighty Ubuntu, can anyone tell me where this axnet_cs fellow is? and how I can get him in me computer?

- wulf

---

### Post by dethwulf on 2005-06-18
Ah, the sweet taste of victory. It took some hacking into /etc/pcmcia/config, but I got it. At least, that's what I think fixed it.

Here's my thought pattern:

Searched all morning trying to find this elusive axnet_cs character. Found him, and he turned out to be the driver for the AX-based network adapters. I noticed that when I inserted the card, it was loading pcnet_cs, which is axnet's couter-part. With some more searching, I found the list of supported network adapters in the Linux Documentation Project. In it, my adapter, a Linksys Network Everywhere 10/100 PC Card, has a version 2 listed under pcnet_cs, and version 1 under axnet_cs.

I had also found that cardmgr, the daemon that runs the PCMCIA service, gives off beeps to indicate whether it worked or not. High beeps are good, low beeps are bad. I, of course, was getting one high, one low.

I found another site explaining how PCMCIA drivers are loaded, using the /etc/pcmcia/config hardware database. With some pocking around in there, I figured the format out, and replaced the "pcnet_cs" under a few cards similar to mine to "axnet_cs".

I rebooted, and happily got two high tone beeps from cardmgr. Upon login, I ran ifconfig eth0 up, and no errors were returned. Checking the Networking section under Administartion, sure enough, my NIC had shown up. Configured and working.

She's happily updating packages as I'm typing.

Now on to the video card...

- wulf

---

### Post by 1sy8 on 2005-06-20
Sorry to get this thread up myself ..

As I said here [http://www.ubuntuforums.org/showthread.php?t=42256](http://www.ubuntuforums.org/showthread.php?t=42256) , I lost my 3c574_cs eth0 card after I dist-upgraded from Warty.


- After I loaded manually the 3c574_cs module (it failed to load on boot as it did under Warty), cardmgr tells me now : no sockets found !

- ifup eth0 returns sit0: unknown hardware address type 776 error !

- cardctl reset|eject|info all answer open_sock() : No such device

- a modinfo 3c574_cs confirms that the loaded module came with the 2.6.10-5-386 kernel shipped with Hoary !!

I really would like to avoid a brand new install on this laptop as it is a very old and slow machine, so any idea would be really welcome !

---

### Post by 1sy8 on 2005-06-22
Anyone ?

---

### Post by dethwulf on 2005-06-28
1sy8,

Have you confirmed that your PC Card reader is installed? It sounds like it's not even recognizing the PC Card bus. Did you check dmesg and Device Manager?

- wulf

---

### Post by 1sy8 on 2005-07-06
Dethwulf,

The PCMCIA slot is inside the 365xd so I'm sure it's there !!

Now, I think it's a problem with the new kernel shipped with Hoary !! 

As mentioned here 
[http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-2.html#ss2.1](http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO-2.html#ss2.1) the only solution would be to recompile a kernel myself. I think this problem is a big mess from the Ubuntu kernel packagers !! The problem is I'm stuck as this network card IS my only way to the internet from the 365xd !!

I already tried 2.6.8.x (from Warty) recovery mode but the card didn't get up as it used to do before !

FYI, I simulated a Warty re-install and the card was working OK again so we can rule out any hardware pb ! I didn't complete the install for now as the same very nasty pb would come back again as soon as I upgrade it ! I gonna fill a bug report !

---

### Post by niigatapeter on 2007-01-22
This problem was ultimately resolved by modifying the file /etc/pcmcia/config with instructions (in Japanese, but if one identifies the part relating to the EtherII, it is self-explationary) from Corega.

Here is the homepage:
[http://www.corega.co.jp/product/os/vine215.txt](http://www.corega.co.jp/product/os/vine215.txt)

Sorry for not posting the solution earlier

---

