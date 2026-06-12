---
title: "Traffic Drops"
date: 2022-07-19
forum: Networking &amp; Wireless
---

### Post by analogscott on 2022-07-19
I setup a new server system.    The box has 2 onboard NICS and i have a PCIe 4 port NIC card installed.    I setup xRDP on it.    When i connect to the machine via the LAN, the connection will drop after about 10 minutes, consistently.    The Webmin, RDP and pinging all drops when this problem kicks in.    i tried adjusting the SSH timeout but this didn't help.   If i reboot the machine, it all works for about 10 minutes then drops.

Has anybody got any hints on what's going on?

---

### Post by analogscott on 2022-07-19
For anybody that runs across this thread,

After looking closer, i discovered that it was breaking the connections when the OS would log off.   I had it set to not log off, but it was still doing it.    I never really found a solution.   Because it was a fresh installation and didn't require Ubuntu, I switched to MX Linux.    It's not having this same issue anymore.    MX Linux isn't disconnecting my network interfaces.   I've used Ubuntu a few times in the past for servers and it has work well until now.  Maybe there is something about the hardware that doesn't jive with Ubuntu, but all is well in MX.

---

### Post by TheFu on 2022-07-19
a)  Servers don't have GUIs.  ssh would be the only answer if you aren't sitting on the console directly.  Nobody does that in the real world, though some enterprises would only buy systems with remote console capabilities, usually for about $300 more than without it.  IPMI, iDRAC, RIBLO adapters have to be built-into the system. These are usually very weak with security.

