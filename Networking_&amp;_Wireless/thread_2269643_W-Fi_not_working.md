---
title: "W-Fi not working"
date: 2015-03-16
forum: Networking &amp; Wireless
---

### Post by Anis_zighmi on 2015-03-16
i have the same probleme please helpme

```
anis@anis-Inspiron-1520:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G86M [GeForce 8400M GS] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
anis@anis-Inspiron-1520:~$ lsmod
Module                  Size  Used by
arc4                   12536  2 
rt73usb                26890  0 
rt2x00usb              20041  1 rt73usb
rt2x00lib              48886  2 rt73usb,rt2x00usb
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
nouveau               969577  3 
snd_hda_codec_idt      48978  1 
snd_hda_intel          42794  3 
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
b43                   356470  0 
snd_hwdep              13272  1 snd_hda_codec
mxm_wmi                12893  1 nouveau
ttm                    80983  1 nouveau
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
coretemp               13195  0 
drm_kms_helper         48868  1 nouveau
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
gpio_ich               13229  0 
dell_wmi               12665  0 
bcma                   42043  1 b43
r852                   17722  0 
mac80211              546067  3 b43,rt2x00lib,rt2x00usb
snd_seq_midi           13132  0 
sparse_keymap          13708  1 dell_wmi
drm                   244037  5 ttm,drm_kms_helper,nouveau
sm_common              16772  1 r852
snd_seq_midi_event     14475  1 snd_seq_midi
nand                   58760  2 r852,sm_common
snd_rawmidi            25135  1 snd_seq_midi
i2c_algo_bit           13197  1 nouveau
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
kvm                   388310  0 
nand_ecc               13136  1 nand
cfg80211              409394  3 b43,mac80211,rt2x00lib
nand_bch               13067  1 nand
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
bch                    17197  1 nand_bch
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
nand_ids                8547  1 nand
snd_timer              28584  2 snd_pcm,snd_seq
mtd                    52813  2 nand,sm_common
joydev                 17101  0 
ssb_hcd                12749  0 
snd                    60939  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
r592                   17711  0 
serio_raw              13230  0 
memstick               16174  1 r592
soundcore              12600  1 snd
lpc_ich                16864  0 
wmi                    18673  3 dell_wmi,mxm_wmi,nouveau
mac_hid                13037  0 
shpchp                 32128  0 
video                  18903  1 nouveau
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
b44                    31275  0 
firewire_ohci          35529  0 
psmouse                91357  0 
sdhci_pci              18535  0 
mii                    13654  1 b44
sdhci                  37779  1 sdhci_pci
firewire_core          61867  1 firewire_ohci
ssb                    51854  3 b43,b44,ssb_hcd
pata_acpi              12886  0 
crc_itu_t              12627  2 rt73usb,firewire_core
anis@anis-Inspiron-1520:~$ rfkill list
0: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by Anis_zighmi on 2015-03-16
when i star my computer it tells me that b43  is not found and when i tried to use the b43.zip by extracting on desktop and by using the line code to copy it to lib/frimwear/b43 , it tells me acces refused !!!! i am administrator of my pc , the only user , how could i fix it  .???

---

### Post by slickymaster on 2015-03-17
Moved to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by kerry_s on 2015-03-17
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by coffeecat on 2015-03-17
> **kerry_s said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

There's also the somewhat easier-to-follow Broadcom sticky from chili555 here:

[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

