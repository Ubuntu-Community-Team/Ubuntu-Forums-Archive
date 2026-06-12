---
title: "WiFi not working in fresh installation of Ubuntu"
date: 2016-01-07
forum: Networking &amp; Wireless
---

### Post by parth_sharma on 2016-01-07
I have an ASUS X550J Laptop  and I recently installed Ubuntu 14.04.3 (alongside windows 10 ) .While running Ubuntu my laptop is not detecting any Wi-fi network (probably it because the adapter is switched off.) and the physical key ( Fn+F2 ) doesn't seem to work along with brightness and few other keys. (Though Volume keys ARE working) . My LAN connection is working fine though. What should I do to resolve this?

Here are my outputs of 
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
```

```
parth@parth-X550JK:~$ lspci -nnk | grep -iA3 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6605]
    Kernel driver in use: bcma-pci-bridge
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5287] (rev 01)
--
04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
parth@parth-X550JK:~$ lsmod
Module                  Size  Used by
rfcomm                 69632  8 
bnep                   20480  2 
nls_iso8859_1          16384  1 
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_conexant    24576  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_conexant
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
btusb                  40960  0 
videobuf2_core         53248  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
bluetooth             491520  22 bnep,btusb,rfcomm
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
kvm_intel             151552  0 
kvm                   479232  1 kvm_intel
snd_hda_intel          32768  5 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
snd_hwdep              20480  1 snd_hda_codec
ghash_clmulni_intel    16384  0 
aesni_intel           172032  1 
snd_seq_midi           16384  0 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi_event     16384  1 snd_seq_midi
aes_x86_64             20480  1 aesni_intel
snd_rawmidi            32768  1 snd_seq_midi
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
ablk_helper            16384  1 aesni_intel
nouveau              1368064  1 
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
i915                 1048576  4 
joydev                 20480  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
serio_raw              16384  0 
mxm_wmi                16384  1 nouveau
ttm                    94208  1 nouveau
snd                    86016  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper        126976  2 i915,nouveau
rtsx_pci_ms            20480  0 
lpc_ich                24576  0 
drm                   344064  8 ttm,i915,drm_kms_helper,nouveau
ie31200_edac           16384  0 
memstick               20480  1 rtsx_pci_ms
bcma                   53248  0 
mei_me                 20480  0 
mei                    90112  1 mei_me
shpchp                 40960  0 
soundcore              16384  2 snd,snd_hda_codec
i2c_algo_bit           16384  2 i915,nouveau
edac_core              53248  1 ie31200_edac
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
video                  20480  3 i915,nouveau,asus_wmi
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
rtsx_pci_sdmmc         24576  0 
psmouse               114688  0 
ahci                   36864  3 
r8169                  81920  0 
rtsx_pci               49152  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                32768  1 ahci
mii                    16384  1 r8169
parth@parth-X550JK:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
parth@parth-X550JK:~$ 


```

---

### Post by chili555 on 2016-01-07
Please see: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by parth_sharma on 2016-01-08
Thanks a ton,

---

