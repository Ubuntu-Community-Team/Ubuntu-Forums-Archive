---
title: "no sound with hardy...please help me"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Wilferno on 2009-03-08
I'm new to ubuntu and i've been trying to get my sound to work for 2 months now.  I installed hardy 8.04 and haven't been able to get the sound working.

I have an emachines t2484 desktop.  I was trying to use the integrated sound card.

---

### Post by Brandon.Viking on 2009-03-08
I guess some information would be handy.

have you ran the mixer to ensure that the volume is on?
paste the output of lspci and lsmod to the thread, to see what card is on your system.

type in :
sudo lspci -v
and
sudo lsmod

copy the output and paste it into a new thread msg or edit the original with the updated info.

Regards,
Brandon.

---

### Post by markbuntu on 2009-03-09
Updated troubleshooting help is here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Wilferno on 2009-03-09
lspci:
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9016
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9016
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Memory at e7000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at d800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d400 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at e7080000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: e4000000-e6ffffff
	Prefetchable memory behind bridge: d8000000-dfffffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9016
	Flags: medium devsel, IRQ 9
	I/O ports at 0500 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Unknown device b309
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 17
	Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at e5000000 [disabled] [size=128K]
	Capabilities: <access denied>

01:01.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem (prog-if 00 [Generic])
	Subsystem: ARCHTEK TELECOM Corp Unknown device 9100
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at e6000000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c000 [size=256]
	Capabilities: <access denied>

01:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9016
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at c400 [size=256]
	Memory at e6001000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at e5020000 [disabled] [size=64K]
	Capabilities: <access denied>


lsmod:
Module                  Size  Used by
isofs                  36388  1 
udf                    88612  0 
ipv6                  267908  8 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
container               5632  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
evdev                  13056  3 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
serio_raw               7940  0 
psmouse                40336  0 
pcspkr                  4224  0 
nvidia               7825536  34 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
i2c_i810                5636  0 
button                  9232  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_algo_bit            7300  1 i2c_i810
intel_agp              25492  1 
i2c_core               24832  3 nvidia,i2c_i810,i2c_algo_bit
agpgart                34760  2 nvidia,intel_agp
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_piix               19588  3 
8139cp                 24704  0 
floppy                 59588  0 
ata_generic             8324  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
libata                159600  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


i've tryed loading the snd-intel8x0 module before with no success and when i use the alsamixer or amixer command i get error messages about not having a device to control

---

