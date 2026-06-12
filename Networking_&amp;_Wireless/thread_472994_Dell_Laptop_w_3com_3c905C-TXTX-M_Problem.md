---
title: "Dell Laptop w 3com 3c905C-TX/TX-M Problem"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by performancepixel on 2007-06-13
I installed Ubuntu 7.04 on a Dell Precision M50 laptop yesterday and I am having trouble getting the network card to work.  I have tried setting a static address and using DHCP without success.  Based on the other network threads I have tried to run the commands that might provide some indication of why it's failing.  I have tried connecting to two different networks, one is a switch connected to an endian firewall w/ DHCP and the other a standard router that is providing DCHP.  There are other clients, including Fedora and Suse on the same networks and picking up DHCP leases without issue.  Any help is appreciated.  There are additional ifocnfig and lshw -C network at the bottom when the nic was configured back to DHCP from static.

```
root@esrmo-laptop:/etc/network# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:08:74:E6:AF:E6  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:60 (60.0 b)
          Interrupt:11 Base address:0xac00 

eth1      Link encap:Ethernet  HWaddr 00:02:2D:7F:E3:C5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5452 (5.3 KiB)  TX bytes:5452 (5.3 KiB)


root@esrmo-laptop:/etc/network# lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17GL [Quadro4 500 GoGL] (rev a3)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)

dmesg output:
[    6.620000] Time: acpi_pm clocksource has been installed.
[    6.744000] ata1.01: configured for UDMA/33
[    6.744000] scsi1 : ata_piix
[    6.900000] scsi 0:0:0:0: Direct-Access     ATA      IC25T060ATCS05-0 CA8O PQ: 0 ANSI: 5
[    6.900000] scsi 0:0:1:0: CD-ROM            SAMSUNG  CDRW/DVD SN-324B U101 PQ: 0 ANSI: 5
[    6.944000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    6.944000] sda: Write Protect is off
[    6.944000] sda: Mode Sense: 00 3a 00 00
[    6.944000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.944000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    6.944000] sda: Write Protect is off
[    6.944000] sda: Mode Sense: 00 3a 00 00
[    6.944000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.944000]  sda: sda1 sda2 < sda5 >
[    7.240000] sd 0:0:0:0: Attached scsi disk sda
[    7.248000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.248000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    7.264000] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    7.264000] Uniform CD-ROM driver Revision: 3.20
[    7.264000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    7.368000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[4a4fc00023642441]
[   25.388000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   25.388000] ata1.01: (BMDMA stat 0x64)
[   25.388000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 254 in
[   25.388000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
[   25.560000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[   25.560000] ata1.00: configured for UDMA/100
[   25.724000] ata1.01: configured for UDMA/33
[   25.724000] ata1: EH complete
[   25.724000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[   25.992000] sda: Write Protect is off
[   25.992000] sda: Mode Sense: 00 3a 00 00
[   26.000000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.072000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   44.072000] ata1.01: (BMDMA stat 0x64)
[   44.072000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 254 in
[   44.072000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
[   44.244000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[   44.244000] ata1.00: configured for UDMA/100
[   44.408000] ata1.01: configured for UDMA/33
[   44.408000] ata1: EH complete
[   44.408000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[   44.680000] sda: Write Protect is off
[   44.680000] sda: Mode Sense: 00 3a 00 00
[   44.680000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.844000] Attempting manual resume
[   44.844000] swsusp: Resume From Partition 8:5
[   44.844000] PM: Checking swsusp image.
[   44.848000] PM: Resume from disk failed.
[   44.904000] kjournald starting.  Commit interval 5 seconds
[   44.904000] EXT3-fs: mounted filesystem with ordered data mode.
[   58.416000] eth0:  setting half-duplex.
[   76.504000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   76.504000] ata1.01: (BMDMA stat 0x64)
[   76.504000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 254 in
[   76.504000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
[   76.676000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[   76.676000] ata1.00: configured for UDMA/100
[   76.840000] ata1.01: configured for UDMA/33
[   76.840000] ata1: EH complete
[   76.840000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[   77.108000] sda: Write Protect is off
[   77.108000] sda: Mode Sense: 00 3a 00 00
[   77.116000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   95.204000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   95.204000] ata1.01: (BMDMA stat 0x65)
[   95.204000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 254 in
[   95.204000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
[   95.376000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[   95.376000] ata1.00: configured for UDMA/100
[   95.540000] ata1.01: configured for UDMA/33
[   95.540000] ata1: EH complete
[   95.540000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[   95.816000] sda: Write Protect is off
[   95.816000] sda: Mode Sense: 00 3a 00 00
[   95.852000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   96.144000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   96.152000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   96.204000] parport: PnPBIOS parport detected.
[   96.204000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   96.292000] Linux agpgart interface v0.102 (c) Dave Jones
[   96.296000] agpgart: Detected an Intel i845 Chipset.
[   96.300000] agpgart: AGP aperture is 64M @ 0xe8000000
[   96.348000] input: PC Speaker as /class/input/input2
[   96.368000] iTCO_vendor_support: vendor-support=0
[   96.372000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   96.796000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:00d5]
[   96.796000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   96.796000] Yenta: Routing CardBus interrupts to PCI
[   96.796000] Yenta TI: socket 0000:02:01.0, mfunc 0x05033002, devctl 0x64
[   96.948000] input: DualPoint Stick as /class/input/input3
[   96.968000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input4
[   96.976000] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0x0860)
[   96.976000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   97.028000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[   97.028000] Socket status: 30000006
[   97.028000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   97.028000] cs: IO port probe 0xe000-0xffff: clean.
[   97.028000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   97.028000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x3dffffff
[   97.028000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:00d5]
[   97.028000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   97.028000] Yenta: Routing CardBus interrupts to PCI
[   97.028000] Yenta TI: socket 0000:02:01.1, mfunc 0x05033002, devctl 0x64
[   97.196000] NET: Registered protocol family 17
[   97.252000] intel_rng: FWH not detected
[   97.288000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[   97.288000] Socket status: 30000006
[   97.288000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   97.288000] cs: IO port probe 0xe000-0xffff: clean.
[   97.288000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   97.288000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x3dffffff
[   97.364000] Yenta: CardBus bridge found at 0000:02:03.0 [12a3:ab01]
[   97.364000] Yenta: Enabling burst memory read transactions
[   97.364000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   97.364000] Yenta: Routing CardBus interrupts to PCI
[   97.364000] Yenta TI: socket 0000:02:03.0, mfunc 0x01000002, devctl 0x60
[   97.616000] Yenta: ISA IRQ mask 0x0000, PCI irq 11
[   97.616000] Socket status: 30000010
[   97.616000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   97.616000] cs: IO port probe 0xe000-0xffff: clean.
[   97.616000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   97.616000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x3dffffff
[   97.632000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   97.632000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   98.200000] intel8x0_measure_ac97_clock: measured 55406 usecs
[   98.200000] intel8x0: clocking to 48000
[   98.276000] pccard: PCMCIA card inserted into slot 2
[   98.728000] cs: memory probe 0xf4000000-0xfbffffff: excluding 0xf4000000-0xf8ffffff
[   98.732000] pcmcia: registering new device pcmcia2.0
[   98.784000] cs: IO port probe 0x100-0x3af: clean.
[   98.784000] cs: IO port probe 0x3e0-0x4ff: clean.
[   98.784000] cs: IO port probe 0x820-0x8ff: clean.
[   98.784000] cs: IO port probe 0xc00-0xcf7: clean.
[   98.784000] cs: IO port probe 0xa00-0xaff: clean.
[   98.788000] cs: IO port probe 0x100-0x3af: clean.
[   98.788000] cs: IO port probe 0x3e0-0x4ff: clean.
[   98.788000] cs: IO port probe 0x820-0x8ff: clean.
[   98.788000] cs: IO port probe 0xc00-0xcf7: clean.
[   98.788000] cs: IO port probe 0xa00-0xaff: clean.
[   98.792000] cs: IO port probe 0x100-0x3af: clean.
[   98.792000] cs: IO port probe 0x3e0-0x4ff: clean.
[   98.792000] cs: IO port probe 0x820-0x8ff: clean.
[   98.792000] cs: IO port probe 0xc00-0xcf7: clean.
[   98.796000] cs: IO port probe 0xa00-0xaff: clean.
[   98.924000] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   98.928000] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   98.928000] pcmcia: request for exclusive IRQ could not be fulfilled.
[   98.928000] pcmcia: the driver needs updating to supported shared IRQ lines.
[   99.016000] eth1: Hardware identity 0005:0004:0005:0000
[   99.016000] eth1: Station identity  001f:0001:0008:000a
[   99.016000] eth1: Firmware determined as Lucent/Agere 8.10
[   99.016000] eth1: Ad-hoc demo mode supported
[   99.016000] eth1: IEEE standard IBSS ad-hoc mode supported
[   99.016000] eth1: WEP supported, 104-bit key
[   99.016000] eth1: MAC address 00:02:2D:7F:E3:C5
[   99.016000] eth1: Station name "HERMES I"
[   99.016000] eth1: ready
[   99.020000] eth1: orinoco_cs at 2.0, irq 11, io 0xe100-0xe13f
[   99.268000] fuse init (API version 7.8)
[   99.312000] lp0: using parport0 (interrupt-driven).
[   99.412000] Adding 1510068k swap on /dev/disk/by-uuid/3ddb5d66-b348-4e43-bc99-649d26ee5290.  Priority:-1 extents:1 across:1510068k
[   99.592000] EXT3 FS on sda1, internal journal
[  100.864000] ACPI: ACPI Dock Station Driver 
[  101.060000] input: Lid Switch as /class/input/input5
[  101.060000] ACPI: Lid Switch [LID]
[  101.088000] input: Power Button (CM) as /class/input/input6
[  101.088000] ACPI: Power Button (CM) [PBTN]
[  101.104000] input: Sleep Button (CM) as /class/input/input7
[  101.104000] ACPI: Sleep Button (CM) [SBTN]
[  101.324000] Using specific hotkey driver
[  101.376000] ACPI: AC Adapter [AC] (off-line)
[  101.408000] ibm_acpi: ec object not found
[  101.464000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[  101.900000] ACPI: Battery Slot [BAT0] (battery present)
[  102.020000] ACPI: Battery Slot [BAT1] (battery present)
[  102.124000] pcc_acpi: loading...
[  108.028000] eth1: New link status: Disconnected (0002)
[  109.652000] ppdev: user-space parallel port driver
[  110.644000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  110.644000] apm: overridden by ACPI.
[  111.160000] Bluetooth: Core ver 2.11
[  111.160000] NET: Registered protocol family 31
[  111.160000] Bluetooth: HCI device and connection manager initialized
[  111.160000] Bluetooth: HCI socket layer initialized
[  111.212000] Bluetooth: L2CAP ver 2.8
[  111.212000] Bluetooth: L2CAP socket layer initialized
[  111.620000] Bluetooth: RFCOMM socket layer initialized
[  111.620000] Bluetooth: RFCOMM TTY layer initialized
[  111.620000] Bluetooth: RFCOMM ver 1.8
[  134.420000] NET: Registered protocol family 10
[  134.420000] lo: Disabled Privacy Extensions
[  134.420000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  134.420000] ADDRCONF(NETDEV_UP): eth1: link is not ready
root@esrmo-laptop:/etc/network# 

root@esrmo-laptop:/etc/network# lsmod
Module                  Size  Used by
ipv6                  268704  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_ich           6288  0 
speedstep_lib           6148  1 speedstep_ich
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 speedstep_ich,cpufreq_stats,cpufreq_ondemand
tc1100_wmi              8068  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
pcc_acpi               13184  0 
container               5248  0 
battery                10756  0 
asus_acpi              17308  0 
video                  16388  0 
ac                      6020  0 
button                  8720  0 
backlight               7040  1 asus_acpi
sbs                    15652  0 
dock                   10268  0 
i2c_ec                  5888  1 sbs
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
orinoco_cs             16900  1 
orinoco                43028  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
joydev                 10816  0 
pcmcia                 39212  1 orinoco_cs
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
af_packet              23816  4 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
i2c_core               22784  1 i2c_ec
yenta_socket           27532  5 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               7940  0 
pcspkr                  4224  0 
psmouse                38920  0 
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
intel_agp              25116  1 
agpgart                35400  1 intel_agp
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
ata_generic             9092  0 
floppy                 59524  0 
ata_piix               15492  2 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
3c59x                  46632  0 
mii                     6528  1 3c59x
generic                 5124  0 [permanent]
uhci_hcd               25360  0 
usbcore               134280  2 uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
root@esrmo-laptop:/etc/network# 


root@esrmo-laptop:/etc/network# cat interfaces
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.2.100
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1

auto etho

Reset eth0 to DHCP and restarted networking:  Ifconfig
root@esrmo-laptop:/etc/network# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:74:E6:AF:E6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:60 (60.0 b)
          Interrupt:11 Base address:0xac00 

eth1      Link encap:Ethernet  HWaddr 00:02:2D:7F:E3:C5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe100 

eth0:avah Link encap:Ethernet  HWaddr 00:08:74:E6:AF:E6  
          inet addr:169.254.10.221  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xac00 

eth1:avah Link encap:Ethernet  HWaddr 00:02:2D:7F:E3:C5  
          inet addr:169.254.9.63  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xe100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8216 (8.0 KiB)  TX bytes:8216 (8.0 KiB)

root@esrmo-laptop:/etc/network# lshw -C network
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:e6:af:e6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:11
  *-network
       description: Wireless interface
       physical id: 3
       logical name: eth1
       serial: 00:02:2d:7f:e3:c5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 link=no multicast=yes wireless=IEEE 802.11b

```

