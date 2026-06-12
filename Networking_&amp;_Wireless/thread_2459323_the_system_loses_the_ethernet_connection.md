---
title: "the system loses the ethernet connection"
date: 2021-03-16
forum: Networking &amp; Wireless
---

### Post by fabio61 on 2021-03-16
I have a new computer with  a dual boot Win10/Ubuntu 20.04 and an unsupported RTL8125 2.5GbE Controller.
After I found and installed the proper driver (for Ubuntu, of course), the Ethernet connection works well. However, when I am back on Ubuntu, after a Windows session, I cannot see my Ethernet connection again and I must re-install the driver to have it work. Then, it continue working fine until the next windows session.

How can I make the driver more "stable"? The script to install the driver suggests to unload the old driver; I am not sure how to do it. Can it be the reason of the behavior? 

Thank you all

---

### Post by chili555 on 2021-03-17
Is Wake-on-lan in Windows enabled and therefore controlling the ethernet? Please try disabling it.

Let's see what drivers are loaded; please run and post:

```
lsmod
```Did you install the driver with dkms?

```
sudo dkms status 
```

---

### Post by praseodym on 2021-03-17
I think its not the driver. Deactivate  quick start mode in Windows (or whatever its name is)

---

### Post by CelticWarrior on 2021-03-17
This ^^^ It's Fast Startup.

---

### Post by praseodym on 2021-03-17
thanks ;-)

---

### Post by fabio61 on 2021-03-19
> **chili555 said:**
> Is Wake-on-lan in Windows enabled and therefore controlling the ethernet? Please try disabling it.

Let's see what drivers are loaded; please run and post:

```
lsmod
```

here it is:
```

Module                  Size  Used by
binfmt_misc            24576  1
nls_utf8               16384  1
isofs                  49152  1
rfcomm                 81920  4
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               516096  2 vboxnetadp,vboxnetflt
ccm                    20480  9
cmac                   16384  2
algif_hash             16384  1
algif_skcipher         16384  1
af_alg                 28672  6 algif_hash,algif_skcipher
bnep                   24576  2
nls_iso8859_1          16384  1
usblp                  24576  0
snd_hda_codec_realtek   131072  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  1 snd_hda_codec_generic
edac_mce_amd           32768  0
snd_hda_codec_hdmi     61440  1
snd_hda_intel          53248  5
uvcvideo               98304  0
snd_intel_dspcfg       24576  1 snd_hda_intel
videobuf2_vmalloc      20480  1 uvcvideo
kvm_amd                98304  0
videobuf2_memops       20480  1 videobuf2_vmalloc
snd_hda_codec         139264  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
videobuf2_v4l2         24576  1 uvcvideo
amdgpu               5214208  32
iwlmvm                393216  0
kvm                   712704  1 kvm_amd
snd_usb_audio         282624  3
snd_hda_core           94208  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
videobuf2_common       57344  2 videobuf2_v4l2,uvcvideo
snd_usbmidi_lib        36864  1 snd_usb_audio
crct10dif_pclmul       16384  1
snd_seq_midi           20480  0
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
mac80211              905216  1 iwlmvm
ghash_clmulni_intel    16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
aesni_intel           372736  9
iommu_v2               20480  1 amdgpu
videodev              241664  3 videobuf2_v4l2,uvcvideo,videobuf2_common
crypto_simd            16384  1 aesni_intel
snd_pcm               114688  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
libarc4                16384  1 mac80211
gpu_sched              36864  1 amdgpu
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
mc                     57344  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
ttm                   102400  1 amdgpu
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
btusb                  57344  0
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper        217088  1 amdgpu
btrtl                  24576  1 btusb
rapl                   20480  0
btbcm                  16384  1 btusb
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
cec                    53248  1 drm_kms_helper
btintel                28672  1 btusb
iwlwifi               352256  1 iwlmvm
rc_core                57344  1 cec
snd_timer              40960  2 snd_seq,snd_pcm
bluetooth             581632  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
i2c_algo_bit           16384  1 amdgpu
snd                    94208  29 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
ecdh_generic           16384  1 bluetooth
input_leds             16384  0
joydev                 24576  0
efi_pstore             16384  0
wmi_bmof               16384  0
k10temp                16384  0
sysimgblt              16384  1 drm_kms_helper
soundcore              16384  1 snd
ccp                    98304  1 kvm_amd
ecc                    32768  1 ecdh_generic
cfg80211              778240  3 iwlmvm,iwlwifi,mac80211
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             45056  0
drm                   552960  11 gpu_sched,drm_kms_helper,amdgpu,ttm
ppdev                  24576  0
lp                     20480  0
parport                65536  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               49152  1 ip_tables
autofs4                45056  2
hid_logitech_hidpp     45056  0
hid_logitech_dj        28672  0
hid_generic            16384  0
uas                    28672  0
usbhid                 57344  1 hid_logitech_dj
hid                   135168  4 usbhid,hid_generic,hid_logitech_dj,hid_logitech_hidpp
usb_storage            73728  2 uas
crc32_pclmul           16384  0
r8125                 155648  0
r8169                  77824  0
i2c_piix4              28672  0
nvme                   45056  3
ahci                   40960  4
xhci_pci               20480  0
libahci                36864  1 ahci
realtek                24576  0
nvme_core             110592  5 nvme
xhci_pci_renesas       20480  1 xhci_pci
wmi                    32768  1 wmi_bmof

```


Maybe I need to purge "r8169 " driver?

[> **chili555 said:**
> ]Did you install the driver with dkms?

no: by running the script

---

### Post by fabio61 on 2021-03-19
> **CelticWarrior said:**
> This ^^^ It's Fast Startup.

I disabled fast startup right away, before installing ubuntu

---

### Post by chili555 on 2021-03-19
> Maybe I need to purge "r8169 " driver?Let's try an experiment first. From the terminal:

```
sudo modprobe -r 8169
```

Is there any improvement? If so, blacklist it:

```
sudo -i
echo "blacklist r8169" >>  /etc/modprobe.d/blacklist.conf
exit

```

---

