---
title: "problem with ethernet card"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by toketin on 2006-12-08
hi, i'm italian and my english is not very good...... i've ubuntu dapper installed on my pc and i've an etehernet card (d-link dfe-528tx) which probably ysue the module 8139too, i tried everything but this card isn't recognised from ubuntu.
is probably that with the ubuntu older tahn dapper version the card can work correctly?

thanks

---

### Post by dbott67 on 2006-12-08
Can you copy & paste the output of the following commadns to a text file & save it to USB/floppy and bring it over to a working computer:

```
cat/etc/network/interfaces
```

Here's mine as an example:

```
dbott@dapper:~$ cat/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```

This command shows ALL network interfaces on the system (whether enabled or not):

```
ifconfig -a
```

```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

This command outputs the network hardware detected:

```
sudo lshw -C network
```

Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

Thanks,
Dave

---

### Post by toketin on 2006-12-09
these are my outputs:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


marco@marco-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10016 (9.7 KiB)  TX bytes:10016 (9.7 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


marco@marco-desktop:~$ sudo lshw -C network
Password:
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: c
       bus info: pci@00:0c.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: ioport:de00-deff iomemory:efffff00-efffffff irq:10


```

---

### Post by dbott67 on 2006-12-09
I've got the same card in my desktop:
```
dbott@edgy:~$ lsmod | grep 8139too
8139too                27136  0
mii                     6016  1 8139too

```
```
dbott@edgy:~$ sudo lshw -C network
Password:
  *-network
       description: Ethernet interface
       **[COLOR="Red"]product: RTL8139 Ethernet[/COLOR]**
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes **[COLOR="Red"]driver=8139too[/COLOR]** driverversion=0.9.27 duplex=full ip=192.168.1.106 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:185

```

Check the output of dmesg to see if there are any errors.
```
dmesg
```

See if the module is already loaded:
```
lsmod | grep 8139too
```
If nothing is listed, try loading it manually:
```
sudo modprobe 8139too
```
Check the end of dmesg again and see if there are any errors.

Let me know.

-Dave

---

### Post by dbott67 on 2006-12-09
Also, do you dual-boot your machine with Windows?  If so, does the card work in Windows?

If you don't dual boot, can you try booting from the "Live CD"? 

-Dave

---

### Post by toketin on 2006-12-09
the modules are already loaded, because this is my lsmod output:

```
marco@marco-desktop:~$ lsmod
Module                  Size  Used by
de4x5                  50208  0
ipv6                  265728  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
mga                    66944  1
drm                    73236  2 mga
ppdev                   9220  0
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
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
af_packet              22920  0
nls_utf8                2176  1
ntfs                  103536  1
dm_mod                 58936  1
md_mod                 72532  0
8139cp                 22528  0
lp                     11844  0
tsdev                   8000  0
floppy                 62148  0
pcspkr                  2180  0
8139too                26880  0
snd_ens1371            24672  3
gameport               15496  1 snd_ens1371
mii                     5888  2 8139cp,8139too
snd_rawmidi            25504  1 snd_ens1371
snd_seq_device          8716  1 snd_rawmidi
matrox_w1               4096  0
snd_ac97_codec         93088  1 snd_ens1371
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd_pcm                89864  4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
rtc                    13492  0
psmouse                36100  0
serio_raw               7300  0
wire                   25384  1 matrox_w1
snd                    55268  12 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  1 snd_pcm
snd_ac97_bus            2304  1 snd_ac97_codec
i2c_amd756              6660  0
i2c_core               21904  2 i2c_acpi_ec,i2c_amd756
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
amd_k7_agp              8588  1
agpgart                34888  2 drm,amd_k7_agp
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci_hcd               21892  0
usbcore               130692  2 ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
generic                 5124  0
amd74xx                15260  0 [permanent]
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
```

with windows the card works correctly....

---

### Post by toketin on 2006-12-09
my output for dmesg and the other:

