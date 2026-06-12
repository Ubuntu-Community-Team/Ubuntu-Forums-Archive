---
title: "[SOLVED] eth0 device not found (Xubuntu 6.06.1 - but works fine with Live CD!)"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by Benjamin G on 2007-09-01
Hi,

I completed a graphical install of Xubuntu 6.06.1 this evening, and am having problems setting up the ethernet card (D-Link DE-660+ PC Card).  Laptop is a Toshiba Satellite 1700-300.

I haven't encountered this problem before: previous text-based installs of Debian Sarge, Ubuntu 5.10 and Kubuntu 6.06, and both Knoppix and this Xubuntu 6.06.1 Live CD, have configured everything correctly, allowing me to gain access to the network out of the box.

Information which may be useful...

**ifconfig**
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)
```

No eth0.

**sudo dhclient eth0**
```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
```
Same result if one replace eth0 with eth1, eth2 or eth3.

**more /etc/network/interfaces**
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

```

**lsmod**
```
Module                  Size  Used by
nls_utf8                2176  1 
nls_cp437               5888  1 
vfat                   13440  1 
fat                    53020  1 vfat
sg                     37920  0 
sd_mod                 19984  2 
usb_storage            74176  1 
scsi_mod              139496  3 sg,sd_mod,usb_storage
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
dm_mod                 58936  1 
md_mod                 72532  0 
lp                     11844  0 
floppy                 62148  0 
tsdev                   8000  0 
pcspkr                  2180  0 
pcmcia                 40508  0 
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
psmouse                36100  0 
serio_raw               7300  0 
rtc                    13492  0 
snd_cs4281             21856  1 
gameport               15496  2 snd_cs4281
snd_rawmidi            25504  1 snd_cs4281
snd_ac97_codec         93088  1 snd_cs4281
snd_ac97_bus            2304  1 snd_ac97_codec
ltserial               11056  0 
ltmodem               566638  1 ltserial
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_cs4281,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10632  1 snd_pcm
snd_opl3_lib           10624  1 snd_cs4281
yenta_socket           28428  3 
snd_seq_device          8716  2 snd_rawmidi,snd_opl3_lib
snd_timer              25220  2 snd_pcm,snd_opl3_lib
snd_hwdep               9376  1 snd_opl3_lib
intel_agp              22940  1 
agpgart                34888  1 intel_agp
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    55268  12 snd_cs4281,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_seq_device,snd_timer,snd_hwdep
shpchp                 45632  0 
i2c_piix4               9104  0 
pci_hotplug            29236  1 shpchp
soundcore              10208  1 snd
i2c_core               21904  2 i2c_acpi_ec,i2c_piix4
evdev                   9856  1 
ext3                  135688  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
uhci_hcd               33680  0 
usbcore               130692  3 usb_storage,uhci_hcd
ide_cd                 33028  0 
cdrom                  38560  1 ide_cd
ide_disk               17664  3 
piix                   11012  1 
generic                 5124  0 
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

Any help would be much appreciated!

Thanks,

Benjamin

---

### Post by lloyd_b on 2007-09-01
1.  Boot using the Live CD.  Once booted, open a terminal window, and run 
```
lshw
```
This will list all the devices in the system, including the D-Link card, and tell you what driver is claiming each of them.  Note the driver being used on that card.

Then, boot normally, and run the same command again.  See if the D-Link card appears, and what (if any) driver is claiming it.

Please post the results of these tests (if possible). 

Lloyd B.

---

### Post by Benjamin G on 2007-09-01
Ok, using the LiveCD lshw returns
```
ubuntu
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 191MB
     *-cpu
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.6
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: e0000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 64
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:fd000000-fdffffff ioport:2000-20ff iomemory:fc100000-fc100fff irq:10
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 4
             bus info: pci@00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:18100000-18100fff irq:10
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 4.1
             bus info: pci@00:04.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:18101000-18101fff irq:10
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1050-105f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: FUJITSU MHM2060AT
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 5729MB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: TOSHIBA DVD-ROM SD-C2302
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 653MB
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1060-107f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: External HDD
                   vendor: Western Digital
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.02
                   serial: 575845313037433332393237
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=0mA speed=12.0MB/s
        *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: Crystal CS4281 PCI Audio
             vendor: Cirrus Logic
             physical id: 8
             bus info: pci@00:08.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=CS4281
             resources: iomemory:fc010000-fc010fff iomemory:fc000000-fc00ffff irq:5
        *-communication UNCLAIMED
             description: Communication controller
             product: LT WinModem
             vendor: Agere Systems
             physical id: 10
             bus info: pci@00:10.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:fc011000-fc0110ff ioport:1080-1087 ioport:1400-14ff irq:10
  *-scsi
       physical id: 1
       bus info: scsi@0
       logical name: scsi0
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth0
       serial: 00:50:ba:87:bb:84
       capabilities: ethernet physical
       configuration: broadcast=yes ip=129.67.63.183 multicast=yes

