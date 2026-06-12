---
title: "Help Wanted: Can not resolv domain name"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by anderson916 on 2005-07-27
Hi,

In my office's lan,I face a very strange problem:I could use "apt-get update "(archive.ubuntu.org.cn),but could not browse web sites in firefox.There is no proxy settings in firefox.And I could not ping to thoese domain name,but if using ip address, it works.I could ping to my default gateway.

And if I switch to windows xp,everything is ok.

The following is some output from my ubuntu 5.04:
route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.132.0.0      *               255.255.255.0   U     0      0        0 eth0
default         10.132.0.1      0.0.0.0         UG    0      0        0 eth0


dmesg:
SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 11, io base 0xbf80
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.1: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 11, io base 0xbf40
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.2: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 11, io base 0xbf20
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 3-2: new full speed USB device using uhci_hcd and address 2
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 11 (level, low) -> IRQ 11
ehci_hcd 0000:00:1d.7: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 11, pci mem 0xf4fffc00
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
hw_random: cannot enable RNG, aborting
usb 3-2: device not accepting address 2, error -71
usb 4-6: new high speed USB device using ehci_hcd and address 2
hub 4-6:1.0: USB hub found
hub 4-6:1.0: 4 ports detected
usb 4-6.4: new full speed USB device using ehci_hcd and address 3
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 5 (level, low) -> IRQ 5
PCI: Setting latency timer of device 0000:00:1f.5 to 64
hub 4-6.4:1.0: USB hub found
hub 4-6.4:1.0: 3 ports detected
usb 4-6.4.1: new full speed USB device using ehci_hcd and address 4
usb 4-6.4.3: new low speed USB device using ehci_hcd and address 5
usbcore: registered new driver hiddev
input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.7-6.4.1
input: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.7-6.4.1
input: USB HID v1.00 Mouse [USB Wheel Mouse] on usb-0000:00:1d.7-6.4.3
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
intel8x0_measure_ac97_clock: measured 96890 usecs
intel8x0: clocking to 48000
tg3.c:v3.14 (November 15, 2004)
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 11 (level, low) -> IRQ 11
eth0: Tigon3 [partno(BCM95702A20) rev 1002 PHY(5703)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0b:db:a4:d3:f7
eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
PCI: Enabling device 0000:02:01.0 (0000 -> 0002)
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 11 (level, low) -> IRQ 11
Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
Yenta O2: res at 0x94/0xD4: 00/ea
Yenta O2: enabling read prefetch/write burst
Yenta: ISA IRQ mask 0x0418, PCI irq 11
Socket status: 30000006
PCI: Enabling device 0000:02:01.1 (0000 -> 0002)
ACPI: PCI interrupt 0000:02:01.1[A] -> GSI 11 (level, low) -> IRQ 11
Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
Yenta: ISA IRQ mask 0x0418, PCI irq 11
Socket status: 30000410
tg3: eth0: Link is up at 100 Mbps, half duplex.
tg3: eth0: Flow control is off for TX and off for RX.
ACPI: AC Adapter [AC] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Battery Slot [BAT1] (battery absent)
ACPI: Lid Switch [LID]
ACPI: Power Button (CM) [PBTN]
ACPI: Sleep Button (CM) [SBTN]
ibm_acpi: ec object not found
ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
apm: BIOS not found.
[drm] Initialized drm 1.0.0 20040925
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 11 (level, low) -> IRQ 11
[drm] Initialized radeon 1.14.0 20050125 on minor 0: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9]
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[drm] Loading R200 Microcode
drivers/usb/input/hid-input.c: event field not found
drivers/usb/input/hid-input.c: event field not found
ip_tables: (C) 2000-2002 Netfilter core team
ip_conntrack version 2.1 (8189 buckets, 65512 max) - 336 bytes per conntrack
cs: IO port probe 0x0100-0x04ff: excluding 0x290-0x297
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
cs: memory probe 0xa0000000-0xa0ffffff: clean.
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0f:1f:87:a6:0b:08:00 SRC=10.132.0.101 DST=10.132.0.255 LEN=235 TOS=0x00 PREC=0x00 TTL=128 ID=29546 PROTO=UDP SPT=138 DPT=138 LEN=215 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:12:79:c1:2d:68:08:00 SRC=10.132.0.106 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=64 ID=59780 PROTO=UDP SPT=138 DPT=138 LEN=209 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:12:79:58:0b:74:08:00 SRC=10.132.0.109 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=27987 PROTO=UDP SPT=138 DPT=138 LEN=209 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:40:05:45:29:1d:08:00 SRC=10.132.0.142 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=64 ID=56253 PROTO=UDP SPT=138 DPT=138 LEN=209 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:06:5b:b7:25:87:08:00 SRC=10.132.0.113 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=56874 PROTO=UDP SPT=138 DPT=138 LEN=209 
Inbound IN=eth0 OUT= MAC=00:0b:db:a4:d3:f7:00:07:4f:40:20:09:08:00 SRC=10.132.3.2 DST=10.132.0.117 LEN=56 TOS=0x00 PREC=0xC0 TTL=254 ID=44833 PROTO=ICMP TYPE=11 CODE=0 [SRC=10.132.0.117 DST=202.108.9.16 LEN=38 TOS=0x00 PREC=0x00 TTL=1 ID=41156 PROTO=UDP SPT=41150 DPT=33440 LEN=18 ] 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0b:db:a3:d5:67:08:00 SRC=10.132.0.138 DST=10.132.0.255 LEN=234 TOS=0x00 PREC=0x00 TTL=128 ID=30629 PROTO=UDP SPT=138 DPT=138 LEN=214 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0f:1f:87:a6:0b:08:00 SRC=10.132.0.101 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=29688 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0f:1f:87:a6:0b:08:00 SRC=10.132.0.101 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=29690 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0f:1f:87:a6:0b:08:00 SRC=10.132.0.101 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=29691 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=15972 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=15973 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=15974 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=15976 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=15977 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=15978 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=15980 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=15981 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=15982 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=15983 PROTO=UDP SPT=138 DPT=138 LEN=209 
tg3: eth0: Link is up at 100 Mbps, half duplex.
tg3: eth0: Flow control is off for TX and off for RX.
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[drm] Loading R200 Microcode
tg3: eth0: Link is up at 100 Mbps, half duplex.
tg3: eth0: Flow control is off for TX and off for RX.
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0b:db:a3:d5:67:08:00 SRC=10.132.0.138 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=30694 PROTO=UDP SPT=138 DPT=138 LEN=209 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0b:db:a3:d5:67:08:00 SRC=10.132.0.138 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30696 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0b:db:a3:d5:67:08:00 SRC=10.132.0.138 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30698 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0b:db:a3:d5:67:08:00 SRC=10.132.0.138 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=30699 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=00:0b:db:a4:d3:f7:00:07:4f:40:20:09:08:00 SRC=10.132.3.2 DST=10.132.0.117 LEN=56 TOS=0x00 PREC=0xC0 TTL=254 ID=45175 PROTO=ICMP TYPE=11 CODE=0 [SRC=10.132.0.117 DST=216.148.48.73 LEN=38 TOS=0x00 PREC=0x00 TTL=1 ID=41441 PROTO=UDP SPT=41435 DPT=33440 LEN=18 ] 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0f:1f:87:a6:0b:08:00 SRC=10.132.0.101 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=30006 PROTO=UDP SPT=138 DPT=138 LEN=209 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:56:dd:19:e4:08:00 SRC=10.132.0.107 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=18120 PROTO=UDP SPT=138 DPT=138 LEN=209 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:56:28:7f:03:08:00 SRC=10.132.0.102 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=49928 PROTO=UDP SPT=138 DPT=138 LEN=209 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=15999 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16000 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16001 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16003 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16004 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16005 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16007 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16008 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16009 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16011 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16012 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16013 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16015 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16016 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:d0:b7:46:ee:c6:08:00 SRC=10.132.0.130 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=16017 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0f:1f:cf:0d:70:08:00 SRC=10.132.0.129 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=58542 PROTO=UDP SPT=138 DPT=138 LEN=209 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:56:76:eb:07:08:00 SRC=10.132.0.112 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=40566 PROTO=UDP SPT=138 DPT=138 LEN=209 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:12:79:bd:6b:86:08:00 SRC=10.132.0.103 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=62500 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:12:79:bd:6b:86:08:00 SRC=10.132.0.103 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=62648 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:12:79:bd:6b:86:08:00 SRC=10.132.0.103 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=62771 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:12:79:bd:6b:86:08:00 SRC=10.132.0.103 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=62858 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:12:79:bd:6b:86:08:00 SRC=10.132.0.103 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=62902 PROTO=UDP SPT=137 DPT=137 LEN=58 
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:12:79:bd:6b:86:08:00 SRC=10.132.0.103 DST=10.132.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=62928 PROTO=UDP SPT=137 DPT=137 LEN=58 
tg3: eth0: Link is up at 100 Mbps, half duplex.
tg3: eth0: Flow control is off for TX and off for RX.
Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:08:00:46:54:2b:9a:08:00 SRC=10.132.0.118 DST=10.132.0.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=35570 PROTO=UDP SPT=138 DPT=138 LEN=209 
NET: Registered protocol family 17
tg3: eth0: Link is up at 100 Mbps, half duplex.
tg3: eth0: Flow control is off for TX and off for RX.

