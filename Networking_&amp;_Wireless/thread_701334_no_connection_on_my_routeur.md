---
title: "no connection on my routeur"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by sdesrousseaux on 2008-02-19
hi
here is my problem: i see some wireless networks but i don't arrive to connect on mine network!

my config:

- iwlist scanning

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:16:41:F0:C1:AD
                    ESSID:"Livebox-e2eb"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=63/100  Signal level=-69 dBm  Noise level=-69 dBm
                    Extra: Last beacon: 10728ms ago
          Cell 02 - Address: 00:16:41:48:5D:66
                    ESSID:"Wanadoo_49c5"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-84 dBm  Noise level=-84 dBm
                    Extra: Last beacon: 8384ms ago
          Cell 03 - Address: 00:04:E2:AF:98:02
                    ESSID:"totoro"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-40 dBm  Noise level=-40 dBm
                    Extra: Last beacon: 10732ms ago
          Cell 04 - Address: 00:16:41:8C:9E:F9
                    ESSID:"Livebox-49a4"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=37/100  Signal level=-87 dBm  Noise level=-87 dBm
                    Extra: Last beacon: 10852ms ago
          Cell 05 - Address: 00:14:A5:9C:0D:9B
                    ESSID:"N9UF_TEL9COM"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-89 dBm  Noise level=-89 dBm
                    Extra: Last beacon: 168ms ago

pan0      Interface doesn't support scanning.

```

- lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

- lsmod
```
Module                  Size  Used by
bnep                   17408  2 
bridge                 56088  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
ipv6                  273892  10 
arc4                    2944  0 
ecb                     4608  0 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  0 
af_packet              24840  2 
rfcomm                 42136  4 
l2cap                  26240  14 bnep,rfcomm
sony_laptop            32088  0 
sonypi                 23960  0 
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  1 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
video                  18060  5 
button                  8976  0 
battery                11012  0 
dock                   10656  0 
container               5504  0 
sbs                    19592  0 
ac                      6148  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263840  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
uvcvideo               48644  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
compat_ioctl32          2304  1 uvcvideo
ipw3945               119840  1 
joydev                 11328  0 
nvidia               6221648  36 
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
sky2                   46852  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hci_usb                18332  2 
tifm_7xx1               8832  0 
tifm_core              11652  1 tifm_7xx1
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
i2c_core               26112  1 nvidia
pcmcia                 41388  0 
bluetooth              57060  8 bnep,rfcomm,l2cap,hci_usb
serio_raw               8068  0 
intel_agp              25620  0 
agpgart                35016  2 nvidia,intel_agp
psmouse                39952  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  8 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usb_storage            73024  1 
ide_core              116804  1 usb_storage
sg                     36764  0 
sd_mod                 30336  5 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
libusual               18448  1 usb_storage
ata_piix               17540  2 
ohci1394               36528  0 
ehci_hcd               36492  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 sbp2,usb_storage,sg,sd_mod,sr_mod,libata
uhci_hcd               26640  0 
usbcore               138632  7 uvcvideo,hci_usb,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

- sudo lshw -C network
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:32:37:d6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:fb:49:22
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.2.151 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

- dmesg | grep eth
```
[   12.640000] sky2 eth0: addr 00:13:a9:fb:49:22
[   17.108000] sky2 eth0: enabling interface
[  238.412000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  262.328000] eth0: no IPv6 routers present
[  357.280000] eth1: no IPv6 routers present
[  574.764000] sky2 eth0: Link is down.
[  583.412000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  584.840000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  595.440000] eth1: no IPv6 routers present
[  638.500000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  639.876000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  649.884000] eth1: no IPv6 routers present
[  802.948000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  804.344000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  814.524000] eth1: no IPv6 routers present
[  856.152000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  857.480000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  862.436000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  862.440000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  886.736000] eth0: no IPv6 routers present
[  897.904000] eth1: no IPv6 routers present

```

i hope someone can help me
thx
stephane in france

---