```
HDD boot results shortly...

---

### Post by Benjamin G on 2007-09-01
When booting from the hdd, the ethernet card isn't detected:
```
stu433
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 191MB
     *-cpu
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.6
          size: 50MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: e0000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 64
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:fd000000-fdffffff ioport:2000-20ff iomemory:fc100000-fc100fff irq:10
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 4
             bus info: pci@00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:18100000-18100fff irq:10
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: 4.1
             bus info: pci@00:04.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:18101000-18101fff irq:10
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1050-105f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: FUJITSU MHM2060AT
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 5729MB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: TOSHIBA DVD-ROM SD-C2302
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1060-107f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   product: External HDD
                   vendor: Western Digital
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.02
                   serial: 575845313037433332393237
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=0mA speed=12.0MB/s
        *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: Crystal CS4281 PCI Audio
             vendor: Cirrus Logic
             physical id: 8
             bus info: pci@00:08.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=CS4281
             resources: iomemory:fc010000-fc010fff iomemory:fc000000-fc00ffff irq:5
        *-communication UNCLAIMED
             description: Communication controller
             product: LT WinModem
             vendor: Agere Systems
             physical id: 10
             bus info: pci@00:10.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:fc011000-fc0110ff ioport:1080-1087 ioport:1400-14ff irq:10
  *-scsi
       physical id: 1
       bus info: scsi@0
       logical name: scsi0
       capabilities: scsi-host
       configuration: driver=usb-storage

