---
title: "Ubuntu 18.04 LTS usb wifi dongle freeze"
date: 2019-05-07
forum: Networking &amp; Wireless
---

### Post by neset94 on 2019-05-07
Whenever I connect to WiFi using my usb wifi dongle (TP-Link TL-WN725N) the computer freezes and I have to force reboot. If I share my iPhone internet connecting with WiFi and connect my computer to it with the usb wifi it works almost perfect, but the system sometimes still completely freezes and I have to force reboot.

Just started using Linux yesterday so I'm still learning all the terminal stuff but here is some info: 

~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 04ca:002f Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 045e:07fd Microsoft Corp. Nano Transceiver 1.1
Bus 001 Device 004: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

If I need to give more info please let me know and please let me know how to get that info because like I said this is my 2nd day using linux. Coming from windows.

to make it clear:
1. When usb wifi dongle is connected to pc and network is turned OFF pc works fine but of course no internet.

2. when usb wifi dongle is connected to pc and I try to connect to home wifi computer freezes.

3. when usb wifi dongle is connected to pc and I try to connect to iPhone internet sharing it connects and internet works on pc.

---

### Post by praseodym on 2019-05-07
Lets see
```

lsmod
```
when plugged, but not connected. Any other device present?
```

lspci -nnk
```

---

### Post by neset94 on 2019-05-07
~$ lsmod
Module                  Size  Used by
r8188eu               413696  0
lib80211               16384  1 r8188eu
cfg80211              667648  1 r8188eu
ipheth                 16384  0
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     49152  1
nvidia_uvm            757760  0
nvidia_drm             40960  2
nvidia_modeset       1048576  11 nvidia_drm
eeepc_wmi              16384  0
nvidia              14376960  448 nvidia_uvm,nvidia_modeset
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  45056  1 asus_wmi
edac_mce_amd           28672  0
snd_hda_codec_realtek   106496  1
wmi_bmof               16384  0
kvm                   626688  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
irqbypass              16384  1 kvm
snd_hda_intel          40960  8
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
ghash_clmulni_intel    16384  0
snd_seq_midi           16384  0
pcbc                   16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
aesni_intel           200704  0
aes_x86_64             20480  1 aesni_intel
snd_rawmidi            32768  1 snd_seq_midi
crypto_simd            16384  1 aesni_intel
drm_kms_helper        172032  1 nvidia_drm
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
glue_helper            16384  1 aesni_intel
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
drm                   458752  5 drm_kms_helper,nvidia_drm
ipmi_devintf           20480  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
ipmi_msghandler       102400  2 ipmi_devintf,nvidia
joydev                 24576  0
snd_timer              32768  2 snd_seq,snd_pcm
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
snd                    81920  27 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
input_leds             16384  0
sysimgblt              16384  1 drm_kms_helper
soundcore              16384  1 snd
k10temp                16384  0
ccp                    86016  0
mac_hid                16384  0
wmi                    24576  2 asus_wmi,wmi_bmof
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   122880  2 usbhid,hid_generic
r8169                  86016  0
ahci                   40960  2
i2c_piix4              24576  0
mii                    16384  1 r8169
libahci                32768  1 ahci
gpio_amdpt             16384  0
gpio_generic           20480  1 gpio_amdpt

---

### Post by neset94 on 2019-05-07
> **praseodym said:**
> Lets see
```

lsmod
```
when plugged, but not connected. Any other device present?
```

lspci -nnk
```

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:8677]
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by praseodym on 2019-05-07
[https://github.com/lwfinger/rtl8188eu](https://github.com/lwfinger/rtl8188eu)

Try this repo

---

