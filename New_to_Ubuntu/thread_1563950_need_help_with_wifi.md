---
title: "need help with wifi"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by k33bz on 2010-08-29
My wifes wireless card has completely failed, so I swapped that wifi card with a different one. The new one is a RealTek RTL8187SE. However it is not letting me see any networks.

All I did was swap out the wifi cards. Am I missing a step.

Thanks in advance

lspci

```
nana@VPena:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

lsmod

```
nana@VPena:~$ lsmod
Module                  Size  Used by
binfmt_misc             8444  1 
ppdev                   6808  0 
snd_hda_codec_realtek   203512  1 
snd_hda_intel          26760  2 
snd_hda_codec          76084  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7416  1 snd_hda_codec
snd_pcm_oss            38176  0 
snd_mixer_oss          16500  1 snd_pcm_oss
snd_pcm                74904  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2680  0 
snd_seq_oss            28768  0 
snd_seq_midi            6560  0 
snd_rawmidi            22336  1 snd_seq_midi
pcmcia                 35560  0 
snd_seq_midi_event      7092  2 snd_seq_oss,snd_seq_midi
snd_seq                50896  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  37184  71 
tileblit                2452  1 fbcon
font                    8116  1 fbcon
bitblit                 5236  1 fbcon
snd_timer              22040  2 snd_pcm,snd_seq
joydev                 10336  0 
softcursor              1748  1 bitblit
snd_seq_device          6880  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    60612  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_sd                 9244  0 
lp                      9508  0 
yenta_socket           24288  1 
tifm_7xx1               5300  0 
rsrc_nonstatic         11860  1 yenta_socket
soundcore               7968  1 snd
i915                  230184  4 
tifm_core               8080  2 tifm_sd,tifm_7xx1
pcmcia_core            37708  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                57452  0 
sony_laptop            32196  0 
serio_raw               5400  0 
snd_page_alloc          9180  2 snd_hda_intel,snd_pcm
rtl8187se             202128  0 
drm                   161184  4 i915
i2c_algo_bit            5784  1 i915
intel_agp              27676  2 i915
parport                36008  2 ppdev,lp
agpgart                35408  2 drm,intel_agp
video                  19340  1 i915
output                  2836  1 video
ohci1394               30308  0 
ieee1394               87284  1 ohci1394
sky2                   46552  0 

```

---

### Post by k33bz on 2010-08-29
can someone please help me with this

---

### Post by k33bz on 2010-08-29
can someone please help me with this


I just tried ndiswrapper, and after ```
sudo ndiswrapper -l
``` I get an invalid driver response

---

### Post by k33bz on 2010-08-29
as a note I just got it fixed, if anyone has problems with this in 10.04, make sure you are using gnome-network-manager

WICD will not work

---

### Post by zeroseven0183 on 2010-08-30
> **k33bz said:**
> as a note I just got it fixed, if anyone has problems with this in 10.04, make sure you are using gnome-network-manager

WICD will not work

Correction, that's **network-manager-gnome** :)

---

