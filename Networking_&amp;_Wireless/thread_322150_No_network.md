---
title: "No network"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by Oppunome on 2006-12-20
I'm a Win expert, but Linux noob and can't get my network to work. I'm not certain that my network card works properly since I built the PC from collected bits and pieces. Asus MB with Pentium 3 and 3com PCI nic; everything seems to work perfectly, 6.10 installs without a hitch, nic lights up, switch port blinks for a couple of seconds during each boot, but no network available. I've read some of the other comments here and will try some things tonight (lshw...), but can't atttm. How do I make linux (Gnome) recognise my nic after i've installed and it's running?](*,) 

Another very noobish question, how do I enter the commands (sudo lshw...), in terminal?:-k 

Thank you in advance for any help, I'm impressed with how nice linux has become. I've always been afraid to get my feet wet, now I wish I'd done it sooner.

O

---

### Post by n00b@linux on 2006-12-20
Welcome to linux.
 
If you're in the GUI, you can open a terminal to get to the command line. Navigate with your mouse: Applications > Accessories > Terminal. To enter a command, you just type it at the prompt and hit <return> (just like cmd.exe in Windoze). Try this:```
lspci
```The command 'lspci' lists your PCI devices. You should see your ethernet controller there. Post the details to this thread as this will help. A similar command, 'lsusb' lists your USB devices, which is useful if you happen to be using a USB wireless adapter. Another useful command is 'lsmod' which lists the kernel modules which have been installed (btw, kernel module = device driver). Once you know your chipset (from 'lspci') you can google to identify the name of the kernel module needed and run 'lsmod' to see if that module's been installed or not. If there's no linux kernel module for the chipset, then you'll have to use ndiswrapper.
 
Please be aware that some commands require you to have root privileges/permissions, eg. 'lspci -v'. When you run these commands you prefix them by the word 'sudo'. For example:```
sudo lspci -v
```
 
To 'make linux recognise your nic' can mean a lot of things in linux-speak:
1. to see if the kernel has recognised the device (can be checked with 'lspci' as per above)
2. to see if the device's driver has been loaded (can be checked with 'lsmod' as per above)
3. to configure the interface and make it available for use (this requires passing certain parameters with the 'ifconfig' command while using root privileges, ie. 'sudo ifconfig')
 
1. and 2. should be answered if you follow the advice in my first few paragraphs. As to 3. well let's cross that bridge when we come to it.
 
FYI, if you ever want to see get some background on a particular command, look at the man page for it. For example```
man ifconfig
```Note: navigate with the arrow keys and press 'q' to quit the man page when you've finished with it.

---

### Post by Oppunome on 2006-12-20
Thanks for the advise, but nothing seems to be as it should. 1st lspci gets me nothing, zero, no matter if I add sudo, or -vvxxx, nothing! lshw gives me a long list of my machine, but no nic. I checked the interfaces file and everything's on auto, but networking restart brings only errors and ifconfig shows only lo and sit0.

I'm going to check my bios to see if something's set wrong, but I don't think so. I was wrong about 1 thing, the MB isn't Asus, it's a Tyan Tiger, but I know that all components ran properly about 6 months ago.

I'm beginning to think it would be best to install a floppy, make a network boot disk and see if I get network. Can you suggest anything else?

Thanks again!
O

PS Just downloaded a test app from 3Com (3link-id) put it on a DOS bootdisk and my card tests OK. This means the PCI bus is being recognised, linux just isn't seeing/recognising it.

---

### Post by Iowan on 2006-12-20
IIRC, I tried putting Breezy on a couple of boxes w/ 3COM cards - default installation didn't recognize them.  Not knowing where/how to download drivers for them, I used a different card.  I haven't pursued it... but I have several 3COM cards (I'm fond of them).

---

### Post by Iowan on 2006-12-20
OK, I found this one on '509's:
[http://ubuntuforums.org/showthread.php?t=16694]("http://ubuntuforums.org/showthread.php?t=16694")

RATS!! My attempt to edit became a double post...

---

### Post by Oppunome on 2006-12-21
Only one problem, that discussion concerns the 3c509 ISA nic, I use the 3c905 PCI nic. The card uses IRQ 11 and has no conflict with anything else. I tried setting BIOS to safe settings and to performance settings with no results. Linux will not recognise my nic.

The only other PCI nic I have available is a Genius, but it isn't recognised either.

](*,) 

O

---

### Post by n00b@linux on 2006-12-21
> **Oppunome said:**
> 1st lspci gets me nothing, zero, no matter if I add sudo, or -vvxxx, nothing!You have a serious problem if you're not getting anything. lspci is a basic command. If you're getting no response, you need to check the md5sum of the iso you burnt and (possibly) re-download/burn/install. **he thinks**Err, you did use the correct case, didn't you? Unlike Windoze, linux is case sensitive.

---

### Post by hermes767 on 2006-12-21
I would like to chip in here - since I am having the same problems. My card is not recognised in ubuntu but is working in Win98 (dual boot). The card is kingston KNE20T and is recognised as NE2000 and worked in SuSe.
But the card is not being recognised in  ubuntu - tried pppoeconf but no it says run modconf but guess what there is no modconf !
Ok found it as a compressed file downloaded in windows and took acroos to ubuntu tried the basic install procedure but then ./configure does not work !!!! 
This is all tedious and catch 22.
Must be a simpler solution..........please anyone

---

### Post by hermes767 on 2006-12-21
Going to clean out and do fresh re-install then see.

---

### Post by n00b@linux on 2006-12-21
Here is the wireless trouble shooting algorithm I use:
1. run 'iwconfig' so see if your wireless nic is listed.
2. run 'lspci' (or 'lsusb' if it's a USB stick) to if the kernel recognises it.
3. find out the chipset used in the device, ie. the manufacturer of the device may use chipsets made by someone else. It is the chipset manufacturer and model that is important, not the vendor's make and model details.
4. google around to see if the chipset is supported in linux directly (ie. a kernel module already exists for it) or whether you have to use ndiswrapper (in which case google to see if there are any previous success stories that you can copy).
5. either get a copy of the kernel module and install it, or run ndiswrapper.
 
@hermes767
If SuSE recognises it, then find the relevant kernel module your SuSE kernel uses and copy it across to Ubuntu and install it there.

---

### Post by Iowan on 2006-12-21
> **Oppunome said:**
> Only one problem, that discussion concerns the 3c509 ISA nic, I use the 3c905 PCI nic.
OK, how 'bout this one?
[http://www.ubuntuforums.org/showthread.php?t=166937]("http://www.ubuntuforums.org/showthread.php?t=166937")
The author of this thread seems to have one working:
[http://www.ubuntuforums.org/showthread.php?t=318586]("http://www.ubuntuforums.org/showthread.php?t=318586")

---

### Post by Oppunome on 2006-12-22
Good thread, I have only one difference, my installation never hangs and after going through all of the admin commands and experimenting I think I can safely say that Linux can't find my PCI bus. 

Some of the commands (probably not all) I tried are; lspci, setpci, mii -diag, mii -tool.

They all tell me essentially the same thing, I have no pci slots with cards in them. Problem is I have 3 cards, 1 3com 3c905, 1 Genius GE2500III nic and a USB card. According to above listed tools, nothing there.

From various threads I found things that looked interesting;
modprobe 3c95x - ifconfig -a still brings nothing
modprobe ne - networking restart does nothing

the one command that seems to bring something meaningful (if I could interpret it) is;
lsmod | grep 3c59x - which returns;

3c59x   47912   0
mii         6512   1   3c59x

I assume it only shows me that I've loaded the 3c59x driver in the kernel and nothing more.

When i looked through the System Admin part of the docs I found a list of commands, when I look through lspci there's info about pcilib, How can I access that command? When I do a lspci -M, pcilib does a thorough search of the PCI bus, but the top is cut off so I can't read it. I'd also like to be able to set it to use the Intel_conf1 or 2. I get the impression that it uses the linux method which reads a file /proc/bus/pci/devices, this file is empty on my machine. Is that normal? In the file /usr/share/misc/pci.ids I found my nic, Vendor - 10b7, device - 9200 - subvendor - 10b7, subdevice - 1000 so I know that linux is aware of this card, I still think the problem is with the PCI bus itself, or actually with linux accessing the PCI bus!

Tough nut, would really appreciate any help in cracking it. I don't give up easily, but i'm beginning to hate linux as much as I do Microdoof (as the germans call it).

Help me oh great linux guru in the sky!

Thanx

O

---

### Post by Oppunome on 2006-12-23
If it helps, here's my dmesg log. One thing that interests me, during the PCI recognition the statement;

PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

How do I do that? Can anyone tell me?

Just above there it show 4 lines where it seems to find the used PCI IRQs. At boot my PC shows that my nic is using IRQ 11, so I assume that linux is aware of it. It also says that ACPI found 13 devices.

Can anyone make sense of this?

Thanks again,

O

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000004fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000004fff0000 - 000000004fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000004fff3000 - 0000000050000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 383MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5940
[17179569.184000] On node 0 totalpages: 327664
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 98288 pages, LIFO batch:31
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 VIA694                                ) @ 0x000f71c0
[17179569.184000] ACPI: RSDT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x4fff3000
[17179569.184000] ACPI: FADT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x4fff3040
[17179569.184000] ACPI: MADT (v001 VIA694          0x00000000  0x00000000) @ 0x4fff5680
[17179569.184000] ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:7 APIC version 17
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 501.230 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.020000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.024000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.252000] Memory: 1289076k/1310656k available (1910k kernel code, 20388k reserved, 1070k data, 308k init, 393152k highmem)
[17179572.252000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.332000] Calibrating delay using timer specific routine.. 1003.70 BogoMIPS (lpj=2007403)
[17179572.332000] Security Framework v1.0.0 initialized
[17179572.332000] SELinux:  Disabled at boot.
[17179572.332000] Mount-cache hash table entries: 512
[17179572.332000] CPU: After generic identify, caps: 0387fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179572.332000] CPU: After vendor identify, caps: 0387fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179572.332000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179572.332000] CPU: L2 cache: 512K
[17179572.332000] CPU serial number disabled.
[17179572.332000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[17179572.332000] Checking 'hlt' instruction... OK.
[17179572.348000] SMP alternatives: switching to UP code
[17179572.348000] Freeing SMP alternatives: 16k freed
[17179572.348000] checking if image is initramfs... it is
[17179574.340000] Freeing initrd memory: 5564k freed
[17179574.340000] ACPI: Core revision 20060707
[17179574.344000] ACPI: Looking for DSDT ... not found!
[17179574.852000] CPU0: Intel Pentium III (Katmai) stepping 03
[17179574.852000] Total of 1 processors activated (1003.70 BogoMIPS).
[17179574.852000] ENABLING IO-APIC IRQs
[17179574.852000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179574.996000] Brought up 1 CPUs
[17179574.996000] migration_cost=0
[17179574.996000] NET: Registered protocol family 16
[17179574.996000] EISA bus registered
[17179574.996000] ACPI: bus type pci registered
[17179575.012000] PCI: PCI BIOS revision 2.10 entry at 0xfb2c0, last bus=1
[17179575.012000] PCI: Using configuration type 1
[17179575.012000] Setting up standard PCI resources
[17179575.024000] ACPI: Interpreter enabled
[17179575.024000] ACPI: Using IOAPIC for interrupt routing
[17179575.028000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179575.028000] PCI: Probing PCI hardware (bus 00)
[17179575.028000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179575.036000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[17179575.036000] Boot video device is 0000:01:00.0
[17179575.036000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179575.036000] ACPI Error (rscreate-0349): (PRT[18].SourceIndex) Need Integer, found Reference [20060707]
[17179575.036000] ACPI Exception (pci_irq-0215): AE_BAD_DATA, Evaluating _PRT [AE_BAD_DATA] [20060707]
[17179575.036000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[17179575.040000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179575.040000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[17179575.040000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[17179575.052000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179575.052000] pnp: PnP ACPI init
[17179575.064000] pnp: PnP ACPI: found 13 devices
[17179575.064000] PnPBIOS: Disabled by ACPI PNP
[17179575.064000] PCI: Using ACPI for IRQ routing
[17179575.064000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179575.068000] PCI: Bridge: 0000:00:01.0
[17179575.068000]   IO window: disabled.
[17179575.068000]   MEM window: dc000000-ddffffff
[17179575.068000]   PREFETCH window: d4000000-dbffffff
[17179575.068000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179575.068000] NET: Registered protocol family 2
[17179575.104000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179575.104000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179575.120000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179575.124000] TCP: Hash tables configured (established 262144 bind 65536)
[17179575.124000] TCP reno registered
[17179575.128000] audit: initializing netlink socket (disabled)
[17179575.128000] audit(1166890861.128:1): initialized
[17179575.128000] highmem bounce pool size: 64 pages
[17179575.128000] VFS: Disk quotas dquot_6.5.1
[17179575.128000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179575.128000] Initializing Cryptographic API
[17179575.128000] io scheduler noop registered
[17179575.128000] io scheduler anticipatory registered
[17179575.128000] io scheduler deadline registered
[17179575.128000] io scheduler cfq registered (default)
[17179575.128000] isapnp: Scanning for PnP cards...
[17179575.484000] isapnp: No Plug & Play device found
[17179575.612000] Real Time Clock Driver v1.12ac
[17179575.616000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179575.616000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.616000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179575.616000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.616000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179575.620000] mice: PS/2 mouse device common for all mice
[17179575.620000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179575.624000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179575.624000] ide: Assuming 50MHz system bus speed for PIO modes; override with idebus=xx
[17179575.624000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179575.624000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179575.624000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179575.624000] EISA: Probing bus 0 at eisa.0
[17179575.624000] Cannot allocate resource for EISA slot 1
[17179575.624000] Cannot allocate resource for EISA slot 4
[17179575.628000] EISA: Detected 0 cards.
[17179575.628000] TCP bic registered
[17179575.628000] NET: Registered protocol family 1
[17179575.628000] NET: Registered protocol family 8
[17179575.628000] NET: Registered protocol family 20
[17179575.628000] Using IPI No-Shortcut mode
[17179575.628000] ACPI: (supports S0 S1 S5)
[17179575.628000] Freeing unused kernel memory: 308k freed
[17179575.656000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179577.020000] Capability LSM initialized
[17179577.176000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179577.176000] ACPI: Getting cpuindex for acpiid 0x1
[17179578.260000] Probing IDE interface ide0...
[17179579.100000] hda: ExcelStor Technology CT210, ATA DISK drive
[17179579.776000] Probing IDE interface ide1...
[17179580.644000] hdc: SAMSUNG DVD-ROM SD-616E, ATAPI CD/DVD-ROM drive
[17179580.980000] Probing IDE interface ide2...
[17179581.544000] Probing IDE interface ide3...
[17179582.108000] Probing IDE interface ide4...
[17179582.672000] Probing IDE interface ide5...
[17179583.236000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179583.236000] ide1 at 0x170-0x177,0x376 on irq 15
[17179583.272000] hda: max request size: 128KiB
[17179583.272000] hda: 20040450 sectors (10260 MB) w/512KiB Cache, CHS=19881/16/63
[17179583.272000] hda: cache flushes not supported
[17179583.272000]  hda: hda1 hda2 < hda5 >
[17179583.988000] hdc: ATAPI 48X DVD-ROM drive, 512kB Cache
[17179583.988000] Uniform CD-ROM driver Revision: 3.20
[17179584.512000] Attempting manual resume
[17179584.580000] kjournald starting.  Commit interval 5 seconds
[17179584.580000] EXT3-fs: mounted filesystem with ordered data mode.
[17179619.100000] Floppy drive(s): fd0 is 1.44M
[17179619.120000] FDC 0 is a post-1991 82077
[17179619.356000] input: PS2++ Logitech MX Mouse as /class/input/input1
[17179620.412000] input: PC Speaker as /class/input/input2
[17179620.536000] parport: PnPBIOS parport detected.
[17179620.536000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179620.568000] ts: Compaq touchscreen protocol output
[17179622.136000] lp0: using parport0 (interrupt-driven).
[17179622.420000] Adding 441748k swap on /dev/disk/by-uuid/90830af7-403e-40ec-95ee-c7138b4c7737.  Priority:-1 extents:1 across:441748k
[17179622.552000] EXT3 FS on hda1, internal journal
[17179624.924000] NET: Registered protocol family 17

---

### Post by Oppunome on 2006-12-25
Anyone?

---

### Post by Oppunome on 2006-12-25
So, I downloaded a new copy of Ubuntu 6.10 and booted my system with the CD, still no network. ](*,) 

Are there no ohter ideas?

Thanx

0

---

### Post by Oppunome on 2006-12-25
Forget it experts, I solved it all by myself! I found an interesting tip to click F6 in the installation window and type in; ACPI=off noapic nolapic

and everything worked perfectly, usb works and network works.

Thank you all for your help,

Merry Christmas

O

---

### Post by hermes767 on 2006-12-27
Well for those interested who have  similar NE2000 problems I solved mine using isapnptools - see [www.roestock.demon.co.uk/isapnptools](www.roestock.demon.co.uk/isapnptools).
Sendind results of pnpdump to a config file then using this file with isapnp command enabled the card then modprobe worked to install ne.ko module.
Strange thing is system now sees two devices eth0 and eth1 each with different io and irq yet only one works ! But tis not the one I set up !  Well well well must be a guru somewhere who understands !

---

