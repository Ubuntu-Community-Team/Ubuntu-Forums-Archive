---
title: "D-Link DWA-140 not working in Ubuntu 18, help needed"
date: 2019-04-20
forum: Networking &amp; Wireless
---

### Post by caspaz on 2019-04-20
Hi,

I'm a beginner and using Ubuntu 18.04.2 LTS. 
I need help with my USB wireless adapter from D-Link, it doesn't work at all.

After lot of googling I think the driver for this adapter is rt2800usb, but it still doesn't work. Not even the led-light is working. I tested the wireless info script and the commands below, however I need help on how to proceed.

Product:
D-Link DWA-140
From the backside: 
HW Ver. D2.
FW Ver. 4.04.

Thanks in advance!

From the wireless info script:
[https://pastebin.com/AUdG1SYE](https://pastebin.com/AUdG1SYE)

lsusb:
```

Bus 002 Device 003: ID 05c8:011c Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 009: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 002 Device 008: ID 2001:3c20 D-Link Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 138a:0001 Validity Sensors, Inc. VFS101 Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

rfkill list:
```

0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
3: phy2: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```

---

### Post by jeremy31 on 2019-04-20
Please post results for ```
lsmod
```
What computer model?

---

### Post by caspaz on 2019-04-20
> **jeremy31 said:**
> Please post results for ```
lsmod
```
What computer model?

Hi!

It's a laptop, HP dv3000, still going strong!

lsmod:
```

Module                  Size  Used by
uas                    24576  0
usb_storage            69632  2 uas
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    73728  1 snd_hda_codec_idt
snd_hda_intel          40960  3
gpio_ich               16384  0
wmi_bmof               16384  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
snd_hda_codec         126976  3 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec_idt
snd_hda_core           81920  4 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec,snd_hda_codec_idt
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
nouveau              1851392  12
mxm_wmi                16384  1 nouveau
ttm                   110592  1 nouveau
snd_rawmidi            32768  1 snd_seq_midi
rt2800usb              32768  0
rt2x00usb              20480  1 rt2800usb
arc4                   16384  4
drm_kms_helper        172032  1 nouveau
iwldvm                229376  0
input_leds             16384  0
joydev                 24576  0
iwlwifi               299008  1 iwldvm
uvcvideo               94208  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  16 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_hda_codec_idt,snd_rawmidi
ir_rc6_decoder         16384  0
drm                   458752  7 drm_kms_helper,ttm,nouveau
rt2800lib             114688  1 rt2800usb
rt2x00lib              53248  3 rt2800usb,rt2x00usb,rt2800lib
mac80211              802816  4 iwldvm,rt2x00lib,rt2x00usb,rt2800lib
lpc_ich                24576  0
cfg80211              667648  4 iwldvm,rt2x00lib,iwlwifi,mac80211
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_common       40960  2 videobuf2_v4l2,uvcvideo
videodev              188416  3 videobuf2_v4l2,uvcvideo,videobuf2_common
media                  40960  2 videodev,uvcvideo
video                  45056  1 nouveau
rc_rc6_mce             16384  0
ite_cir                28672  0
rc_core                45056  4 ite_cir,ir_rc6_decoder,rc_rc6_mce
mac_hid                16384  0
i2c_algo_bit           16384  1 nouveau
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
soundcore              16384  1 snd
wmi                    24576  4 hp_wmi,wmi_bmof,mxm_wmi,nouveau
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
input_polldev          16384  1 lis3lv02d
sch_fq_codel           20480  2
coretemp               16384  0
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
psmouse               151552  0
r8169                  86016  0
ahci                   40960  3
libahci                32768  1 ahci
mii                    16384  1 r8169

```

---

### Post by jeremy31 on 2019-04-20
Does the wifi button above the keyboard change the results for ```
rfkill list
```

---

### Post by caspaz on 2019-04-20
> **jeremy31 said:**
> Does the wifi button above the keyboard change the results for ```
rfkill list
```

After the wifi-button I now have:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

I tried rfkill unblock all, so rfkill list:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``` 

Now the built-in wifi works, but no sign of the usb-wifi.

---

### Post by jeremy31 on 2019-04-20
See the wireless script link in my signature and post results

---

### Post by caspaz on 2019-04-20
> **jeremy31 said:**
> See the wireless script link in my signature and post results

Here you go: [https://pastebin.com/3Vs5PgFw](https://pastebin.com/3Vs5PgFw)

---

### Post by caspaz on 2019-04-21
> **jeremy31 said:**
> See the wireless script link in my signature and post results

> **caspaz said:**
> Here you go: [https://pastebin.com/3Vs5PgFw](https://pastebin.com/3Vs5PgFw)

Today rfkill list gives another result so I uploaded a new wireless info script: [https://pastebin.com/xVAwhSDS](https://pastebin.com/xVAwhSDS)

Here is rfkill list:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

```

Also, today the wifi-button doesn't work at all, so it doesn't change the result.
Using rfkill unblock all doesn't change anything so rfkill list gives the same output:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

```

---