```

---

### Post by lloyd_b on 2007-09-01
Okay, nothing useful there.  I believe I was misunderstanding your hardware, anyway.  That is a "PC Card" (as in a credit-card sized gadget you stick into the laptop), correct? (I still always think of them as PCMCIA cards).

If so, when booted from the HD, in a terminal window:
```
pccardctl -v ident
```

This *should* identify all such cards that you have in the system.  Let's see if it's even being detected...

Another idea (if you haven't already tried it) - boot the machine up without the card, then insert it after you get logged in.  

One more question: what kernel version is that running? ("cat /proc/version" to obtain that info).  The reason I ask is I can't remember what kernel Dapper (6.06) used, and there was a BIG change in the way PCMCIA cards were handled between the 2.4.x kernels and the 2.6.x kernels.

Lloyd B.

---

### Post by Benjamin G on 2007-09-01
Thanks Lloyd.  I've looked at the lsmod output for the hdd and cd boots respectively, and noticed that the pcnet_cs module is not being run automatically when booting from the hdd.  I've tried adding it using
```
modprobe pcnet_cs
```
and it loads the module, but it still doesn't detect the ethernet card.  Do I need to edit a configuration file so that it runs at startup?  Do I need to do anything else?

The output of lsmod for the cd boot is:
```
Module                  Size  Used by
nls_utf8                2176  1 
vfat                   13440  1 
fat                    53020  1 vfat
sg                     37920  0 
sd_mod                 19984  2 
usb_storage            74176  1 
scsi_mod              139496  3 sg,sd_mod,usb_storage
ppdev                   9220  0 
lp                     11844  0 
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
ipv6                  265728  6 
dm_mod                 58936  1 
md_mod                 72532  0 
af_packet              22920  2 
pcnet_cs               39220  1 
8390                   10496  1 pcnet_cs
pcmcia                 40508  1 pcnet_cs
snd_cs4281             21856  1 
gameport               15496  2 snd_cs4281
snd_rawmidi            25504  1 snd_cs4281
snd_ac97_codec         93088  1 snd_cs4281
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
tsdev                   8000  0 
snd_pcm                89864  3 snd_cs4281,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10632  1 snd_pcm
snd_opl3_lib           10624  1 snd_cs4281
snd_seq_device          8716  2 snd_rawmidi,snd_opl3_lib
snd_timer              25220  2 snd_pcm,snd_opl3_lib
snd_hwdep               9376  1 snd_opl3_lib
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
snd                    55268  12 snd_cs4281,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_seq_device,snd_timer,snd_hwdep
floppy                 62148  0 
pcspkr                  2180  0 
rtc                    13492  0 
psmouse                36100  0 
yenta_socket           28428  4 
rsrc_nonstatic         13440  1 yenta_socket
serio_raw               7300  0 
ltserial               11056  0 
ltmodem               566638  1 ltserial
soundcore              10208  1 snd
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
i2c_piix4               9104  0 
i2c_core               21904  2 i2c_acpi_ec,i2c_piix4
intel_agp              22940  1 
agpgart                34888  1 intel_agp
evdev                   9856  1 
squashfs               44980  1 
unionfs                89884  1 
loop                   17288  2 
nls_cp437               5888  2 
isofs                  37688  1 
ide_generic             1536  0 
uhci_hcd               33680  0 
usbcore               130692  3 usb_storage,uhci_hcd
ide_cd                 33028  1 
cdrom                  38560  1 ide_cd
ide_disk               17664  2 
piix                   11012  1 
generic                 5124  0 
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
And for the hdd boot:
```
Module                  Size  Used by
nls_utf8                2176  1 
nls_cp437               5888  1 
vfat                   13440  1 
fat                    53020  1 vfat
sg                     37920  0 
sd_mod                 19984  2 
usb_storage            74176  1 
scsi_mod              139496  3 sg,sd_mod,usb_storage
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
dm_mod                 58936  1 
md_mod                 72532  0 
lp                     11844  0 
floppy                 62148  0 
tsdev                   8000  0 
pcspkr                  2180  0 
pcmcia                 40508  0 
parport_pc             35780  1 
parport                36296  3 ppdev,lp,parport_pc
psmouse                36100  0 
serio_raw               7300  0 
rtc                    13492  0 
snd_cs4281             21856  1 
gameport               15496  2 snd_cs4281
snd_rawmidi            25504  1 snd_cs4281
snd_ac97_codec         93088  1 snd_cs4281
snd_ac97_bus            2304  1 snd_ac97_codec
ltserial               11056  0 
ltmodem               566638  1 ltserial
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_cs4281,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10632  1 snd_pcm
snd_opl3_lib           10624  1 snd_cs4281
yenta_socket           28428  3 
snd_seq_device          8716  2 snd_rawmidi,snd_opl3_lib
snd_timer              25220  2 snd_pcm,snd_opl3_lib
snd_hwdep               9376  1 snd_opl3_lib
intel_agp              22940  1 
agpgart                34888  1 intel_agp
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    55268  12 snd_cs4281,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_seq_device,snd_timer,snd_hwdep
shpchp                 45632  0 
i2c_piix4               9104  0 
pci_hotplug            29236  1 shpchp
soundcore              10208  1 snd
i2c_core               21904  2 i2c_acpi_ec,i2c_piix4
evdev                   9856  1 
ext3                  135688  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
uhci_hcd               33680  0 
usbcore               130692  3 usb_storage,uhci_hcd
ide_cd                 33028  0 
cdrom                  38560  1 ide_cd
ide_disk               17664  3 
piix                   11012  1 
generic                 5124  0 
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

---

### Post by Benjamin G on 2007-09-01
Sorry, just missed your last post.  I'll try that now.

---

### Post by Benjamin G on 2007-09-01
> **lloyd_b said:**
> That is a "PC Card" (as in a credit-card sized gadget you stick into the laptop), correct? (I still always think of them as PCMCIA cards).  Yes, PCMCIA.  Sorry about the ambiguity.

Tried running "pccardctl ident":
- CD boot: Detected and identified card whichever of the two sockets I put it in.
- HD boot: Didn't detect card at all, regardless of socket it was in.  (And, if it's helpful to know, still didn't detect card when I tried it after loadin pcnet_cs.)

Kernel version is 2.6.15-26-386.

---

### Post by Benjamin G on 2007-09-01
Solved!  Improvised workaround as follows...

I noticed /etc/pcmcia on CD boot contained files, whereas /etc/pcmcia on HD boot was empty.  So copied files from CD filesystem to HD filesystem.  And it worked, so this post is actually being written using a HD boot!

I know this is potentially a messy solution, so if you think it might result in instability or if there is a better solution, please let me know.

Lloyd, thankyou so much for your time - it is much appreciated!

I may now head to bed and enjoy the joys of having a working ethernet card in the morning - it's 3.30am here...

---

### Post by lloyd_b on 2007-09-01
> I know this is potentially a messy solution, so if you think it might result in instability or if there is a better solution, please let me know.

I'm glad it's working for you.  I wouldn't expect this to create any problems, as files under "/etc" are mostly just configuration files.  The fact that you didn't have those files to begin with is troubling (it most likely means that the installer goofed), but I wouldn't expect it to cause any other problems.

Lloyd B.

---

