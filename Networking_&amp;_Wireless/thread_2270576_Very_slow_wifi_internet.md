---
title: "Very slow wifi internet"
date: 2015-03-24
forum: Networking &amp; Wireless
---

### Post by mh-mithun on 2015-03-24
Hi,
I bought a new laptop which is Lenovo z40-70. I installed Ubuntu Gnome 14.04 on it. When I am near by by router the speed is not that bad but if I go another room the speed goes down to bytes/sec. I tested system using Windows 8.1 and it is fast.but ubuntu some how messed up. Please help.

```


root@lucid:/home/hasan/Downloads# lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380b]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo Device [17aa:0621]
    Kernel driver in use: wl


``` 

```

root@lucid:/home/hasan/Downloads# lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
wl                   6367833  0 
rtsx_usb_ms            18697  0 
memstick               16966  1 rtsx_usb_ms
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_codec_hdmi     47548  1 
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm_intel             143590  0 
kvm                   452043  1 kvm_intel
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
nouveau              1206577  1 
cfg80211              494330  1 wl
mxm_wmi                13021  1 nouveau
ttm                    85314  1 nouveau
joydev                 17393  0 
serio_raw              13483  0 
snd_hda_codec_conexant    23064  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_conexant
i915                  905798  6 
snd_soc_rt5640         93042  0 
lpc_ich                21093  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
drm_kms_helper         61574  2 i915,nouveau
snd_soc_core          200204  1 snd_soc_rt5640
shpchp                 37047  0 
drm                   311018  8 ttm,i915,drm_kms_helper,nouveau
mei_me                 19696  0 
mei                    87875  1 mei_me
snd_compress           19200  1 snd_soc_core
snd_pcm_dmaengine      15172  1 snd_soc_core
snd_hda_intel          30469  5 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
i2c_algo_bit           13413  2 i915,nouveau
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ideapad_laptop         18278  0 
snd_rawmidi            30876  1 snd_seq_midi
sparse_keymap          13948  1 ideapad_laptop
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
wmi                    19193  2 mxm_wmi,nouveau
snd                    79468  23 snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
snd_soc_sst_acpi       13007  0 
video                  20128  2 i915,nouveau
soundcore              15047  2 snd,snd_hda_codec
i2c_hid                18726  0 
hid                   110426  1 i2c_hid
dw_dmac                12835  0 
dw_dmac_core           28390  1 dw_dmac
i2c_designware_platform    12979  0 
i2c_designware_core    14768  1 i2c_designware_platform
8250_dw                13551  0 
spi_pxa2xx_platform    23079  0 
mac_hid                13227  0 
soc_button_array       12720  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
rtsx_usb_sdmmc         27787  0 
rtsx_usb               20987  2 rtsx_usb_sdmmc,rtsx_usb_ms
psmouse               106561  0 
ahci                   34062  2 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
sdhci_acpi             13351  0 
sdhci                  43685  1 sdhci_acpi
root@lucid:/home/hasan/Downloads# 



```

---

### Post by mh-mithun on 2015-03-26
There is no one around to help this problem :(

---

