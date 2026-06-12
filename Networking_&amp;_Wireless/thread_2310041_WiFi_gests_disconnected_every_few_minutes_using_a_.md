---
title: "WiFi gests disconnected every few minutes using a TL-WN823N USB adapter"
date: 2016-01-15
forum: Networking &amp; Wireless
---

### Post by raptormon on 2016-01-15
Hello everyone,
I'm new to Ubuntu (15.10) and I've tried to follow instructions in many other similar threads, but no success so far. Once it's disconnected, it doesn't get connected again unless I switch off connections and then back on. 

My adapter is a TP-Link TL-WN823N usb (mini). 

```
**lsusb:**
Bus 001 Device 005: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 10d5:55a4 Uni Class Technology Co., Ltd 
Bus 003 Device 003: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
**lsmod:**
Module                  Size  Used by
cmac                   16384  2
rfcomm                 69632  0
ctr                    16384  1
ccm                    20480  1
bnep                   20480  2
nls_utf8               16384  0
cifs                  565248  0
fscache                61440  1 cifs
binfmt_misc            20480  1
snd_hda_codec_hdmi     49152  1
drbg                   32768  1
ansi_cprng             16384  0
xts                    16384  1
gf128mul               16384  1 xts
dm_crypt               28672  1
cx22702                16384  1
isl6421                16384  1
cx24123                20480  1
arc4                   16384  2
cx88_dvb               36864  0
cx88_vp3054_i2c        16384  1 cx88_dvb
videobuf2_dvb          16384  1 cx88_dvb
dvb_core              122880  2 cx88_dvb,videobuf2_dvb
rtl8192cu              69632  0
snd_soc_wm8776         24576  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              733184  3 rtl_usb,rtlwifi,rtl8192cu
snd_soc_core          200704  1 snd_soc_wm8776
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
wm8775                 16384  1
ir_lirc_codec          16384  0
lirc_dev               20480  1 ir_lirc_codec
ir_rc6_decoder         16384  0
ir_sanyo_decoder       16384  0
ir_xmp_decoder         16384  0
ir_rc5_decoder         16384  0
ir_mce_kbd_decoder     16384  0
ir_nec_decoder         16384  0
ir_sharp_decoder       16384  0
ir_sony_decoder        16384  0
ir_jvc_decoder         16384  0
snd_hda_codec_realtek    86016  1
rc_hauppauge           16384  0
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
tuner_simple           20480  2
snd_hda_intel          36864  5
tuner_types            28672  1 tuner_simple
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
tda9887                16384  1
snd_hwdep              16384  1 snd_hda_codec
tda8290                24576  0
kvm_amd                65536  0
kvm                   512000  1 kvm_amd
tuner                  28672  2
snd_seq_midi           16384  0
cx8802                 20480  1 cx88_dvb
cx88_alsa              20480  1
cx8800                 40960  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
cx88xx                 86016  4 cx88_dvb,cx88_alsa,cx8800,cx8802
videobuf2_dma_sg       20480  3 cx88_dvb,cx8800,cx8802
tveeprom               24576  1 cx88xx
edac_core              53248  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
videobuf2_memops       16384  1 videobuf2_dma_sg
rc_core                28672  14 ir_sharp_decoder,ir_xmp_decoder,lirc_dev,ir_lirc_codec,rc_hauppauge,ir_rc5_decoder,ir_nec_decoder,ir_sony_decoder,cx88xx,ir_mce_kbd_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_sanyo_decoder
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_core         49152  5 cx88_dvb,cx8800,cx8802,cx88xx,videobuf2_dvb
edac_mce_amd           24576  0
k8temp                 16384  0
v4l2_common            16384  5 tuner,cx8800,cx88xx,wm8775,videobuf2_core
snd_pcm               106496  8 snd_soc_wm8776,cx88_alsa,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
joydev                 20480  0
input_leds             16384  0
videodev              172032  7 tuner,cx88_alsa,cx8800,cx88xx,v4l2_common,wm8775,videobuf2_core
snd_timer              32768  2 snd_pcm,snd_seq
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
media                  24576  2 tuner,videodev
btintel                16384  1 btusb
bluetooth             516096  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
snd                    81920  26 snd_hda_codec_realtek,cx88_alsa,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
soundcore              16384  1 snd
8250_fintek            16384  0
i2c_piix4              24576  0
shpchp                 36864  0
asus_atk0110           20480  0
mac_hid                16384  0
cfg80211              548864  2 mac80211,rtlwifi
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_microsoft          16384  0
pata_acpi              16384  0
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_generic,hid_microsoft,usbhid
amdkfd                122880  1
amd_iommu_v2           20480  1 amdkfd
radeon               1519616  4
i2c_algo_bit           16384  3 cx88_vp3054_i2c,cx88xx,radeon
psmouse               126976  0
ttm                    94208  1 radeon
drm_kms_helper        126976  1 radeon
firewire_ohci          40960  0
drm                   356352  7 ttm,drm_kms_helper,radeon
ahci                   36864  2
firewire_core          65536  1 firewire_ohci
libahci                32768  1 ahci
crc_itu_t              16384  1 firewire_core
r8169                  81920  0
mii                    16384  1 r8169
pata_atiixp            16384  0
```


Many thanks for helping!
mon.

I have nothing but problems with Wireless adapters and Linux. 

Thanks for your reply , but before spending more money I will do all I can to make it work. Any other ideas from anyone else?

---

### Post by byb3 on 2016-01-16
Consider the amount of time you will spend fixing it, and then fixing it again compared to £10 on a compatible one.  It depends how much you value your time.

---

### Post by byb3 on 2016-01-16
Do some googling for people with your adapter to see if there are issues.  There may be a newer firmware available or you may have to upgrade your kernel to get some stability.  If not I would find a USB adapter that is compatible and buy that instead.  I had an Intel 7265 adapter that consistently crashed in the most Random ways and after a year of pain I just gave up and bought a much cheaper Atheros one that hasn't failed me once.

---

### Post by Hadaka on 2016-01-16
Hi, with a working wired connection, please go here..
[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)
*Before you Download
Read carefully the installation instructions [about 1/2 way down the page]
and the added note in TROUBLE SHOOTING for disconnects.
The Download button is in the upper right corner.
good luck

---