---

### Post by anderson916 on 2005-07-27
Otherwise,

I could ping to the dns server,and could traceroute to any given domain name.

---

### Post by strikeforce on 2005-07-27
Is your network set to dhcp?  Just check that your getting dns addressing through to you.  If not setup through dhcp you might need to add dns servers to your /etc/resolv.conf file?


e.g.

nameserver 123.123.123.123

---

### Post by anderson916 on 2005-07-27
/etc/network/interfaces:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#	script grep
#	map eth0

iface eth0 inet dhcp
#address 10.132.0.117
#netmask 255.255.255.0
#gateway 10.132.0.1

auto eth0


ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:A4:D3:F7  
          inet addr:10.132.0.114  Bcast:10.132.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1984 (1.9 KiB)  TX bytes:3119 (3.0 KiB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

arp:
Address                  HWtype  HWaddress           Flags Mask            Iface
10.132.0.1               ether   00:07:4F:40:20:09   C                     eth0

---

### Post by strikeforce on 2005-07-27
Can you check your /etc/resolv.conf file?

---

### Post by anderson916 on 2005-07-27
Yes,I checked the /etc/resolv.conf.It is ok.

I could ping to the ip of name server.

---

### Post by gruepig on 2005-07-27
Try using the host or nslookup command.  First try 
'host ubuntuforums.org' (or 'host ubuntuforums.org <ip_of_nameserver>).  Does that work?  If you get an error, post it here.

Also try 'host archive.ubuntu.org.cn <ip_of_nameserver>'?  Does that work?  Other .cn hosts?  How about 'host ubuntuforums.org.' (note the dot at the end)?

Also, are the nameservers listed in /etc/resolv.conf on Ubuntu the same as the servers that Windows is using?

---

