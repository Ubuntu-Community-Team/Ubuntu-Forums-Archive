---
title: "Unable to make rt7610 wifi driver on any linux system"
date: 2019-07-15
forum: Networking &amp; Wireless
---

### Post by willtryanything on 2019-07-15
Have tried several install of OS but cannot get past the make to build the driver, due to Unexpected indentation and wrong integer errors, see pastebin, same usernam, cannot make driver, ever.. Live cd of Mint would not even load due to code below, and exit on ubuntu shows this code: 
[[ 1315.233442]("tel:1315233442")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: RX urb failed:-1
[[ 1315.233690]("tel:1315233690")] mt[7601]("tel:7601")u 1-1.3:1.0: Error: MCU resp urb failed:-71
[1315]("tel:1315").[2337601]("tel:2337601") mt [7601]("tel:7601")u 1-1.3:1.0: Error: MCU resp evt:0 seq:5-4!
[[ 1315.233844]("tel:1315233844")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: mt [7601]("tel:7601")u_mcu_wait resp timed out
[1315.404857]("tel:1315404857")] mt[7601]("tel:7601")u 1-1.3:1.0: Vendor request req:07 off:0080 failed: -71
[[ 1315]("tel:1315").[5688571]("tel:5688571") mt [7601]("tel:7601")u 1-1.3:1.0: Vendor request req:02 off:0080 failed:-71
[1315.732858]("tel:1315732858")] mt [7601]("tel:7601")u 1-1.3:1.0: Vendor request reg:02 off:0080 failed:-71
[[ 1316.848807]("tel:1316848807")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: RX urb failed:-71
[1316.848923]("tel:1316848923")] mt[7601]("tel:7601")u 1-1.3:1.0: Error: MCU resp urb failed:-71
[1316.848994]("tel:1316848994")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: MCU resp evt:0 seq:5-4!
[[ 1316.853055]("tel:1316853055")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: RX urb failed:-71
[1316.853303]("tel:1316853303")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: MCU resp urb failed:-71
[1316.853373]("tel:1316853373")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: MCU resp evt:0 seq:5-4!
[[1316.857306]("tel:1316857306")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: RX urb failed:-71
[[ 1316.857561]("tel:1316857561")] mt[7601]("tel:7601")u 1-1.3:1.0: Error: MCU resp urb failed:-71
[[ 1316.857633]("tel:1316857633")] mt [7601]("tel:7601")u 1-1.3:1.0 Error: MCU resp evt:0 seq:5-4!
[[ 1316.861555]("tel:1316861555")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: RX urb failed:-71
[[ 1316.861803]("tel:1316861803")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: MCU resp urb failed:-71
[[ 1316.861875]("tel:1316861875")] mt[7601]("tel:7601")u 1-1.3:1.0: Error: MCU resp evt:0 sec
[[ 1316.865807]("tel:1316865807")] mt[7601]("tel:7601")u 1-1.3:1.0: Error: RX urb failed:-71
[[ 1316.866053]("tel:1316866053")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: MCU resp urb failed:-71
[1316.866124]("tel:1316866124")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: MCU resp evt:0 seq:5-4!
[1316.866209]("tel:1316866209")] mt [7601]("tel:7601")u 1-1.3:1.0: Error: mt[7601]("tel:7601")u_mcu_wait resp timed out
[1317.044857]("tel:1317044857")) mt [7601]("tel:7601")u 1-1.3:1.0: Vendor request req:07 off:0080 failed:-71
obviously related to the wifi driver, have two dongles with the same driver chipset and neither function.
Some help would be appreciated, this is my first real entrance into linux, but no wifi is a game killer.
Thanks in advance.

---

### Post by praseodym on 2019-07-15
Which system? Which kernel? That driver is supported starting with the mainline kernel 4.3. Please show the outputs of
```

uname -a
lsusb
lsmod
```
Which driver did you try?

---

### Post by willtryanything on 2019-07-15
Heres my system   uname -a  5.0.0-20-generic #21-Ubuntu SMP Mon Jun 24 09:32:09 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Output from command line, the dongle is detected with lsusb
Bus 002 Device 006: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 002 Device 005: ID 413c:2107 Dell Computer Corp. 
Bus 002 Device 004: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and lsmod  gives 
Module                  Size  Used by
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek   114688  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_intel          40960  4
intel_rapl             24576  0
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           86016  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
mt7601u               102400  0
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
coretemp               20480  0
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
kvm_intel             241664  0
kvm                   626688  1 kvm_intel
mac80211              806912  1 mt7601u
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
cfg80211              671744  2 mt7601u,mac80211
irqbypass              16384  1 kvm
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
snd_timer              36864  2 snd_seq,snd_pcm
ghash_clmulni_intel    16384  0
mei_me                 40960  0
mei                   102400  1 mei_me
snd                    81920  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
aesni_intel           372736  0
aes_x86_64             20480  1 aesni_intel
soundcore              16384  1 snd
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
input_leds             16384  0
nvidia_uvm            831488  0
mac_hid                16384  0
glue_helper            16384  1 aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
dcdbas                 20480  0
serio_raw              20480  0
sch_fq_codel           20480  2
parport_pc             40960  1
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 53248  0
hid                   126976  2 usbhid,hid_generic
nvidia_drm             45056  5
nvidia_modeset       1085440  17 nvidia_drm
nvidia              17604608  776 nvidia_uvm,nvidia_modeset
drm_kms_helper        180224  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
psmouse               151552  0
drm                   475136  8 drm_kms_helper,nvidia_drm
ahci                   40960  1
libahci                32768  1 ahci
i2c_i801               32768  0
e1000e                245760  0
lpc_ich                24576  0
ipmi_devintf           20480  0
ipmi_msghandler       102400  2 ipmi_devintf,nvidia
video                  45056  0

This the last driver, mt7610u_wifi_sta_v3002_dpo_20130916

 I deleted them one by one as they never, ever passed make command
Thanks for responding, awaiting instructions.

---

### Post by praseodym on 2019-07-16
As you see that driver is from 2013, way too old. However, the native one is loaded. Lets see
```

dkms status
locate mt7601u.ko | grep lib
dmesg | egrep 'rt2|mt7'
```

---

