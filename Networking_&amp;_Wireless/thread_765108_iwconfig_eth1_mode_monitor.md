---
title: "iwconfig eth1 mode monitor"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by Sub101 on 2008-04-24
This is my first post despite using ubuntu for some time.
I installed Hardy last nite and whilst playing around i changed the mode of my wireless to monitor. I can now see the networks but not connect to any of them?
  I have tried changing the mode to the other possibles like Ad-Hoc, Manages etc. but with no success? Any ideas?

---

### Post by Monicker on 2008-04-24
> **Sub101 said:**
> This is my first post despite using ubuntu for some time.
I installed Hardy last nite and whilst playing around i changed the mode of my wireless to monitor. I can now see the networks but not connect to any of them?
  I have tried changing the mode to the other possibles like Ad-Hoc, Manages etc. but with no success? Any ideas?

You can't connect to a wireless network while in monitor mode.  Its needs to be either Ad-Hoc or Managed.


Do you have that many 'networks" of your own, or are you trying to connect to other people's wireless networks without their permission?

---

### Post by Sub101 on 2008-04-24
I just have the one im trying to connect to i was trying to get across that i can see other network names so it isnt just a problem with my network. 
 And I have tried Ad-Hoc and managed wiht no effect? Ive just been experimenting trying to get to know the system better. Any other ideas?

---

### Post by Monicker on 2008-04-24
> **Sub101 said:**
> I just have the one im trying to connect to i was trying to get across that i can see other network names so it isnt just a problem with my network. 
 And I have tried Ad-Hoc and managed wiht no effect? Ive just been experimenting trying to get to know the system better. Any other ideas?

What happens when you try to go to Managed mode?  Are there errors?  What is the output of iwconfig?


What is the chipset of your wireless device, and what driver is it using?  Also supply the output of lspci -v

---

### Post by Sub101 on 2008-04-24
iwconfig gives

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and monitor mode still displays no networks at all.

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1840 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1860 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f4505c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at f4500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f2000000-f3ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f4000000-f40fffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: f4100000-f41fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1880 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 18a0 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18c0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at f4506000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
	Memory behind bridge: f4200000-f42fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1830 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 218
	I/O ports at 1c10 [size=8]
	I/O ports at 1c04 [size=4]
	I/O ports at 1c08 [size=8]
	I/O ports at 1c00 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f4505000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: medium devsel, IRQ 11
	Memory at 88000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, fast devsel, latency 0, IRQ 217
	Memory at f4000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 4000 [size=256]
	Capabilities: <access denied>

07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Compaq 6710b
	Flags: bus master, fast devsel, latency 0, IRQ 216
	Memory at f4100000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at f4200000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at f4200800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at f4200c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at f4201000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)

	!!! Unknown header type 7f
cheers for your help

---

### Post by Sub101 on 2008-04-24
iwconfig gives

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and monitor mode still displays no networks at all.

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1840 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1860 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f4505c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at f4500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f2000000-f3ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f4000000-f40fffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: f4100000-f41fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1880 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 18a0 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18c0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at f4506000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
	Memory behind bridge: f4200000-f42fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1830 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 218
	I/O ports at 1c10 [size=8]
	I/O ports at 1c04 [size=4]
	I/O ports at 1c08 [size=8]
	I/O ports at 1c00 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f4505000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: medium devsel, IRQ 11
	Memory at 88000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, fast devsel, latency 0, IRQ 217
	Memory at f4000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 4000 [size=256]
	Capabilities: <access denied>

07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Compaq 6710b
	Flags: bus master, fast devsel, latency 0, IRQ 216
	Memory at f4100000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at f4200000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at f4200800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cd
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at f4200c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>



08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)

	!!! Unknown header type 7f
cheers for your help

---

### Post by Monicker on 2008-04-24
Intel chipset for the wireless.  Those can be a pain, but the driver seems to be loaded.

Do the following:

iwconfig eth1 essid myssid

dhclient eth1


Note: the above assumes your home network is not encrypted.


Are you not running Network Manager?  It makes some of this easier than doing it all manually.

---

### Post by Sub101 on 2008-04-24
was encrypted so removed the encryption and gave it a go.
The problem was the channel had changed? So i ran;
sudo iwconfig eth1 mode Ad-Hoc channel

this seemed it sort the problem? Thankyou for all your help.

---

