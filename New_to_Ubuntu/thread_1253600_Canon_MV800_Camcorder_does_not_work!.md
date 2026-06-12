---
title: "Canon MV800 Camcorder does not work!"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by inzy123 on 2009-08-30
I've been trying to get a Canon MV800 camcorder to work via firewire (1394), but no luck! Ubuntu does not recognize it or more precisely the camcorder does not mount.

Any suggestion??  

Below is my configs

```
 $ lsmod
Module                  Size  Used by
dv1394                 25948  0 
raw1394                32732  0 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
i915                   67844  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18496  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  3 
arc4                    9856  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
ecb                    10752  2 
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
iwl3945                84100  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
iwlcore               112768  1 iwl3945
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
lbm_cw_mac80211       227492  2 iwl3945,iwlcore
psmouse                61972  0 
intel_agp              34108  1 
lbm_cw_cfg80211        73888  3 iwl3945,iwlcore,lbm_cw_mac80211
dcdbas                 15264  0 
serio_raw              13444  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
ricoh_mmc              11904  0 
agpgart                42696  3 drm,intel_agp
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
btusb                  19608  2 
led_class              12036  2 iwl3945,iwlcore
usblp                  20224  0 
video                  25360  0 
output                 11008  1 video
usbhid                 42336  0 
usb_storage            99648  1 
ohci1394               38576  1 dv1394
b44                    35472  0 
ssb                    53128  1 b44
ieee1394               94660  3 dv1394,raw1394,ohci1394
pcmcia                 44748  1 ssb
pcmcia_core            43540  2 ssb,pcmcia
mii                    13312  1 b44
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
``````
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by cariboo on 2009-08-30
Have a look at this [page]("https://help.ubuntu.com/community/Firewire"), it helped me get my Sony camcorder connected properly.

---

