---
title: "Do I need a driver or different OS?"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by trus-rod on 2010-08-01
I have Ubuntu Studio 64 bit on a shuttle SK21G.  Just upgraded to 10.4.  Every thing seemed fine till I went preferences/screen saver and clicked on the spotlight ant.  now the mouse freezes constantly, it will seem OK, the curser moves around fine, till I scroll, or click, then it freezes for 30 seconds to a minute.  

Also, grafics seem screwed up, like the colors in blender. I can't read anything on the tool bar.  Its like set at 256 colors instead of 16 bit.  

Thank god this computer is old enough to have a reset button

---

### Post by jtarin on 2010-08-01
Video card is???

---

### Post by trus-rod on 2010-08-01
No video card just the onboard video.

---

### Post by jtarin on 2010-08-01
Chip number/name? Issue in a terminal the command ```
lspci
``` and post.
I assume you turned off the screensaver?

---

### Post by trus-rod on 2010-08-01
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0b.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

---

### Post by jtarin on 2010-08-02
OK....you have very common chip/card. Post the results of the command ```
lsmod
``` If the incorrect driver is loaded then use Synaptic and make sure you have the  "xserver-xorg-video-openchrome" pkg installed. This not a 3D chip.

[OpenChrome Documentation]("http://www.openchrome.org/trac/wiki/Installation")

---

### Post by trus-rod on 2010-08-02
Module                  Size  Used by
isofs                  36456  1 
udf                    88808  0 
crc_itu_t               2320  1 udf
via                    45056  2 
drm                   196064  3 via
binfmt_misc            10300  1 
tuner_simple           16596  1 
tuner_types            18480  1 tuner_simple
snd_via82xx            28444  2 
gameport               14400  1 snd_via82xx
snd_ac97_codec        125848  1 snd_via82xx
ac97_bus                2160  1 snd_ac97_codec
snd_pcm_oss            44928  0 
snd_mixer_oss          19664  1 snd_pcm_oss
tea5767                 7636  0 
snd_pcm                91704  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
tuner                  24648  1 
snd_page_alloc         11008  2 snd_via82xx,snd_pcm
snd_mpu401_uart         8720  1 snd_via82xx
snd_seq_dummy           3540  0 
snd_seq_oss            33856  0 
snd_seq_midi            8448  0 
snd_rawmidi            27296  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8688  2 snd_seq_oss,snd_seq_midi
cx8800                 37092  0 
snd_seq                61664  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cx88xx                 86476  1 cx8800
ir_common              52724  1 cx88xx
ppdev                   8504  0 
snd_timer              26872  2 snd_pcm,snd_seq
i2c_algo_bit            7060  1 cx88xx
snd_seq_device          8388  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tveeprom               14868  1 cx88xx
amd64_edac_mod         26944  0 
psmouse                58100  0 
v4l2_common            21392  3 tuner,cx8800,cx88xx
serio_raw               6772  0 
edac_core              49884  1 amd64_edac_mod
k8temp                  5648  0 
snd                    79240  16 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             37320  1 
videodev               43968  4 tuner,cx8800,cx88xx,v4l2_common
v4l1_compat            17076  1 videodev
v4l2_compat_ioctl32    11792  1 videodev
videobuf_dma_sg        14580  2 cx8800,cx88xx
videobuf_core          21556  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc               5656  2 cx8800,cx88xx
soundcore              10080  1 snd
i2c_viapro              8840  0 
shpchp                 38220  0 
lp                     12644  0 
parport                41548  3 ppdev,parport_pc,lp
ohci1394               34564  0 
via_rhine              26040  0 
mii                     6384  1 via_rhine
ieee1394              101984  1 ohci1394
sata_via               12020  2 
floppy                 66024  0

---

### Post by jtarin on 2010-08-02
You need to look at the documentation on the link I gave you and make sure everything that needs to be upgraded....is.

[Also for Ubuntu specific ]("https://help.ubuntu.com/community/BinaryDriverHowto")

---

### Post by trus-rod on 2010-08-02
Thanks jtarin, I'm calling it a night, and work some more on it tomorrow.

So do I need a grafics card to work in blender?  This machine didn't have a problem with it in windows.

---

### Post by jtarin on 2010-08-02
> **trus-rod said:**
> Thanks jtarin, I'm calling it a night, and work some more on it tomorrow.

So do I need a grafics card to work in blender?  This machine didn't have a problem with it in windows.You need a graphics card and/or a chip to run any applications in X.We just need to determine yours and what did not upgrade when you did your upgrade.

---

### Post by trus-rod on 2010-08-06
Well, it appears i have the km800 chip.  Openchrome is alive and well.  I guess my onboard grafics just suck that bad.  when I do the system test, the 3d with the gears, the fans spin up and I feel like I have to hold the machine to keep it from hovering.  

I was hoping linux would improve things, but on this machine, its worse than windoze.  Even the stock charts on google finance sputter the mouse.  Can anyone recomend a card for the an AGP slot, preferably cheap from ebay that might help?

---