b) On desktop installs, there are 2 different methods for setting up network - system-wide or per-user.  Typically, a laptop would be per-user so the user could control when connections are made, typically wifi.  The login/logout process can be configured to kill all user processes or not, but I suspect systemd (which MX Linux doesn't use) could have changed the default to help save batteries on desktops/laptops.

Throwing out an entire distro over a minor configuration issue isn't something I'd do, but I understand if others want to do that.  MX Linux isn't perfect any more than Ubuntu is. A few of my friends use MX Linux on very low-end systems.  One boot off a flash drive and the other is running a C2D system.  OTOH, considering that MX just released a new version after about 3 yrs of nothing, you may find in a year that patching and finding support for the distro is a reason to try a different Flavor of Ubuntu.  Or you may be happy.  I hope it works out for you.

---

### Post by praseodym on 2022-07-20
Chipsets?
```

lspci -nnk
```

---

### Post by analogscott on 2022-07-21
[COLOR=#000000]a) Servers can have GUI.   I've only run servers 5-10 times over the years but never had any major issues with the GUI.    [/COLOR]

[COLOR=#000000]b) It was a server install with the GUI added.    The computer is a dual processor Xeon of some sort (don't remember off the top of my head).    I got the impression that maybe it defaulted to killing the processes on login/logout, but i really can't be sure.   I didn't set it that way.  MX Linux does have systemd as an option but defaults to sysVinit.  I switched the system to systemd and it was an easy and a smooth process. [/COLOR]

[COLOR=#000000]Throwing out the distro wasn't my first choice, but to me a minor choice.   It was a fresh install and other distros could serve the purpose well.    I spent too much time trying to figure out why it kept disconnecting on me.  It was probably something i was ignorant to, but i wore out my experience and google trying to figure it out.   MX Linux is new to me, but the install and base configurations went smooth.   So far i like it.    Ubuntu has treated me well over the years, no real complaints.    At my current job i've run an Ubuntu file server as a virtual machine for 5 years or so and it's been rock solid.    [/COLOR]

[COLOR=#000000]I'll have to experiment with running MX off a flash drive.   

I've used Linux in virtual machines as file servers and webservers for 10+years.   Linux has really impressed me as i slowly learn it.     I've used Windows since 95.   When Windows 8 came out i told myself i was switching to Linux at home.  It didn't happen.   I did the same thing with Windows 10.   Now with Windows 11 i swear i'm gonna switch, lol.   There is a bunch of software i have to find Linux versions for.    I'll get there eventually.

[/COLOR]So far with MX it's been good.    I really appreciate your reply and expertise.

---

### Post by analogscott on 2022-07-21
Even though i'm probably not going to switch back from MX Linux (for this project), for future people researching a similar issue,

As for chipsets,

praseodym, Thank you for your help,

```
lspci -nnk00:00.0 Host bridge [0600]: Intel Corporation Xeon E5/Core i7 DMI2 [8086:3c00] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMI2 [8086:3586]
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 1a [8086:3c02] (rev 07)
	Kernel driver in use: pcieport
00:01.1 PCI bridge [0604]: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 1b [8086:3c03] (rev 07)
	Kernel driver in use: pcieport
00:03.0 PCI bridge [0604]: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 3a in PCI Express Mode [8086:3c08] (rev 07)
	Kernel driver in use: pcieport
00:04.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 0 [8086:3c20] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 0 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
00:04.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 1 [8086:3c21] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 1 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
00:04.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 2 [8086:3c22] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 2 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
00:04.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 3 [8086:3c23] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 3 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
00:04.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 4 [8086:3c24] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 4 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
00:04.5 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 5 [8086:3c25] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 5 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
00:04.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 6 [8086:3c26] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 6 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
00:04.7 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 7 [8086:3c27] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 7 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
00:05.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Address Map, VTd_Misc, System Management [8086:3c28] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Address Map, VTd_Misc, System Management [8086:3586]
00:05.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Control Status and Global Errors [8086:3c2a] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Control Status and Global Errors [8086:3586]
00:05.4 PIC [0800]: Intel Corporation Xeon E5/Core i7 I/O APIC [8086:3c2c] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 I/O APIC [8086:3586]
00:11.0 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Virtual Root Port [8086:1d3e] (rev 06)
	Kernel driver in use: pcieport
00:16.0 Communication controller [0780]: Intel Corporation C600/X79 series chipset MEI Controller #1 [8086:1d3a] (rev 05)
	Subsystem: Intel Corporation C600/X79 series chipset MEI Controller [8086:3586]
	Kernel modules: mei_me
00:16.1 Communication controller [0780]: Intel Corporation C600/X79 series chipset MEI Controller #2 [8086:1d3b] (rev 05)
	Subsystem: Intel Corporation C600/X79 series chipset MEI Controller [8086:3586]
00:1a.0 USB controller [0c03]: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #2 [8086:1d2d] (rev 06)
	Subsystem: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller [8086:3586]
	Kernel driver in use: ehci-pci
	Kernel modules: ehci_pci
00:1c.0 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 1 [8086:1d10] (rev b6)
	Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 2 [8086:1d12] (rev b6)
	Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 3 [8086:1d14] (rev b6)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #1 [8086:1d26] (rev 06)
	Subsystem: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller [8086:3586]
	Kernel driver in use: ehci-pci
	Kernel modules: ehci_pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation C600/X79 series chipset LPC Controller [8086:1d41] (rev 06)
	Subsystem: Intel Corporation C600/X79 series chipset LPC Controller [8086:3586]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation C600/X79 series chipset 6-Port SATA AHCI Controller [8086:1d02] (rev 06)
	DeviceName: PCH Integrated SATA Controller
	Subsystem: Intel Corporation C600/X79 series chipset 6-Port SATA AHCI Controller [8086:3586]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation C600/X79 series chipset SMBus Host Controller [8086:1d22] (rev 06)
	Subsystem: Intel Corporation C600/X79 series chipset SMBus Host Controller [8086:3586]
	Kernel driver in use: i801_smbus
	Kernel modules: i2c_i801
02:00.0 PCI bridge [0604]: Microsemi / PMC / IDT PES12N3A 12-lane 3-Port PCI Express Switch [111d:8018] (rev 0e)
	Kernel driver in use: pcieport
03:02.0 PCI bridge [0604]: Microsemi / PMC / IDT PES12N3A 12-lane 3-Port PCI Express Switch [111d:8018] (rev 0e)
	Kernel driver in use: pcieport
03:04.0 PCI bridge [0604]: Microsemi / PMC / IDT PES12N3A 12-lane 3-Port PCI Express Switch [111d:8018] (rev 0e)
	Kernel driver in use: pcieport
04:00.0 Ethernet controller [0200]: Intel Corporation 82571EB/82571GB Gigabit Ethernet Controller (Copper) [8086:10bc] (rev 06)
	Subsystem: Hewlett-Packard Company NC364T PCI Express Quad Port Gigabit Server Adapter [103c:704b]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
04:00.1 Ethernet controller [0200]: Intel Corporation 82571EB/82571GB Gigabit Ethernet Controller (Copper) [8086:10bc] (rev 06)
	Subsystem: Hewlett-Packard Company NC364T PCI Express Quad Port Gigabit Server Adapter [103c:704b]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
05:00.0 Ethernet controller [0200]: Intel Corporation 82571EB/82571GB Gigabit Ethernet Controller (Copper) [8086:10bc] (rev 06)
	Subsystem: Hewlett-Packard Company NC364T PCI Express Quad Port Gigabit Server Adapter [103c:704b]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
05:00.1 Ethernet controller [0200]: Intel Corporation 82571EB/82571GB Gigabit Ethernet Controller (Copper) [8086:10bc] (rev 06)
	Subsystem: Hewlett-Packard Company NC364T PCI Express Quad Port Gigabit Server Adapter [103c:704b]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
07:00.0 Serial Attached SCSI controller [0107]: Intel Corporation C602 chipset 4-Port SATA Storage Control Unit [8086:1d6b] (rev 06)
	DeviceName: SCU
	Subsystem: Intel Corporation C602 chipset 4-Port SATA Storage Control Unit [8086:3587]
	Kernel driver in use: isci
	Kernel modules: isci
07:00.3 SMBus [0c05]: Intel Corporation C600/X79 series chipset SMBus Controller 0 [8086:1d70] (rev 06)
	Subsystem: Intel Corporation C600/X79 series chipset SMBus Controller 0 [8086:3586]
	Kernel driver in use: i801_smbus
	Kernel modules: i2c_i801
08:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
	DeviceName: Intel 82574L
	Subsystem: Intel Corporation 82574L Gigabit Network Connection [8086:3586]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
09:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
	DeviceName: Intel 82574L
	Subsystem: Intel Corporation 82574L Gigabit Network Connection [8086:3586]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
0a:00.0 VGA compatible controller [0300]: Matrox Electronics Systems Ltd. MGA G200e [Pilot] ServerEngines (SEP1) [102b:0522] (rev 05)
	DeviceName: ServerEngines Pilot III
	Subsystem: Intel Corporation MGA G200e [Pilot] ServerEngines (SEP1) [8086:0103]
	Kernel driver in use: mgag200
	Kernel modules: mgag200
7f:08.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link 0 [8086:3c80] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 QPI Link 0 [8086:3586]
7f:09.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link 1 [8086:3c90] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 QPI Link 1 [8086:3586]
7f:0a.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 0 [8086:3cc0] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Power Control Unit 0 [8086:3586]
7f:0a.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 1 [8086:3cc1] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Power Control Unit 1 [8086:0000]
7f:0a.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 2 [8086:3cc2] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Power Control Unit 2 [8086:3586]
7f:0a.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 3 [8086:3cd0] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Power Control Unit 3 [8086:3586]
7f:0b.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Interrupt Control Registers [8086:3ce0] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Interrupt Control Registers [8086:3586]
7f:0b.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Semaphore and Scratchpad Configuration Registers [8086:3ce3] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Semaphore and Scratchpad Configuration Registers [8086:3586]
7f:0c.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3586]
7f:0c.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3586]
7f:0c.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 0 [8086:3cf4] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 0 [8086:3586]
7f:0c.7 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 System Address Decoder [8086:3cf6] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 System Address Decoder [8086:3586]
7f:0d.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3586]
7f:0d.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3586]
7f:0d.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 1 [8086:3cf5] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 1 [8086:3586]
7f:0e.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Processor Home Agent [8086:3ca0] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Processor Home Agent [8086:3586]
7f:0e.1 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Processor Home Agent Performance Monitoring [8086:3c46] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Processor Home Agent Performance Monitoring [8086:3586]
	Kernel driver in use: snbep_uncore
7f:0f.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Registers [8086:3ca8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Registers [8086:3586]
7f:0f.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller RAS Registers [8086:3c71] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller RAS Registers [8086:3586]
7f:0f.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 0 [8086:3caa] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 0 [8086:3586]
7f:0f.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 1 [8086:3cab] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 1 [8086:3586]
7f:0f.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 2 [8086:3cac] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 2 [8086:3586]
7f:0f.5 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 3 [8086:3cad] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 3 [8086:3586]
7f:0f.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 4 [8086:3cae] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 4 [8086:0000]
7f:10.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 0 [8086:3cb0] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 0 [8086:3586]
	Kernel driver in use: snbep_uncore
7f:10.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 1 [8086:3cb1] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 1 [8086:3586]
	Kernel driver in use: snbep_uncore
7f:10.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 0 [8086:3cb2] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 0 [8086:3586]
7f:10.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 1 [8086:3cb3] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 1 [8086:3586]
7f:10.5 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 3 [8086:3cb5] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 3 [8086:3586]
	Kernel driver in use: snbep_uncore
7f:10.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 2 [8086:3cb6] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 2 [8086:3586]
7f:10.7 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 3 [8086:3cb7] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 3 [8086:3586]
7f:11.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DDRIO [8086:3cb8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DDRIO [8086:0000]
7f:13.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 R2PCIe [8086:3ce4] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 R2PCIe [8086:3586]
7f:13.1 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Ring to PCI Express Performance Monitor [8086:3c43] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Ring to PCI Express Performance Monitor [8086:3586]
	Kernel driver in use: snbep_uncore
7f:13.4 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 QuickPath Interconnect Agent Ring Registers [8086:3ce6] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 QuickPath Interconnect Agent Ring Registers [8086:3586]
7f:13.5 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 0 Performance Monitor [8086:3c44] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 0 Performance Monitor [8086:3586]
	Kernel driver in use: snbep_uncore
7f:13.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 1 Performance Monitor [8086:3c45] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 1 Performance Monitor [8086:3586]
	Kernel driver in use: snbep_uncore
80:03.0 PCI bridge [0604]: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 3a in PCI Express Mode [8086:3c08] (rev 07)
	Kernel driver in use: pcieport
80:04.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 0 [8086:3c20] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 0 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
80:04.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 1 [8086:3c21] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 1 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
80:04.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 2 [8086:3c22] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 2 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
80:04.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 3 [8086:3c23] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 3 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
80:04.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 4 [8086:3c24] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 4 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
80:04.5 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 5 [8086:3c25] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 5 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
80:04.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 6 [8086:3c26] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 6 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
80:04.7 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DMA Channel 7 [8086:3c27] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DMA Channel 7 [8086:3586]
	Kernel driver in use: ioatdma
	Kernel modules: ioatdma
80:05.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Address Map, VTd_Misc, System Management [8086:3c28] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Address Map, VTd_Misc, System Management [8086:3586]
80:05.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Control Status and Global Errors [8086:3c2a] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Control Status and Global Errors [8086:3586]
80:05.4 PIC [0800]: Intel Corporation Xeon E5/Core i7 I/O APIC [8086:3c2c] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 I/O APIC [8086:3586]
ff:08.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link 0 [8086:3c80] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 QPI Link 0 [8086:3586]
ff:09.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link 1 [8086:3c90] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 QPI Link 1 [8086:3586]
ff:0a.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 0 [8086:3cc0] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Power Control Unit 0 [8086:3586]
ff:0a.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 1 [8086:3cc1] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Power Control Unit 1 [8086:0000]
ff:0a.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 2 [8086:3cc2] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Power Control Unit 2 [8086:3586]
ff:0a.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 3 [8086:3cd0] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Power Control Unit 3 [8086:3586]
ff:0b.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Interrupt Control Registers [8086:3ce0] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Interrupt Control Registers [8086:3586]
ff:0b.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Semaphore and Scratchpad Configuration Registers [8086:3ce3] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Semaphore and Scratchpad Configuration Registers [8086:3586]
ff:0c.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3586]
ff:0c.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3586]
ff:0c.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 0 [8086:3cf4] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 0 [8086:3586]
ff:0c.7 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 System Address Decoder [8086:3cf6] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 System Address Decoder [8086:3586]
ff:0d.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3586]
ff:0d.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3586]
ff:0d.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 1 [8086:3cf5] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 1 [8086:3586]
ff:0e.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Processor Home Agent [8086:3ca0] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Processor Home Agent [8086:3586]
ff:0e.1 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Processor Home Agent Performance Monitoring [8086:3c46] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Processor Home Agent Performance Monitoring [8086:3586]
	Kernel driver in use: snbep_uncore
ff:0f.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Registers [8086:3ca8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Registers [8086:3586]
ff:0f.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller RAS Registers [8086:3c71] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller RAS Registers [8086:3586]
ff:0f.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 0 [8086:3caa] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 0 [8086:3586]
ff:0f.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 1 [8086:3cab] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 1 [8086:3586]
ff:0f.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 2 [8086:3cac] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 2 [8086:3586]
ff:0f.5 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 3 [8086:3cad] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 3 [8086:3586]
ff:0f.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 4 [8086:3cae] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 4 [8086:0000]
ff:10.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 0 [8086:3cb0] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 0 [8086:3586]
	Kernel driver in use: snbep_uncore
ff:10.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 1 [8086:3cb1] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 1 [8086:3586]
	Kernel driver in use: snbep_uncore
ff:10.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 0 [8086:3cb2] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 0 [8086:3586]
ff:10.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 1 [8086:3cb3] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 1 [8086:3586]
ff:10.5 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 3 [8086:3cb5] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 3 [8086:3586]
	Kernel driver in use: snbep_uncore
ff:10.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 2 [8086:3cb6] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 2 [8086:3586]
ff:10.7 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 3 [8086:3cb7] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 3 [8086:3586]
ff:11.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DDRIO [8086:3cb8] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 DDRIO [8086:0000]
ff:13.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 R2PCIe [8086:3ce4] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 R2PCIe [8086:3586]
ff:13.1 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Ring to PCI Express Performance Monitor [8086:3c43] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Ring to PCI Express Performance Monitor [8086:3586]
	Kernel driver in use: snbep_uncore
ff:13.4 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 QuickPath Interconnect Agent Ring Registers [8086:3ce6] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 QuickPath Interconnect Agent Ring Registers [8086:3586]
ff:13.5 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 0 Performance Monitor [8086:3c44] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 0 Performance Monitor [8086:3586]
	Kernel driver in use: snbep_uncore
ff:13.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 1 Performance Monitor [8086:3c45] (rev 07)
	Subsystem: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 1 Performance Monitor [8086:3586]
	Kernel driver in use: snbep_uncore
```

---

### Post by TheFu on 2022-07-22
> **analogscott said:**
> [COLOR=#000000]a) Servers can have GUI.   I've only run servers 5-10 times over the years but never had any major issues with the GUI.    [/COLOR]
 

There are lots of things that **are** possible, but that doesn't make them a good idea.  I have a suspicion that adding the GUI is what changed the behavior to disconnect-on-logout, but I don't have any proof and I've not seen it myself.  My servers don't have GUIs.

Google found this - Ubuntu-Mate DE - [https://ubuntu-mate.community/t/stop-network-disconnecting-in-ubuntu/829](https://ubuntu-mate.community/t/stop-network-disconnecting-in-ubuntu/829)  Seems related to wifi.
 Other google results found other answers for different DEs. Basically, it is a network setting that treats the system as a single-user laptop or as a multi-user server that isn't behaving in the desired way.

---