```
marco@marco-desktop:~$ dmesg
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000bff0000 (usable)
[17179569.184000]  BIOS-e820: 000000000bff0000 - 000000000bff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000bff8000 - 000000000c000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 191MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 49136
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 45040 pages, LIFO batch:7
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa770
[17179569.184000] ACPI: RSDT (v001 AMIINT          0x00000010 MSFT 0x00000097) @ 0x0bff0000
[17179569.184000] ACPI: FADT (v001 AMIINT          0x00000010 MSFT 0x00000097) @ 0x0bff0030
[17179569.184000] ACPI: DSDT (v001 AMD75X IRONGATE 0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x5008
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f3ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01181000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 606.078 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.628000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.628000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179569.644000] Memory: 184116k/196544k available (1976k kernel code, 11876k reserved, 606k data, 288k init, 0k highmem)
[17179569.644000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.724000] Calibrating delay using timer specific routine.. 1213.28 BogoMIPS (lpj=2426575)
[17179569.724000] Security Framework v1.0.0 initialized
[17179569.724000] SELinux:  Disabled at boot.
[17179569.724000] Mount-cache hash table entries: 512
[17179569.724000] CPU: After generic identify, caps: 0183f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179569.724000] CPU: After vendor identify, caps: 0183f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179569.724000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.724000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.724000] CPU: After all inits, caps: 0183f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[17179569.724000] mtrr: v2.0 (20020519)
[17179569.724000] CPU: AMD Athlon(tm) Processor stepping 01
[17179569.724000] Enabling fast FPU save and restore... done.
[17179569.724000] Checking 'hlt' instruction... OK.
[17179569.740000] checking if image is initramfs... it is
[17179571.548000] Freeing initrd memory: 6840k freed
[17179571.580000] ACPI: Looking for DSDT ... not found!
[17179571.584000] ACPI: setting ELCR to 0800 (from 0e20)
[17179571.584000] NET: Registered protocol family 16
[17179571.584000] EISA bus registered
[17179571.584000] ACPI: bus type pci registered
[17179571.600000] PCI: PCI BIOS revision 2.10 entry at 0xfdb71, last bus=1
[17179571.600000] PCI: Using configuration type 1
[17179571.600000] ACPI: Subsystem revision 20051216
[17179571.612000] ACPI: Interpreter enabled
[17179571.612000] ACPI: Using PIC for interrupt routing
[17179571.616000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.616000] PCI: Probing PCI hardware (bus 00)
[17179571.620000] Boot video device is 0000:01:05.0
[17179571.620000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.628000] ACPI: Power Resource [URP1] (off)
[17179571.628000] ACPI: Power Resource [URP2] (off)
[17179571.628000] ACPI: Power Resource [FDDP] (off)
[17179571.628000] ACPI: Power Resource [LPTP] (off)
[17179571.632000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179571.632000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179571.632000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179571.632000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179571.632000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.632000] pnp: PnP ACPI init
[17179571.640000] pnp: PnP ACPI: found 11 devices
[17179571.640000] PnPBIOS: Disabled by ACPI PNP
[17179571.640000] PCI: Using ACPI for IRQ routing
[17179571.640000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.644000] pnp: 00:00: ioport range 0xde00-0xde03 has been reserved
[17179571.644000] PCI: Bridge: 0000:00:01.0
[17179571.644000]   IO window: c000-cfff
[17179571.644000]   MEM window: eee00000-efefffff
[17179571.644000]   PREFETCH window: e2c00000-e6cfffff
[17179571.644000] audit: initializing netlink socket (disabled)
[17179571.644000] audit(1165690304.644:1): initialized
[17179571.644000] VFS: Disk quotas dquot_6.5.1
[17179571.644000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.644000] Initializing Cryptographic API
[17179571.644000] io scheduler noop registered
[17179571.644000] io scheduler anticipatory registered
[17179571.644000] io scheduler deadline registered
[17179571.644000] io scheduler cfq registered
[17179571.648000] isapnp: Scanning for PnP cards...
[17179572.000000] isapnp: No Plug & Play device found
[17179572.044000] PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179572.044000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.044000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.044000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.044000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.044000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.052000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.052000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.052000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.052000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.052000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.052000] mice: PS/2 mouse device common for all mice
[17179572.052000] EISA: Probing bus 0 at eisa.0
[17179572.052000] Cannot allocate resource for EISA slot 5
[17179572.052000] EISA: Detected 0 cards.
[17179572.052000] NET: Registered protocol family 2
[17179572.088000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.092000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)[17179572.092000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[17179572.092000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[17179572.092000] TCP: Hash tables configured (established 8192 bind 8192)
[17179572.092000] TCP reno registered
[17179572.092000] TCP bic registered
[17179572.092000] NET: Registered protocol family 1
[17179572.092000] NET: Registered protocol family 8
[17179572.092000] NET: Registered protocol family 20
[17179572.092000] Using IPI Shortcut mode
[17179572.092000] ACPI wakeup devices:
[17179572.092000] PCI0 UAR1  USB
[17179572.092000] ACPI: (supports S0 S1 S4 S5)
[17179572.092000] Freeing unused kernel memory: 288k freed
[17179572.244000] vga16fb: initializing
[17179572.244000] vga16fb: mapped to 0xc00a0000
[17179572.304000] Console: switchin&#30360; to colour frame buffer device 80x25
[17179572.304000] fb0: VGA16 VGA frame buffer device
[17179573.440000] Capability LSM initialized
[17179573.556000] ACPI: Thermal Zone [THRM] (47 C)
[17179574.920000] AMD7409: IDE controller at PCI slot 0000:00:07.1
[17179574.920000] AMD7409: chipset revision 7
[17179574.920000] AMD7409: not 100% native mode: will probe irqs later
[17179574.920000] AMD7409: 0000:00:07.1 (rev 07) UDMA66 controller
[17179574.920000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[17179574.920000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[17179574.920000] Probing IDE interface ide0...
[17179575.208000] hda: SAMSUNG SV1533D, ATA DISK drive
[17179575.880000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.880000] Probing IDE interface ide1...
[17179576.616000] hdc: HL-DT-ST GCE-8525B, ATAPI CD/DVD-ROM drive
[17179577.288000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.312000] hda: max request size: 128KiB
[17179577.332000] hda: 29897280 sectors (15307 MB) w/472KiB Cache, CHS=29660/16/63, UDMA(33)
[17179577.332000] hda: cache flushes not supported
[17179577.332000]  hda: hda1 hda2 hda3
[17179577.364000] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.364000] Uniform CD-ROM driver Revision: 3.20
[17179577.928000] usbcore: registered new driver usbfs
[17179577.928000] usbcore: registered new driver hub
[17179577.932000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.936000] **** SET: Misaligned resource pointer: cbc1f4e2 Type 07 Len 0
[17179577.936000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[17179577.936000] PCI: setting IRQ 5 as level-triggered
[17179577.936000] ACPI: PCI Interrupt 0000:00:07.4[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179577.936000] ohci_hcd 0000:00:07.4: OHCI Host Controller
[17179577.936000] ohci_hcd 0000:00:07.4: new USB bus registered, assigned bus number 1
[17179577.936000] ohci_hcd 0000:00:07.4: irq 5, io mem 0xeffcf000
[17179577.992000] hub 1-0:1.0: USB hub found
[17179577.992000] hub 1-0:1.0: 4 ports detected
[17179578.256000] Attempting manual resume
[17179578.336000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.360000] kjournald starting.  Commit interval 5 seconds
[17179598.744000] Linux agpgart interface v0.101 (c) Dave Jones
[17179598.780000] agpgart: Detected AMD Irongate chipset
[17179598.800000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179598.824000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179598.832000] shpchp: HPC vendor_id 1022 device_id 7007 ss_vid 0 ss_did 0
[17179598.832000] shpchp: shpc_init: cannot reserve MMIO region
[17179598.832000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179599.680000] logips2pp: Detected unknown logitech mouse model 1
[17179600.004000] **** SET: Misaligned resource pointer: cbb82102 Type 07 Len 0
[17179600.004000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[17179600.004000] PCI: setting IRQ 10 as level-triggered
[17179600.004000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179600.168000] input: PS/2 Logitech Mouse as /class/input/input1
[17179600.228000] Driver for 1-wire Dallas network protocol.
[17179600.532000] Floppy drive(s): fd0 is 1.44M
[17179600.540000] Real Time Clock Driver v1.12
[17179600.548000] input: PC Speaker as /class/input/input2
[17179600.552000] FDC 0 is a post-1991 82077
[17179600.572000] 8139too Fast Ethernet driver 0.9.27
[17179600.664000] parport: PnPBIOS parport detected.
[17179600.664000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179600.916000] matrox_w1 0000:01:05.0: Matrox G400 GPIO transport layer for 1-wire.
[17179600.916000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179600.916000] PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:0c.0
[17179600.916000] Trying to free nonexistent resource <0000de00-0000deff>
[17179600.916000] Trying to free nonexistent resource <efffff00-efffffff>
[17179600.916000] 8139too: probe &#30360;f 0000:00:0c.0 failed with error -16
[17179601.180000] ts: Compaq touchscreen protocol output
[17179603.160000] lp0: using parport0 (interrupt-driven).
[17179603.232000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179603.496000] Adding 522104k swap on /dev/hda2.  Priority:-1 extents:1 across:522104k
[17179603.668000] EXT3 FS on hda3, internal journal
[17179604.068000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179604.068000] md: bitmap version 4.39
[17179604.960000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179605.868000] cdrom: open failed.
[17179606.832000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179606.948000] NTFS volume version 3.1.
[17179609.216000] NET: Registered protocol family 17
[17179616.640000] ACPI: Power Button (FF) [PWRF]
[17179616.640000] ACPI: Sleep Button (FF) [SLPF]
[17179616.640000] ACPI: Power Button (CM) [PWRB]
[17179616.940000] ibm_acpi: ec object not found
[17179617.012000] pcc_acpi: loading...
[17179618.092000] powernow: No powernow capabilities detected
[17179628.180000] ppdev: user-space parallel port driver
[17179629.376000] [drm] Initialized drm 1.0.1 20051102
[17179629.388000] **** SET: Misaligned resource pointer: c77353e2 Type 07 Len 0
[17179629.388000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179629.388000] PCI: setting IRQ 11 as level-triggered
[17179629.388000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179629.392000] [drm] Initialized mga 3.2.1 20051102 on minor 0
[17179629.396000] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[17179629.396000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179629.396000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 1x mode
[17179629.504000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179629.504000] apm: overridden by ACPI.
[17179635.408000] Bluetooth: Core ver 2.8
[17179635.408000] NET: Registered protocol family 31
[17179635.408000] Bluetooth: HCI device and connection manager initialized
[17179635.408000] Bluetooth: HCI socket layer initialized
[17179635.596000] Bluetooth: L2CAP ver 2.8
[17179635.596000] Bluetooth: L2CAP socket layer initialized
[17179635.664000] Bluetooth: RFCOMM socket layer initialized
[17179635.664000] Bluetooth: RFCOMM TTY layer initialized
[17179635.664000] Bluetooth: RFCOMM ver 1.7
[17179652.592000] NET: Registered protocol family 10
[17179652.592000] lo: Disabled Privacy Extensions
[17179652.592000] IPv6 over IPv4 tunneling driver
marco@marco-desktop:~$ lsmod | grep 8139too
8139too                26880  0
mii                     5888  2 8139cp,8139too

```

