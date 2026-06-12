---
title: "[SOLVED] Can't connect to wireless internet, no wireless extension"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by jose158 on 2008-04-06
I can't seem to connect to the internet anymore. All this started after I did a partial update. I installed wicd but to no avail. I ran iwconfig and got this:     Code:
```

lo          no wireless extension

eth0      no wireless extension 
``` any help appreciated.

---

### Post by anjpr on 2008-04-06
There's two of us.  I have the same problem and get the same message.  For a while my wireless worked fine.  Nonetheless, after some updates I haven't been able to connect wireless.  I changed the wireless card to Atheros to avoid issues with nsdwrapper.  It didn't work.  Now what?

---

### Post by Whiffle on 2008-04-06
Looks like your wireless drivers aren't loaded.  Could you post the output of "lspci -v" and "lsmod"?

---

### Post by jose158 on 2008-04-06
> **anjpr said:**
> There's two of us.  I have the same problem and get the same message.  For a while my wireless worked fine.  Nonetheless, after some updates I haven't been able to connect wireless.  I changed the wireless card to Atheros to avoid issues with nsdwrapper.  It didn't work.  Now what? It might be your network manager. check the attachment for the one that works. and the lspci command and the lsmod command are attached. Thanks

---

### Post by Whiffle on 2008-04-06
Try doing "modprobe ath_pci", and if that doesn't work, then you need to install the MadWifi drivers.

---

### Post by jose158 on 2008-04-06
I never needed madwifi before, Ubuntu connected to the internet right off the install. Is there some other way?

---

### Post by Whiffle on 2008-04-06
I suppose you could use ndiswrapper if you really wanted to, but madwifi would probably work better and should be available through the restricted drivers manager.  Your lspci output lists "Netgear Netgear WG311T Wireless PCI Adapter," which is listed on this page as working with madwifi: [http://madwifi.org/wiki/Compatibility/Netgear](http://madwifi.org/wiki/Compatibility/Netgear)

---

### Post by jose158 on 2008-04-06
Ok I'll try madwifi even thought I never had to use any driver. I will inform you if it works.

---

### Post by jose158 on 2008-04-06
Is there a .deb file for madwifi so I can just transfer that on to my flashdrive?

---

### Post by jose158 on 2008-04-07
I'm tired of trying to get this to work, I will get wired internet tomorrow, but  thanks anyway.:)

---

### Post by anjpr on 2008-04-08
**oficina@oficina-laptop:~$ lspci -v**

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d7ffffff
        Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0200000-d02fffff
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at d0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at d0002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: 66MHz, medium devsel
        I/O ports at 8400 [size=16]
        Memory at d0003000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8410 [size=16]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=05, subordinate=09, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0300000-d03fffff
        Prefetchable memory behind bridge: 50000000-53ffffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
        Subsystem: Gateway 2000 MX6421
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at d0003400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at d0003800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at d0200000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        Capabilities: <access denied>

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Broadcom Corporation Gateway 7510GX
        Flags: bus master, fast devsel, latency 64, IRQ 22
        Memory at d0304000 (32-bit, non-prefetchable) [size=8K]

05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at d030a000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at d0308000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0300000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d0306000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
        Subsystem: Gateway 2000 Unknown device 0300
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d0309000 (32-bit, non-prefetchable) [size=256]
        Memory at d0308c00 (32-bit, non-prefetchable) [size=256]
        Memory at d0308800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

**oficina@oficina-laptop:~$ lsmod**
Module                  Size  Used by
arc4                    2944  0 
ecb                     4608  0 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  0 
nfs                   246124  1 
lockd                  67592  2 nfs
sunrpc                172412  3 nfs,lockd
af_packet              24840  2 
binfmt_misc            12936  1 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
vboxdrv                60720  0 
ppdev                  10244  0 
ipv6                  273892  18 
powernow_k8            16960  0 
cpufreq_ondemand        9612  1 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
button                  8976  0 
video                  18060  0 
container               5504  0 
ac                      6148  0 
dock                   10656  0 
sbs                    19592  0 
battery                11012  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_atiixp             21132  1 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
pcmcia                 41388  0 
snd_atiixp_modem       17160  0 
snd_ac97_codec        100644  2 snd_atiixp,snd_atiixp_modem
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
psmouse                39952  0 
serio_raw               8068  0 
pcspkr                  4224  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
k8temp                  6656  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                80388  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              24324  2 snd_seq,snd_pcm
bcm43xx               127336  0 
usblp                  15104  0 
ipaq                   34584  0 
ieee80211softmac       31360  1 bcm43xx
sdhci                  18828  0 
usbserial              34920  1 ipaq
tifm_7xx1               8832  0 
tifm_core              11652  1 tifm_7xx1
snd                    54660  13 snd_atiixp,snd_seq_oss,snd_rawmidi,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_atiixp,snd_atiixp_modem,snd_pcm
sky2                   46852  0 
ieee80211              35656  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
mmc_core               28420  1 sdhci
i2c_piix4               9740  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               26112  1 i2c_piix4
ati_agp                10124  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  2 drm,ati_agp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  5 
usbhid                 29536  0 
hid                    28928  1 usbhid
atiixp                  7056  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,atiixp
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  2 sbp2,libata
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  7 usblp,ipaq,usbserial,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

