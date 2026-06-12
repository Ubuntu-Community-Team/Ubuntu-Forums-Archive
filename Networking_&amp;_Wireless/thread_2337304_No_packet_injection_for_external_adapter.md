---
title: "No packet injection for external adapter"
date: 2016-09-16
forum: Networking &amp; Wireless
---

### Post by csbova on 2016-09-16
Hello everyone!

I'm new to the community and for the past week have been reading through   loads of posts regarding various incredibly cool things you can do  with  linux.
Here's where I am at.


My internal wireless card is capable of injecting packets, however, I have found that my   usb wifi rt2800 usb rl2870/3070 was incapable of injecting packets in   aireplay-ng.
 [ ```
description: Wireless interface
       physical id: 1
       bus info: usb@2:2
       logical name: wlx00c0ca5958fe
       serial: 00:c0:ca:59:58:fe
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=rt2800usb    driverversion=4.4.0-36-generic firmware=0.29 ip=192.168.0.100 link=yes    multicast=yes wireless=IEEE 802.11bgn
```]



So for the sake of learning/challenge [IMG]https://ubuntuforums.org/images/icons/icon6.png[/IMG]   I followed the steps to install the latest backports (4.2.0-32) which   were supposed to have patched the adapter, making it capable of packet   injection.

After running aireplay again, still nothing

[```
$ sudo aireplay-ng -9 mon0
13:43:02  Trying broadcast probe requests...
13:43:04  No Answer...
13:43:04  Found 2 APs

13:43:04  Trying directed probe requests...
13:43:04  DC:D9:16:A4:0F:D7 - channel: 9 - 'VodafoneMobileWiFi-0FD784'
13:43:10   0/30:   0%

13:43:10  3C:1E:04:92:21:64 - channel: 10 - 'D-Link'
13:43:16   0/30:   0%
```]

Does anyone have any ideas? Maybe something obvious that I haven't tried yet?

```
$ lsmod
Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  2
ccm                    20480  2
bnep                   20480  2
bbswitch               16384  0
nls_iso8859_1          16384  1
nvidia_uvm            696320  0
nvidia_modeset        745472  2
nvidia              10076160  55 nvidia_modeset,nvidia_uvm
arc4                   16384  4
rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
crc_ccitt              16384  1 rt2800lib
coretemp               16384  0
uvcvideo               90112  0
kvm                   540672  0
ath10k_pci             45056  0
videobuf2_vmalloc      16384  1 uvcvideo
ath10k_core           229376  1 ath10k_pci
videobuf2_memops       16384  1 videobuf2_vmalloc
ath                    32768  1 ath10k_core
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
irqbypass              16384  1 kvm
mac80211              643072  4 rt2x00lib,rt2x00usb,rt2800lib,ath10k_core
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
cfg80211              565248  4 ath,mac80211,rt2x00lib,ath10k_core
media                  24576  2 uvcvideo,videodev
aesni_intel           167936  4
snd_hda_codec_realtek    86016  1
btusb                  45056  0
compat                 16384  4 cfg80211,mac80211,rt2800usb,ath10k_pci
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
btrtl                  16384  1 btusb
gf128mul               16384  1 lrw
btbcm                  16384  1 btusb
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
btintel                16384  1 btusb
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_ssm4567        16384  0
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
snd_hda_codec_hdmi     53248  1
snd_compress           20480  1 snd_soc_core
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
bluetooth             520192  9 bnep,btbcm,btrtl,btusb,btintel
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
ac97_bus               16384  1 snd_soc_core
cryptd                 20480  2 aesni_intel,ablk_helper
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hwdep              16384  1 snd_hda_codec
intel_pch_thermal      16384  0
input_leds             16384  0
snd_pcm               106496  7   snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
joydev                 20480  0
serio_raw              16384  0
hid_multitouch         20480  0
lpc_ich                24576  0
dw_dmac                16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
dw_dmac_core           24576  1 dw_dmac
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
mei_me                 36864  0
snd                    81920  23   snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
mei                    98304  1 mei_me
shpchp                 36864  0
ideapad_laptop         24576  0
elan_i2c               36864  0
intel_vbtn             16384  0
sparse_keymap          16384  2 ideapad_laptop,intel_vbtn
soundcore              16384  1 snd
snd_soc_sst_acpi       16384  0
i2c_designware_platform    16384  0
8250_dw                16384  0
wmi                    20480  1 ideapad_laptop
i2c_designware_core    20480  1 i2c_designware_platform
mac_hid                16384  0
spi_pxa2xx_platform    24576  0
acpi_pad               20480  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
i915                 1208320  3
i2c_algo_bit           16384  1 i915
drm_kms_helper        147456  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
psmouse               126976  0
ahci                   36864  3
drm                   364544  8 i915,drm_kms_helper,nvidia
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  1 r8169
video                  40960  2 i915,ideapad_laptop
sdhci_acpi             16384  0
sdhci                  45056  1 sdhci_acpi
i2c_hid                20480  0
hid                   118784  4 i2c_hid,hid_multitouch,hid_generic,usbhid
fjes                   28672  0

```

Thanks!

Please do not reply with any illegal suggestions.

---

### Post by wildmanne39 on 2016-09-16
Hello, let me be clear since the last thread being closed was not apparently, we do not allow this topic on the forum because no matter if you say do not discuss anything that is not legal people that are not as upstanding as you in their intentions can use what is posted here to hack into other peoples networks.

Your best bet is the Kali forum or aircracks forum.

I work with wireless and I know nothing about it since it is not allowed here and I do not know anyone else here that does so it will almost certainly go unresolved even if it was left open.

---

