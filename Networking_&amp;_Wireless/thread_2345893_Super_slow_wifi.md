---
title: "Super slow wifi"
date: 2016-12-08
forum: Networking &amp; Wireless
---

### Post by gjm07 on 2016-12-08
Hello guys, 

I am very new to Ubuntu. but i notice my wireless speed is very slow. 0.50 mbs.

I have searched and tried everything, no luck .  Can you guys please help?  Thank you in advance. 



```
lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7693]
    Kernel driver in use: r8169
    Kernel modules: r8169

Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  2
ccm                    20480  2
rtl8xxxu               73728  0
arc4                   16384  2
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              737280  4 rtl8xxxu,rtl_usb,rtlwifi,rtl8192cu
cfg80211              565248  2 mac80211,rtlwifi
joydev                 20480  0
input_leds             16384  0
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
kvm_amd                65536  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
kvm                   536576  1 kvm_amd
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
irqbypass              16384  1 kvm
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
crct10dif_pclmul       16384  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
crc32_pclmul           16384  0
aesni_intel           167936  4
aes_x86_64             20480  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
8250_fintek            16384  0
snd_timer              32768  2 snd_pcm,snd_seq
ablk_helper            16384  1 aesni_intel
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
soundcore              16384  1 snd
shpchp                 36864  0
fam15h_power           16384  0
edac_mce_amd           24576  0
i2c_piix4              24576  0
tpm_infineon           20480  0
edac_core              53248  0
k10temp                16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
nouveau              1495040  7
psmouse               126976  0
mxm_wmi                16384  1 nouveau
video                  40960  1 nouveau
i2c_algo_bit           16384  1 nouveau
ttm                    94208  1 nouveau
r8169                  81920  0
mii                    16384  1 r8169
drm_kms_helper        147456  1 nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  10 ttm,drm_kms_helper,nouveau
ahci                   36864  3
libahci                32768  1 ahci
fjes                   28672  0
wmi                    20480  2 mxm_wmi,nouveau
```

---

### Post by wildmanne39 on 2016-12-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