---

### Post by chili555 on 2007-06-13
Please tell me what happens when you complete these commands in order:```
sudo ifdown eth0
sudo /etc/init.d/avahi-daemon stop
sudo ifup eth0
```

Thanks.

---

### Post by performancepixel on 2007-06-14
Here are the results of the requested commands.

```
admintb@esrmo-laptop:~$ sudo ifdown eth0
Password:
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 6129
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:08:74:e6:af:e6
Sending on   LPF/eth0/00:08:74:e6:af:e6
Sending on   Socket/fallback
admintb@esrmo-laptop:~$ sudo /etc/init.d/avahi-daemon stop
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                                                                                            [ OK ] 
admintb@esrmo-laptop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:08:74:e6:af:e6
Sending on   LPF/eth0/00:08:74:e6:af:e6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
admintb@esrmo-laptop:~$ 

```

---

### Post by performancepixel on 2007-06-14
Thanks for your help.  I might be making some headway.  I plugged the network cable into an ancient Kingston hub and got a link light.  So that started me thinking that the media settings might be the problem.  I have used mii-tool to force the settings to 100 and full and on reboot I _can't_ get a link to the Cisco 2950.  Doing a mii-tool watch on the interface, I can see 10Mb HD connect when I plug into the hub.  When I plug back into the 2950, I see no link with mii-tool until I force the media type to 100/full.  But when I restart networking, I still do not pick up a DHCP address and when I assign a static address, I don't get to the gateway and the arp table entry for the gateway is incomplete.  Any suggestions at this point?

Update:
I seemed to have solved the media type and duplex issues with mii-tool.  For s&g's I tried checking the roaming mode box and it worked.  So what is roaming mode, and why wouldn't a static work?

Thanks.

---

