---
title: "Wireless LAN Realtek RTL8191SEvB Hard Blocked on Restart.  Ubuntu 16.04."
date: 2017-08-29
forum: Networking &amp; Wireless
---

### Post by frugabruger on 2017-08-29
My wireless card changes to hard blocked automatically.  My wireless card does work, if I enter the bios, disable the card, login, restart, enter the bios, and turn the card back on.  It will work until I restart or suspend the system.  Then back to hard blocked.  Wireless info is attached.  This is now a clean install with updates because I tried so many things I was lost.  System is a 
Toshiba Satellite l505d-gs6000.
 
```

frugabruger@frugabruger-Satellite-L505D:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

Function and F8 change soft block.

```
frugabruger@frugabruger-Satellite-L505D:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
```

toshiba satellite l505d-gs6000

```
frugabruger@frugabruger-Satellite-L505D:~$ sudo lshw -c network
  *-network DISABLED      
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 10
       serial: 00:26:b6:d6:69:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=4.4.0-93-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:7000(size=256) memory:f2100000-f2103fff
```

---

### Post by praseodym on 2017-08-31
Please show

```
lsmod
```
completely

---

### Post by frugabruger on 2017-08-31
Here ya go.

```
frugabruger@frugabruger-Satellite-L505D:~$ lsmod
Module                  Size  Used by
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
kvm_amd                65536  0
kvm                   544768  1 kvm_amd
irqbypass              16384  1 kvm
arc4                   16384  2
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1
snd_hda_intel          40960  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
input_leds             16384  0
joydev                 20480  0
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
rtl8192se              65536  0
serio_raw              16384  0
rtl_pci                28672  1 rtl8192se
snd_hwdep              16384  1 snd_hda_codec
k10temp                16384  0
rtlwifi                77824  2 rtl_pci,rtl8192se
mac80211              737280  3 rtl_pci,rtlwifi,rtl8192se
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
cfg80211              565248  2 mac80211,rtlwifi
edac_mce_amd           24576  0
edac_core              53248  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
i2c_piix4              24576  0
toshiba_acpi           40960  0
shpchp                 36864  0
sparse_keymap          16384  1 toshiba_acpi
wmi                    20480  1 toshiba_acpi
toshiba_bluetooth      16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
amdkfd                131072  1
amd_iommu_v2           20480  1 amdkfd
radeon               1515520  8
i2c_algo_bit           16384  1 radeon
ttm                    98304  1 radeon
drm_kms_helper        155648  1 radeon
syscopyarea            16384  1 drm_kms_helper
psmouse               131072  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  2
drm                   364544  11 ttm,drm_kms_helper,radeon
libahci                32768  1 ahci
r8169                  81920  0
mii                    16384  1 r8169
video                  40960  1 toshiba_acpi
fjes                   28672  0
```

---

### Post by praseodym on 2017-08-31
&#7808;hat about resetting your BIOS to default settings?

---

### Post by frugabruger on 2017-08-31
Just tried.  Same result.

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

---

### Post by praseodym on 2017-09-02
Try when hard blocked
```

sudo rmmod toshiba_acpi
```

---

