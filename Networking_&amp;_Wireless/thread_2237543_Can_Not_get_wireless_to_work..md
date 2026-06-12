---
title: "Can Not get wireless to work."
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by rickm1945 on 2014-08-02
I have Ubuntu 14.04 Trusty Tahr running on a usb external HD. The wired connection works fine, but now do I get the wireless to work? I have Netgear Router.

---

### Post by praseodym on 2014-08-02
Hi there.

Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by rickm1945 on 2014-08-02
Outputs:
```
 richard@richard-Studio-XPS-8100:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8554]
    Kernel driver in use: r8169


```

```


richard@richard-Studio-XPS-8100:~$ lsmod
Module                  Size  Used by
cfg80211              484040  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391196  10 bnep,rfcomm
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
aesni_intel            55624  0 
snd_hwdep              13602  1 snd_hda_codec
aes_x86_64             17131  1 aesni_intel
snd_seq_midi           13324  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
lrw                    13286  1 aesni_intel
snd_seq_midi_event     14899  1 snd_seq_midi
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_rawmidi            30144  1 snd_seq_midi
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
nouveau              1097199  3 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
serio_raw              13462  0 
mxm_wmi                13021  1 nouveau
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ttm                    85115  1 nouveau
drm_kms_helper         53081  1 nouveau
mei_me                 18627  0 
drm                   303102  5 ttm,drm_kms_helper,nouveau
mei                    82276  1 mei_me
lpc_ich                21080  0 
soundcore              12680  1 snd
i2c_algo_bit           13413  1 nouveau
video                  19476  2 nouveau,asus_wmi
mac_hid                13205  0 
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18581  0 
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  4 hid_generic,usbhid,hid_logitech_dj
usb_storage            62209  2 
ahci                   25819  0 
psmouse               106678  0 
r8169                  67581  0 
libahci                32560  1 ahci
mii                    13934  1 r8169
richard@richard-Studio-XPS-8100:~$ 


```
```

richard@richard-Studio-XPS-8100:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0461:4e26 Primax Electronics, Ltd 
Bus 003 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 003 Device 002: ID 0930:a002 Toshiba Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
richard@richard-Studio-XPS-8100:~$ lsmod
Module                  Size  Used by
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391196  10 bnep,rfcomm
snd_hda_codec_hdmi     46254  1 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
snd_hda_codec_realtek    61438  1 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_hda_intel          52355  5 
kvm                   451511  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
crct10dif_pclmul       14289  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
nouveau              1097199  3 
serio_raw              13462  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mxm_wmi                13021  1 nouveau
ttm                    85115  1 nouveau
drm_kms_helper         53081  1 nouveau
lpc_ich                21080  0 
mei_me                 18627  0 
drm                   303102  5 ttm,drm_kms_helper,nouveau
mei                    82276  1 mei_me
soundcore              12680  1 snd
i2c_algo_bit           13413  1 nouveau
video                  19476  2 nouveau,asus_wmi
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18581  0 
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  4 hid_generic,usbhid,hid_logitech_dj
usb_storage            62209  2 
ahci                   25819  0 
psmouse               106678  0 
r8169                  67581  0 
libahci                32560  1 ahci
mii                    13934  1 r8169
richard@richard-Studio-XPS-8100:~$ 

```
```
richard@richard-Studio-XPS-8100:~$ iwconfig
eth1      no wireless extensions.

lo        no wireless extensions.

```

```
richard@richard-Studio-XPS-8100:~$ rfkill list
richard@richard-Studio-XPS-8100:~$ 

```

```

richard@richard-Studio-XPS-8100:~$ iwlist chan
eth1      no frequency information.

lo        no frequency information.

```

```

richard@richard-Studio-XPS-8100:~$ sudo iwlist scan
[sudo] password for richard: 
eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

richard@richard-Studio-XPS-8100:~$ 

```

This computer is a ASUS, Intel i7 porcessor, 12gb ram, I installed Ubuntu 1404 on usb HD when I had the Dell system. So Studio-XPS-8100 is the old system.

---

