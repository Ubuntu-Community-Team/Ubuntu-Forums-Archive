---
title: "OpenGL/3D programs not working!"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by eskmsaul on 2010-12-26
Recently, all programs that use OpenGL (gltron, Mupen64, etc.) fail to work on my computer. They worked fine a week ago.... I'm running 10.04 on a Sony Vaio laptop. Actually, any 3d program fails to load. They all worked fine a week ago...help!

---

### Post by sandyd on 2010-12-26
> **eskmsaul said:**
> Recently, all programs that use OpenGL (gltron, Mupen64, etc.) fail to work on my computer. They worked fine a week ago.... I'm running 10.04 on a Sony Vaio laptop. Actually, any 3d program fails to load. They all worked fine a week ago...help!
post output of
```

lsmod
glxinfo
lspci
```

---

### Post by isoscelesrectangle on 2010-12-26
Hi. What video card are you using? Have you installed the appropriate drivers?

---

### Post by eskmsaul on 2010-12-26
saul@saul-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
arc4                    1153  2 
lib80211_crypt_wep      2667  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203344  1 
snd_hda_intel          22005  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
fbcon                  35102  71 
tileblit                2031  1 fbcon
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
i915                  287458  2 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
drm_kms_helper         29329  1 i915
joydev                  8740  0 
ipw2200               135216  0 
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 30784  0 
drm                   162409  3 i915,drm_kms_helper
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
libipw                 39896  1 ipw2200
psmouse                63245  0 
snd                    54180  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
intel_agp              24375  2 i915
lib80211                5046  3 lib80211_crypt_wep,ipw2200,libipw
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
serio_raw               3978  0 
sony_laptop            28248  0 
yenta_socket           20408  1 
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
rsrc_nonstatic         10015  1 yenta_socket
tifm_sd                 7863  0 
tifm_7xx1               3690  0 
output                  1871  1 video
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_core               6045  2 tifm_sd,tifm_7xx1
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
e100                   28211  0 
ieee1394               81181  1 ohci1394
mii                     4381  1 e100
saul@saul-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault
saul@saul-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

---

### Post by eskmsaul on 2010-12-26
I have no idea what drivers were installed, they were all working fine for months.

---

### Post by eskmsaul on 2010-12-26
> **sandyd said:**
> post output of
```

lsmod
glxinfo
lspci
```

Posted^

---

### Post by jtarin on 2010-12-26
Maybe look at your changelog and try to figure out what was upgraded and borked your install.

[http://manpages.ubuntu.com/manpages/jaunty/man1/apt-listchanges.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/apt-listchanges.1.html)

---

### Post by sandyd on 2010-12-27
ur glx isnt running properly
```

[B]saul@saul-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault[/B] 

```

your using the i915 drivers.

unfortunately, i don't use intel, so your going to have to wait.

---

### Post by eskmsaul on 2010-12-27
Alrighty.....I tried to install Nvidia drivers but I still get the same result....

---

### Post by eskmsaul on 2010-12-27
In fact, it's not even recognizing them..

---

### Post by rockerphil on 2010-12-27
the first thing that pops in to mind is to go to System>Administration>Hardware Drivers and try uninstalling then reinstalling the driver you're using, maybe it'll work, maybe it won't, but it's worth a shot. hope this helps,

Phil

---

### Post by eskmsaul on 2010-12-27
I tried that; no drivers showed up...

---