---

### Post by dbott67 on 2006-12-09
```
[17179600.572000] 8139too Fast Ethernet driver 0.9.27
[17179600.664000] parport: PnPBIOS parport detected.
[17179600.664000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179600.916000] matrox_w1 0000:01:05.0: Matrox G400 GPIO transport layer for 1-wire.
[17179600.916000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179600.916000] PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:0c.0
[17179600.916000] Trying to free nonexistent resource <0000de00-0000deff>
[COLOR=Red][17179600.916000] Trying to free nonexistent resource <efffff00-efffffff>
[17179600.916000] 8139too: probe &#30360;f 0000:00:0c.0 failed with error -16[/COLOR]
```Well, there's the source of yer trouble... the old dreaded 'error 16'!  It's a good thing it's not error 15, 'cuz we all know what that means!  I remember once, musta been back in '02 or so... got me a dreaded 'error 22'.  WHOOOOOO-WHEEEEEEEE!!!! I'll tell ya, thems were some good times, I tell ya.
[I]
(of course, I have no idea what either error 15 or 16 is, but I was just having some fun)[/I]

Anyhow, if you've got another NIC lying around (or can borrow a different one), maybe you could try that & see if it works.

-Dave

---

### Post by toketin on 2006-12-10
so this card doesn't work for me, and you advice me to buy another one?

---

### Post by missmoondog on 2006-12-10
i have the same card in 3 of my machines and they all worked out of the box for me, on every distributioin of linux i've tried.

---

### Post by toketin on 2006-12-10
but have you got the card called "DFE-528TX OF D-LINK"?

---

### Post by zasf on 2006-12-24
I have exactly the same card (DFE-528TX) and it works out of the box

---

### Post by toketin on 2007-01-05
with kubuntu is probably that the card will be recognized??

---

### Post by koenn on 2007-01-05
no - the desktop (gnome, kde, ... is just what you see on your screen, the system underneath it is the same in kubuntu or ubuntu)
Ubuntu recognizes the cart as a realtek 1839 and loads the driver for it - but apparently the driver is not capable of communicating with the card - at least thats how I understand the 
[17179600.916000] 8139too: probe  0000:00:0c.0 failed with error -16

 It's possible the card is broken, that's why it would be good to try with an other card if you have one or are willing to by one (they cost 10-15 $ if i'm not mistaking).

---

### Post by toketin on 2007-01-20
on the new version of ubuntu is probably that will my card be recognised?...... have anyone already try it on the new ubuntu?

---

