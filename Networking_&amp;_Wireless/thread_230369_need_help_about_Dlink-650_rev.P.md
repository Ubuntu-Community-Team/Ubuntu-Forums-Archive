---
title: "need help about Dlink-650 rev.P"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by zjcim on 2006-08-05
After plug the card,
```
joey@ubuntu:/usr/src$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
0000:02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
0000:02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

```
ubuntu recognize the card ,but cann't make it work

```
joey@ubuntu:~/linux-wlan-ng-0.2.3$ sudo lshw -C network
  *-network
       description: DWL-650 Wireless PC Card RevP
       product: ISL37101P-10
       vendor: D-Link
       physical id: 0
       version: A3
       slot: Socket 0
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:d0:59:cb:db:b3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=full firmware=N/A ip=192.168.1.36 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:c0200000-c0200fff ioport:7000-703f irq:11

```

dose the card use the this driver:
```
lsmod | grep ori
```
*and get nothing*

[B]joey@ubuntu:~/linux-wlan-ng-0.2.3$ lsmod
Module                  Size  Used by
sg                     37920  0
acpi_sbs               19980  0
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
ibm_acpi               26112  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
button                  6672  0
e100                   40580  0
mii                     5888  1 e100
prism2_cs              76244  0
tc1100_wmi              6916  0
video                  16260  0
container               4608  0
pcc_acpi               12416  0
sony_acpi               5644  0
dev_acpi               11140  0
hotkey                 11556  0
ipv6                  265728  24
nls_iso8859_1           4224  3
nls_cp437               5888  3
vfat                   13440  3
fat                    53020  1 vfat
dm_mod                 58936  1
atyfb                  43428  0
radeon                116768  0
drm                    75672  1 radeon
sr_mod                 16932  0
cdrom                  38560  1 sr_mod
sbp2                   24196  0
scsi_mod              139496  3 sg,sr_mod,sbp2
lp                     11844  0
irtty_sir               8576  0
sir_dev                19628  1 irtty_sir
nsc_ircc               23948  0
irda                  187068  3 irtty_sir,sir_dev,nsc_ircc
crc_ccitt               2304  1 irda
pcmcia                 40508  1 prism2_cs
parport_pc             35780  1
parport                36296  2 lp,parport_pc
floppy                 62148  0
psmouse                36100  0
serio_raw               7300  0
rtc                    13492  0
pcspkr                  2180  0
snd_intel8x0           33692  5
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
yenta_socket           28428  4
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
hw_random               5652  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  2 drm,intel_agp
tsdev                   8000  0
evdev                   9856  1
reiserfs              268016  2
usbhid                 39904  0
ide_generic             1536  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
uhci_hcd               33680  0
usbcore               130692  3 usbhid,uhci_hcd
ide_disk               17664  7
piix                   11012  1
generic                 5124  0
fbcon                  42784  0
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
capability              5000  0
commoncap               7296  1 capability[/B]

---

