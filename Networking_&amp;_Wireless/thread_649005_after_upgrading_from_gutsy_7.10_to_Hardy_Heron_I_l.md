---
title: "after upgrading from gutsy 7.10 to Hardy Heron I lost my wireless connection"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by raminv2 on 2007-12-24
in version 7.10 Wireless worked flawlessly using NDISWRAPPER. after upgrade I could see the wireless net work but was not able to connect, only one little green dot and one gray dot with blue ribbon circling. 
I re-installed using the 8.04 cd but now I can't connect or see the network at all. I also tried compiling madwifi 0.9.3.3 without success. I can go back to gutsy and am able to connect perfectly...here are some of my configuration info:

lshw:
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8039 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 14
                serial: 00:1a:80:1a:dc:0c
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.118 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0

dmseg  grep | grep -i wifi

[   32.638829] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

dmseg:

[   32.373232] pcmcia: parent PCI bridge Memory window: 0xfc200000 - 0xfc2fffff
[   32.404284] input: Sony Vaio Jogdial as /devices/virtual/input/input10
[   32.549995] wlan: 0.8.4.2 (0.9.3.3)
[   32.590225] ath_pci: 0.9.4.5 (0.9.3.3)
[   32.590328] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18

lsmod:

Module                  Size  Used by
ipv6                  311976  10 
i915                   30336  2 
drm                   104744  3 i915
af_packet              27272  2 
rfcomm                 47392  2 
l2cap                  28800  11 rfcomm
bluetooth              66436  4 rfcomm,l2cap
ppdev                  11400  0 
acpi_cpufreq           10832  2 
cpufreq_powersave       3200  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  1 
cpufreq_stats           8416  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       6180  0 
container               6656  0 
dock                   12960  0 
sbs                    17808  0 
sbshc                   8832  1 sbs
ndiswrapper           233664  0 
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
pcmcia                 45976  0 
snd_hda_intel         379432  3 
snd_pcm_oss            47488  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5508  0 
snd_seq_oss            36736  0 
snd_seq_midi           10880  0 
snd_rawmidi            29824  1 snd_seq_midi
sky2                   53508  0 
ath_pci               105392  0 
wlan                  225864  1 ath_pci
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
ath_hal               219888  1 ath_pci
snd_seq                62112  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27400  2 snd_pcm,snd_seq
snd_seq_device         10388  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sony_laptop            40368  0 
video                  23316  0 
output                  5632  1 video
battery                16648  0 
yenta_socket           30092  1 
rsrc_nonstatic         14080  1 yenta_socket
snd                    69416  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_7xx1               9984  0 
pcmcia_core            46116  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                46108  0 
soundcore              10400  1 snd
tifm_core              13064  1 tifm_7xx1
ac                      8328  0 
power_supply           13576  3 sbs,battery,ac
button                 10912  0 
pcspkr                  4736  0 
iTCO_wdt               15312  0 
iTCO_vendor_support     5764  1 iTCO_wdt
evdev                  14976  7 
serio_raw               9092  0 
intel_agp              30496  1 
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
pata_acpi               9856  0 
ata_generic             9988  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sd_mod                 33280  3 
usbhid                 35168  0 
hid                    44608  1 usbhid
ata_piix               23556  0 
ahci                   33028  2 
ohci1394               36532  0 
libata                173616  4 pata_acpi,ata_generic,ata_piix,ahci
scsi_mod              178360  5 sbp2,sr_mod,sg,sd_mod,libata
ieee1394              106968  2 sbp2,ohci1394
ehci_hcd               40972  0 
uhci_hcd               29856  0 
usbcore               169520  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                19744  0 
processor              41192  4 acpi_cpufreq,thermal
fan                     6536  0 
fuse                   56112  1

Please HELP

---

### Post by Perpetual on 2007-12-24
See if a [bug report]("http://ubuntuforums.org/showthread.php?t=284595") exists and if not file one as developers are not likely to see this posted on user forums.

---

### Post by raminv2 on 2007-12-24
Thanks,
I did report the bug, as of now I'm using the gutsy kernel and hope that it will be fixed. thanks...

---

