---
title: "conflicting modules"
date: 2005-07-12
forum: Networking &amp; Wireless
---

### Post by pacz on 2005-07-12
I just installed the nvidia glx module and enabled it, after which my Ubuntu promptly failed to recognize my ethernet card, which I had previously installed the sk98lin module for.

I have no idea how to fix a problem like this :confused: 

do you?

---

### Post by scoon on 2005-07-12
Hey there, 

Is there anything in dmesg ?  Did /etc/modules get over written ?

regards, 

scoon

---

### Post by pacz on 2005-07-12
Hello

Here's what seems to be the relavent portion of a "dmesg." I bolded the point where I enabled nvidia and where my ethernet device failed:

pacz@ubuntu:~$ dmesg
...
...
Probing IDE interface ide5...
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
hdb: ATAPI 52X DVD-ROM drive, 256kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Linux agpgart interface v0.100 (c) Dave Jones
**nvidia: module license 'NVIDIA' taints kernel.**
ACPI: PCI interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:04:00.0 to 64
**NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174**  Tue Mar 22 06:44:39 PST 2005
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
agpgart: Detected an Intel 915G Chipset.
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: AGP aperture is 256M @ 0x0
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
uhci_hcd 0000:00:1d.0: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 23, io base 0x8000
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1{B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0x8400
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0x8800
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.3: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 16, io base 0x9000
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xcacffc00
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
hw_random: RNG not detected
ICH6: IDE controller at PCI slot 0000:00:1f.1
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH6: chipset revision 5
ICH6: not 100% native mode: will probe irqs later
ICH6: port 0x01f0 already claimed by ide0
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide1...
Linux video capture interface: v1.00
saa7130/34: v4l2 driver version 0.2.12 loaded
ACPI: PCI interrupt 0000:01:09.0[A] -> GSI 17 (level, low) -> IRQ 17
saa7133[0]: found at 0000:01:09.0, rev: 240, irq: 17, latency: 64, mmio: 0xcadff800
saa7133[0]: subsystem: 1043:4845, board: UNKNOWN/GENERIC [card=0,autodetected]
saa7133[0]: board init: gpio is 0
saa7133[0]: dsp access wait timeout [bit=WRR]
saa7133[0]: dsp access wait timeout [bit=WRR]
saa7133[0]: i2c eeprom 00: 43 10 45 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
saa7133[0]: i2c eeprom 10: 00 ff e2 0f ff 20 ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 04 08 ff 00 89 ff ff ff ff
saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: registered device video0 [v4l2]
saa7133[0]: registered device vbi0
ACPI: PCI interrupt 0000:01:0a.0[A] -> GSI 21 (level, low) -> IRQ 21
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:02:00.0 to 64
[B]eth%d: -- ERROR --
        Class:  internal Software error
        Nr:  0x2bd
        Msg:  TWSI: transfer does not complete
sk98lin: SkGeInitAssignRamToQueues failed.[/B]
NET: Registered protocol family 17
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
Linux Tulip driver version 1.1.13 (May 11, 2002)

That last entry is because I swapped out my modem for an old Linksys NIC.  I read that all you had to do was a "sudo modprobe tulip" to get it to work, but Ubuntu still won't recognize either NIC, onboard or linksys.

---

### Post by pacz on 2005-07-12
I looked in /etc/modules.  Nvidia was listed there, but neither tulip nor sk98lin were.  I added them, rebooted, no change.

I also looked in /proc/net/sk98lin.  It's supposed to contain files like "eth0" and "eth1" but it has nothing.

Still no luck with tulip for the linksys NIC.

If I go buy another NIC out of desperation, which kind would work the best?

edit: I wiggled the linksys NIC.  Now it works.  hmm

---

### Post by scoon on 2005-07-14
Hey there, 

In the future, check out man lspci.  lspci should at the very least show you that the kernel recognises your card, even if the module is not loaded. 

regards, 

scoon

---

