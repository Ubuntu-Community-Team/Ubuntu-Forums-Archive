---
title: "wireless problem: can't load wlan0 with ndiswrapper"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by robli99 on 2006-11-10
I am using a SMC ez-connected 2862w USB2 wireless adapter, have to use ndiswrapper.
I used the ndiswrapper inside Dapper, the windows driver is loaded successfully

ljz@ljz-desktop:~$ sudo ndiswrapper -l
Installed ndis drivers:
2862w           driver present, hardware present

When I run sudo modprode ndiswrapper the first after installed the driver, the light of the adapter was on for a while, and I can use the Networking to configure wlan0. 

My /etc/network/interfaces is:
------------
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid SMC
wireless-key xxxxxxxxxx
--------------------

The file /etc/modprobe.d/ndiswrapper contains:
alias wlan0 ndiswrapper


When I run iwconfig, I don't find wlan0

In Systems/Admin/Networking, the wireless interface is eth1, sometimes is sit0. 

I installed the driver step by step following the instruction in the forum.
Can anybody give some instruction how to load the wlan0?

---

### Post by robli99 on 2006-11-11
Anyone can give some instructions? it is a SMC 2862w usb adapter.
Following are some additional informations:


ljz@ljz-desktop:~$ sudo ndiswrapper -l
Installed ndis drivers:
2862w           driver present, hardware present

ljz@ljz-desktop:~$ sudo lsusb
Bus 005 Device 002: ID 0707:ee06 Standard Microsystems Corp. EZ-Connect 802.11g Adapter
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 003: ID 1241:1166 Belkin
Bus 004 Device 002: ID 0603:00f2 Novatek Microelectronics Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

ljz@ljz-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:F4:BE:5F
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fef4:be5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1364457 (1.3 MiB)  TX bytes:148903 (145.4 KiB)
          Interrupt:217 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

ljz@ljz-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:off/any
          Mode:Auto  Channel=0  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


ljz@ljz-desktop:~$ sudo ifup wlan0
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

I don't know why it always tell me 'no such device'.

---

### Post by bjd on 2006-11-11
your wireless device is called eth1 not wlan0..

---

### Post by robli99 on 2006-11-12
but in the file /etc/modprobe.d/ndiswrapper, the ndiswrapper is defined with alias wlan0:
============= /etc/modprobe.d/ndiswrapper=============
alias wlan0 ndiswrapper
======================================================
And in the file /etc/network/interfaces wlan0 is also defined:

=========================interfaces============
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid SMC
wireless-key aaaaabbbbb

auto eth0
===========================

Does it mean Ubuntu has another driver for my usb adapater and it is used as the interface of eth1? If yes, how can I disable the driver in Ubuntu?
Thanks!

---

### Post by bjd on 2006-11-12
that's possible.. from a quick google it looks like this is a prism54 device with unsupported firmware. 
USB prism54 devices seem to use the *islsm* module... so you'd need to add *blacklist islsm* and maybe also *blacklist islsm_device* and * blacklist islsm_usb* to /etc/modprobe.d/blacklist and then restart.
Or post the output of lsmod if that doesn't work..

---

### Post by robli99 on 2006-11-12
Thanks
I have added islsm, islsm_device, islsm_usb to the blacklist and restarted the system. I still don't see wlan0 by iwconfig.
===========iwconfig============
ljz@ljz-desktop:~$ sudo modprobe ndiswrapper
ljz@ljz-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
====================================
===========lsmod============================
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  1
drm                    73236  2 radeon
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
nls_utf8                2176  2
ntfs                  103536  2
ipv6                  265728  6
af_packet              22920  2
dm_mod                 58936  1
md_mod                 72532  0
ndiswrapper           177364  0
sbp2                   24196  0
lp                     11844  0
tsdev                   8000  0
r1000                  16000  0
parport_pc             35780  1
r8169                  28808  0
usbhid                 39904  0
parport                36296  3 ppdev,lp,parport_pc
floppy                 62148  0
psmouse                36100  0
pcspkr                  2180  0
serio_raw               7300  0
rtc                    13492  0
usb_storage            74304  1
snd_hda_intel          18964  1
snd_hda_codec         157616  1 snd_hda_intel
intel_agp              22940  1
agpgart                34888  2 drm,intel_agp
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
hw_random               5652  0
sr_mod                 16932  0
sg                     37920  0
cdrom                  38560  1 sr_mod
evdev                   9856  3
ext3                  135816  3
jbd                    58772  1 ext3
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  6 ndiswrapper,usbhid,usb_storage,ehci_hcd,uhci_hcdsd_mod                 19984  9
generic                 5124  0
ata_piix               11012  12
libata                 78992  1 ata_piix
scsi_mod              139496  6 sbp2,usb_storage,sr_mod,sg,sd_mod,libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
==================================================

