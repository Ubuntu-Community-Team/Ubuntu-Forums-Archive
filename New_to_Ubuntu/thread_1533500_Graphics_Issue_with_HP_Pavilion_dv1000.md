---
title: "Graphics Issue with HP Pavilion dv1000"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by welshpudding on 2010-07-18
I've installed Ubuntu 10.4 on a HP Pavilion dv1000, unfortunately when it tries to boot it dies on the Ubuntu loading screen in a manner symptomatic of a graphics error. Sure enough, on booting up in graphics fail safe mode it works, albeit with the lowest possible graphics settings. 

After trawling the web for drivers I can't seem to find anything for this distro and machine... this is pretty annoying as I'd just like to use this laptop as a little web, file & media sever at home as it's not really that good for much else. I can only boot it in low graphics mode at present is which probably isn't the best practice.

Any suggestions?

---

### Post by jtarin on 2010-07-18
> **welshpudding said:**
> I've installed Ubuntu 10.4 on a HP Pavilion dv1000, unfortunately when it tries to boot it dies on the Ubuntu loading screen in a manner symptomatic of a graphics error. Sure enough, on booting up in graphics fail safe mode it works, albeit with the lowest possible graphics settings. 

After trawling the web for drivers I can't seem to find anything for this distro and machine... this is pretty annoying as I'd just like to use this laptop as a little web, file & media sever at home as it's not really that good for much else. I can only boot it in low graphics mode at present is which probably isn't the best practice.

Any suggestions?
In a terminal enter and post the results here of```
lspci
``` 
In a terminal enter and post the results here of```
lsmod
```

---

### Post by welshpudding on 2010-07-18
lspci result:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

lsmod result:

Module                  Size  Used by
rfcomm                 33421  4 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
nls_utf8                1069  1 
udf                    78785  1 
crc_itu_t               1371  1 udf
aes_i586                7268  2 
aes_generic            26863  1 aes_i586
lib80211_crypt_ccmp     4369  2 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
pcmcia                 33024  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sdhci_pci               5470  0 
snd_timer              19098  2 snd_pcm,snd_seq
yenta_socket           20408  1 
joydev                  8708  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rsrc_nonstatic         10015  1 yenta_socket
vga16fb                11385  1 
sdhci                  15462  1 sdhci_pci
tifm_7xx1               3690  0 
ipw2200               135216  0 
vgastate                8961  1 vga16fb
led_class               2864  1 sdhci
tifm_core               6045  1 tifm_7xx1
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
libipw                 39896  1 ipw2200
psmouse                63245  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                5046  3 lib80211_crypt_ccmp,ipw2200,libipw
i915                  285076  0 
drm_kms_helper         29297  1 i915
btusb                  10925  2 
drm                   162377  2 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24119  2 i915
serio_raw               3978  0 
video                  17375  1 i915
soundcore               6620  1 snd
lp                      7028  0 
shpchp                 28820  0 
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
bluetooth              49892  12 rfcomm,sco,bnep,l2cap,btusb
output                  1871  1 video
parport                32635  1 lp
ohci1394               26950  0 
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
ieee1394               81181  1 ohci1394

---

### Post by jtarin on 2010-07-18
You list: Display controller: Intel Corporation [82852/855GM ]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")Integrated Graphics Device

---