---

### Post by bjd on 2006-11-12
does *dmesg* give any messages about ndiswrapper or wlan0?

---

### Post by FrodoB on 2006-11-12
Publish the section in dmesg where this driver is loaded. It it likely a firmware not present issue.

Have you looked at the device on the ndiswrapper site:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#S](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#S)

---

### Post by robli99 on 2006-11-12
Yes, I have checked the device list in ndiswrapper website. My usb adapter is there. And ndiswrapper -l also show up the driver presented.
This usb adapter works well on FC5 with ndiswrapper.
Following the the dmesg and ndiswrapper -l result.
Thanks all for the instructions.

=============dmesg============================
ljz@ljz-desktop:~$ sudo dmesg
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000d0000000 - 00000000e0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5020
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f69e0
[17179569.184000] ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff3040
[17179569.184000] ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff30c0
[17179569.184000] ACPI: MCFG (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff6d00
[17179569.184000] ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x3fff6c40
[17179569.184000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:90000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda9 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2793.545 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.176000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.176000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179573.200000] Memory: 1028816k/1048512k available (1976k kernel code, 18936k reserved, 606k data, 288k init, 131008k highmem)
[17179573.200000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.280000] Calibrating delay using timer specific routine.. 5593.13 BogoMIPS (lpj=11186262)
[17179573.280000] Security Framework v1.0.0 initialized
[17179573.280000] SELinux:  Disabled at boot.
[17179573.280000] Mount-cache hash table entries: 512
[17179573.280000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000000
[17179573.280000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000000
[17179573.280000] monitor/mwait feature present.
[17179573.280000] using mwait in idle threads.
[17179573.280000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179573.280000] CPU: L2 cache: 1024K
[17179573.280000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000080 0000651d 00000000 00000000
[17179573.280000] mtrr: v2.0 (20020519)
[17179573.280000] CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 01
[17179573.280000] Enabling fast FPU save and restore... done.
[17179573.280000] Enabling unmasked SIMD FPU exception support... done.
[17179573.280000] Checking 'hlt' instruction... OK.
[17179573.296000] checking if image is initramfs... it is
[17179573.840000] Freeing initrd memory: 6616k freed
[17179573.852000] ACPI: Looking for DSDT ... not found!
[17179573.856000] ENABLING IO-APIC IRQs
[17179573.856000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179574.000000] NET: Registered protocol family 16
[17179574.000000] EISA bus registered
[17179574.000000] ACPI: bus type pci registered
[17179574.000000] PCI: PCI BIOS revision 3.00 entry at 0xfaf60, last bus=2
[17179574.000000] PCI: Using MMCONFIG
[17179574.004000] ACPI: Subsystem revision 20051216
[17179574.008000] ACPI: Interpreter enabled
[17179574.008000] ACPI: Using IOAPIC for interrupt routing
[17179574.008000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.008000] PCI: Probing PCI hardware (bus 00)
[17179574.012000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179574.012000] Boot video device is 0000:01:00.0
[17179574.012000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.012000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.024000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179574.028000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179574.028000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179574.028000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179574.028000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179574.028000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179574.028000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179574.028000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179574.028000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179574.028000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.028000] pnp: PnP ACPI init
[17179574.032000] pnp: PnP ACPI: found 13 devices
[17179574.032000] PnPBIOS: Disabled by ACPI PNP
[17179574.032000] PCI: Using ACPI for IRQ routing
[17179574.032000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.052000] pnp: 00:09: ioport range 0x400-0x4bf could not be reserved
[17179574.056000] PCI: Bridge: 0000:00:01.0
[17179574.056000]   IO window: 9000-9fff
[17179574.056000]   MEM window: e8000000-e9ffffff
[17179574.056000]   PREFETCH window: e0000000-e7ffffff
[17179574.056000] PCI: Bridge: 0000:00:1e.0
[17179574.056000]   IO window: a000-afff
[17179574.056000]   MEM window: ea000000-ebffffff
[17179574.056000]   PREFETCH window: 50000000-500fffff
[17179574.056000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.056000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179574.056000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.056000] audit: initializing netlink socket (disabled)
[17179574.056000] audit(1163365862.056:1): initialized
[17179574.056000] highmem bounce pool size: 64 pages
[17179574.056000] VFS: Disk quotas dquot_6.5.1
[17179574.056000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.056000] Initializing Cryptographic API
[17179574.056000] io scheduler noop registered
[17179574.056000] io scheduler anticipatory registered
[17179574.056000] io scheduler deadline registered
[17179574.056000] io scheduler cfq registered
[17179574.056000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.056000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179574.056000] assign_interrupt_mode Found MSI capability
[17179574.056000] Allocate Port Service[pcie00]
[17179574.056000] Allocate Port Service[pcie03]
[17179574.056000] isapnp: Scanning for PnP cards...
[17179574.408000] isapnp: No Plug & Play device found
[17179574.424000] PNP: No PS/2 controller found. Probing ports directly.
[17179574.436000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.436000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.436000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.436000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.436000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.440000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.440000] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.440000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.440000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.440000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.440000] mice: PS/2 mouse device common for all mice
[17179574.444000] EISA: Probing bus 0 at eisa.0
[17179574.444000] EISA: Detected 0 cards.
[17179574.444000] NET: Registered protocol family 2
[17179575.092000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.104000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179575.104000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179575.104000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179575.104000] TCP: Hash tables configured (established 262144 bind 65536)
[17179575.104000] TCP reno registered
[17179575.104000] TCP bic registered
[17179575.104000] NET: Registered protocol family 1
[17179575.104000] NET: Registered protocol family 8
[17179575.104000] NET: Registered protocol family 20
[17179575.104000] Using IPI Shortcut mode
[17179575.104000] ACPI wakeup devices:
[17179575.104000] PCI0 PEX0 PEX1 PEX2 PEX3 HUB0 USB2 USB3 USBE AC97 MC97 AZAL
[17179575.104000] ACPI: (supports S0 S3 S4 S5)
[17179575.104000] Freeing unused kernel memory: 288k freed
[17179575.148000] vga16fb: initializing
[17179575.148000] vga16fb: mapped to 0xc00a0000
[17179575.272000] Console: switching to colour frame buffer device 80x25
[17179575.272000] fb0: VGA16 VGA frame buffer device
[17179576.336000] Capability LSM initialized
[17179576.492000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179577.020000] SCSI subsystem initialized
[17179577.020000] ACPI: bus type scsi registered
[17179577.020000] libata version 1.20 loaded.
[17179577.024000] ata_piix 0000:00:1f.2: version 1.05
[17179577.024000] ata_pci_init_one: pci_dev class+intf: 0x10180
[17179577.024000] ata_pci_init_one: NO_LEGACY == 0
[17179577.024000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 193
[17179577.024000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179577.024000] ata1: PATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xF000 irq 14
[17179577.188000] ata1: dev 0 cfg 00:0040 49:2f00 82:7c6b 83:5b09 84:4673 85:7c68 86:1a21 87:4663 88:207f 93:0000
[17179577.188000] ata1: dev 0 ATA-7, max UDMA/133, 160084415 sectors: LBA
[17179577.188000] ata_acpi_push_id: skipping for PATA mode
[17179577.188000] ata1: dev 0 configured for UDMA/133
[17179577.188000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179577.188000] pata_get_dev_handle: dev_handle: 0xdffe8f40, parent_handle: 0xdf96e4a0
[17179577.188000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff75a00, *handle=0xdffe8f40
[17179577.188000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdffe8cc0
[17179577.192000] scsi0 : ata_piix
[17179577.192000]   Vendor: ATA       Model: Maxtor 6L080M0    Rev: BACE
[17179577.192000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179577.192000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179577.192000] pata_get_dev_handle: dev_handle: 0xdffe8f40, parent_handle: 0xdf96e4a0
[17179577.192000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff75a00, *handle=0xdffe8f40
[17179577.192000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xF008 irq 15
[17179577.512000] ata2: dev 0 cfg 00:85c0 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:041f 93:4049
[17179577.512000] ata2: dev 0 ATAPI, max UDMA/66
[17179577.512000] ata2(0): applying bridge limits
[17179577.512000] ata_acpi_push_id: skipping for PATA mode
[17179577.512000] ata2: dev 0 configured for UDMA/66
[17179577.512000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179577.512000] pata_get_dev_handle: dev_handle: 0xdffe8f40, parent_handle: 0xdf96e4a0
[17179577.512000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff75a00, *handle=0xdffe8f40
[17179577.512000] do_drive_get_GTF:   drive w/ adr=0: v: 0xdffe8b40
[17179577.516000] scsi1 : ata_piix
[17179577.516000]   Vendor: BENQ      Model: DVD DC DW1670     Rev: 101
[17179577.516000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179577.516000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
[17179577.516000] pata_get_dev_handle: dev_handle: 0xdffe8f40, parent_handle: 0xdf96e4a0
[17179577.516000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff75a00, *handle=0xdffe8f40
[17179577.524000] Driver 'sd' needs updating - please use bus_type methods
[17179577.528000] SCSI device sda: 160084415 512-byte hdwr sectors (81963 MB)
[17179577.532000] SCSI device sda: drive cache: write back
[17179577.536000] SCSI device sda: 160084415 512-byte hdwr sectors (81963 MB)
[17179577.540000] SCSI device sda: drive cache: write back
[17179577.540000]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[17179577.620000] sd 0:0:0:0: Attached scsi disk sda
[17179577.940000] usbcore: registered new driver usbfs
[17179577.940000] usbcore: registered new driver hub
[17179577.940000] USB Universal Host Controller Interface driver v2.3
[17179577.940000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 201
[17179577.940000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.940000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.940000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.940000] uhci_hcd 0000:00:1d.0: irq 201, io base 0x0000bc00
[17179577.944000] hub 1-0:1.0: USB hub found
[17179577.944000] hub 1-0:1.0: 2 ports detected
[17179578.008000] ieee1394: Initialized config rom entry `ip1394'
[17179578.048000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179578.048000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179578.048000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179578.048000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179578.048000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000b000
[17179578.048000] hub 2-0:1.0: USB hub found
[17179578.048000] hub 2-0:1.0: 2 ports detected
[17179578.152000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[17179578.152000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179578.152000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179578.152000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179578.152000] uhci_hcd 0000:00:1d.2: irq 209, io base 0x0000b400
[17179578.152000] hub 3-0:1.0: USB hub found
[17179578.152000] hub 3-0:1.0: 2 ports detected
[17179578.256000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179578.256000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179578.256000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179578.256000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179578.256000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000b800
[17179578.256000] hub 4-0:1.0: USB hub found
[17179578.256000] hub 4-0:1.0: 2 ports detected
[17179578.360000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 201
[17179578.360000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179578.360000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179578.360000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179578.360000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179578.360000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xec004000
[17179578.364000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.364000] hub 5-0:1.0: USB hub found
[17179578.364000] hub 5-0:1.0: 8 ports detected
[17179578.468000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179578.468000] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 23 (level, low) -> IRQ 201
[17179578.516000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[201]  MMIO=[eb004000-eb0047ff]  Max Packet=[2048]
[17179578.540000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179578.540000] ide0: ports already in use, skipping probe
[17179578.540000] ide1: I/O resource 0x170-0x177 not free.
[17179578.540000] ide1: ports already in use, skipping probe
[17179578.572000] Attempting manual resume
[17179578.596000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.612000] kjournald starting.  Commit interval 5 seconds
[17179579.008000] usb 5-6: new high speed USB device using ehci_hcd and address 2
[17179579.748000] usb 4-1: new low speed USB device using uhci_hcd and address 2[17179579.788000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea0000f5241f]
[17179580.164000] usb 4-2: new low speed USB device using uhci_hcd and address 3[17179585.744000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179585.744000]  1:0:0:0: Attached scsi generic sg1 type 5
[17179585.852000] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[17179585.852000] Uniform CD-ROM driver Revision: 3.20
[17179585.852000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179586.468000] hw_random hardware driver 1.0.0 loaded
[17179586.492000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.496000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.736000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.744000] agpgart: Detected an Intel 915G Chipset.
[17179586.764000] agpgart: AGP aperture is 256M @ 0x0
[17179586.768000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179586.768000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179587.072000] Initializing USB Mass Storage driver...
[17179587.072000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179587.072000] usb-storage: device found at 2
[17179587.072000] usb-storage: waiting for device to settle before scanning
[17179587.072000] usbcore: registered new driver usb-storage
[17179587.072000] USB Mass Storage support registered.
[17179587.084000] Real Time Clock Driver v1.12
[17179587.100000] input: PC Speaker as /class/input/input1
[17179587.112000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[17179587.152000] Floppy drive(s): fd0 is 1.44M
[17179587.168000] FDC 0 is a post-1991 82077
[17179587.484000] usbcore: registered new driver hiddev
[17179587.500000] input: NOVATEK USB Keyboard as /class/input/input2
[17179587.500000] input: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1d.3-1
[17179587.524000] parport: PnPBIOS parport detected.
[17179587.524000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179587.528000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17179587.528000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 21 (level, low) -> IRQ 217
[17179587.528000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17179587.528000] eth0: RTL8169 at 0xf8a46000, 00:0f:ea:f4:be:5f, IRQ 217
[17179587.540000] input: NOVATEK USB Keyboard as /class/input/input3
[17179587.540000] input,hiddev96: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1d.3-1
[17179587.588000] input: HID 1241:1166 as /class/input/input4
[17179587.588000] input: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:1d.3-2
[17179587.588000] usbcore: registered new driver usbhid
[17179587.588000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179587.824000] ts: Compaq touchscreen protocol output
[17179588.344000] r8169: eth0: link down
[17179588.512000] lp0: using parport0 (interrupt-driven).
[17179588.540000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179588.540000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179588.540000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179588.580000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179588.608000] usbcore: registered new driver ndiswrapper
[17179588.644000] Adding 1044184k swap on /dev/sda7.  Priority:-1 extents:1 across:1044184k
[17179588.804000] EXT3 FS on sda9, internal journal
[17179588.952000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179588.952000] md: bitmap version 4.39
[17179589.360000] r8169: eth0: link up
[17179589.520000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179589.560000] NET: Registered protocol family 17
[17179590.124000] cdrom: open failed.
[17179591.968000] NET: Registered protocol family 10
[17179591.968000] lo: Disabled Privacy Extensions
[17179591.968000] IPv6 over IPv4 tunneling driver
[17179592.072000]   Vendor: HDS72808  Model: 0PLAT20           Rev:  0 0
[17179592.072000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179592.072000] SCSI device sdb: 160836480 512-byte hdwr sectors (82348 MB)
[17179592.072000] sdb: assuming drive cache: write through
[17179592.072000] SCSI device sdb: 160836480 512-byte hdwr sectors (82348 MB)
[17179592.072000] sdb: assuming drive cache: write through
[17179592.072000]  sdb: sdb1
[17179592.080000] sd 2:0:0:0: Attached scsi disk sdb
[17179592.080000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[17179592.080000] usb-storage: device scan complete
[17179592.808000] kjournald starting.  Commit interval 5 seconds
[17179592.808000] EXT3 FS on sda6, internal journal
[17179592.808000] EXT3-fs: mounted filesystem with ordered data mode.
[17179592.816000] kjournald starting.  Commit interval 5 seconds
[17179592.816000] EXT3 FS on sda8, internal journal
[17179592.816000] EXT3-fs: mounted filesystem with ordered data mode.
[17179592.896000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179592.964000] NTFS volume version 3.1.
[17179597.488000] ACPI: Power Button (FF) [PWRF]
[17179597.488000] ACPI: Power Button (CM) [PWRB]
[17179597.576000] ibm_acpi: ec object not found
[17179597.608000] pcc_acpi: loading...
[17179601.248000] [drm] Initialized drm 1.0.1 20051102
[17179601.260000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179601.260000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179601.892000] ppdev: user-space parallel port driver
[17179602.252000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179602.252000] apm: overridden by ACPI.
[17179602.548000] eth0: no IPv6 routers present
[17179604.548000] Bluetooth: Core ver 2.8
[17179604.548000] NET: Registered protocol family 31
[17179604.548000] Bluetooth: HCI device and connection manager initialized
[17179604.548000] Bluetooth: HCI socket layer initialized
[17179604.592000] Bluetooth: L2CAP ver 2.8
[17179604.592000] Bluetooth: L2CAP socket layer initialized
[17179604.596000] Bluetooth: RFCOMM socket layer initialized
[17179604.596000] Bluetooth: RFCOMM TTY layer initialized
[17179604.596000] Bluetooth: RFCOMM ver 1.7
[17179618.708000] [drm] Setting GART location based on new memory map
[17179618.708000] [drm] Loading R300 Microcode
[17179618.708000] [drm] writeback test succeeded in 1 usecs
[17179634.920000] NTFS-fs warning (device sdb1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17179634.964000] NTFS volume version 3.1.
[17181047.028000] eth0: no IPv6 routers present
ljz@ljz-desktop:~$
===========================================
==========ndiswrapper -l===========================
ljz@ljz-desktop:~$ sudo ndiswrapper -l
Installed ndis drivers:
2862w           driver present
=====================================================

---

### Post by robli99 on 2006-11-12
dmesg shows ndiswrapper is loaded, but it does show up wlan0

=================================
ljz@ljz-desktop:~$ sudo dmesg | grep ndiswrapper
[17179588.580000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179588.608000] usbcore: registered new driver ndiswrapper
ljz@ljz-desktop:~$ sudo dmesg | grep wlan0
=====================================

---

### Post by FrodoB on 2006-11-12
Well now that you have blacklisted the other driver could you please publish the outputs of:

iwconfig 

ifconfig

and the contents of /etc/network/interfaces 

again please.

---

### Post by FrodoB on 2006-11-12
I would also note that the Yawnster has gone through a very difficult time with another device that contains a similar chip and he has published this howto that might prove informative in this situation:

[https://help.ubuntu.com/community/WifiDocs/Device/WG121](https://help.ubuntu.com/community/WifiDocs/Device/WG121)

---

### Post by robli99 on 2006-11-13
I followed the following instruction to add more blacklist.
[https://help.ubuntu.com/community/WifiDocs/Device/WG121](https://help.ubuntu.com/community/WifiDocs/Device/WG121)

Now the result os iwconfig and ifconfig are:
=========================================
ljz@ljz-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ljz@ljz-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:F4:BE:5F
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fef4:be5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10124260 (9.6 MiB)  TX bytes:309383 (302.1 KiB)
          Interrupt:217 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)
==========================================

---

### Post by FrodoB on 2006-11-13
I hate to say it, but I would just do a fresh install and start over. I would start a new thread on this issue as well and make a link from the end of this one to the new thread so you don't loose anyone.

We need to see the output of:

iwconfig

first thing in your new thread.

---

### Post by docplastic on 2006-11-27
> **robli99 said:**
> I am using a SMC ez-connected 2862w USB2 wireless adapter,

I am using a SMC 2862W-G (0707:ee13) under Ubuntu 6.10 and NdisWrapper without any problems, but first I had to:

1. Edit the blacklist file:

 ```
sudo gedit /etc/modprobe.d/blacklist
```

and add to the end of that file the following lines:

```
# Disabling rt2500 wireless usb stick  - edited by jama
blacklist rt2400
blacklist rt2500
blacklist rt2570
blacklist rt73usb
```

(NB: Possibly it is only really needed to add the blacklist rt73usb line.)

2. Then **rebooted** the PC

3. Finally installed:

```
sudo apt-get install ndiswrapper-utils-1.8 ndiswrapper-utils-1.1 ndiswrapper-utils ndiswrapper-common ndisgtk
```

4. Called **sudo /usr/bin/ndisgtk** and from there loaded the latest WinXP .inf (/Driver/WinXP/SMC2862W.inf)

5. Calling **iwconfig**... showed a wlan0 interface ready to use:
```

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:19 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Hope, this helps.

J.

---

### Post by FrodoB on 2006-11-27
I would add that if you have defined the device as wlan0 in /etc/mopdrobe.d/ndiswrapper and it does not show up as wlan0, this is because some other device's MAC identifier is tied to wlan0 in:

/etc/iftab

use 

sudo gedit /etc/iftab 

and remove the device that is tied to wlan0 and reboot and it should now be wlan0 for sure.

---

### Post by lukeluke on 2006-11-27
> **FrodoB said:**
> I would add that if you have defined the device as wlan0 in /etc/mopdrobe.d/ndiswrapper and it does not show up as wlan0, this is because some other device's MAC identifier is tied to wlan0 in:

/etc/iftab

use 

sudo gedit /etc/iftab 

and remove the device that is tied to wlan0 and reboot and it should now be wlan0 for sure.

I had the same problem: eth1 getting up in place of wlan0. Editing /etc/iftab did the trick, thanks! :)

---

