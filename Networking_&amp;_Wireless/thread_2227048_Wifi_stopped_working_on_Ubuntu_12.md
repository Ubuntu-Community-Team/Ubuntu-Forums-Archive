---
title: "Wifi stopped working on Ubuntu 12"
date: 2014-05-30
forum: Networking &amp; Wireless
---

### Post by tetradeca7tope on 2014-05-30
Hi,

My Wifi stopped working on my Ubuntu - Its been about 6 months since I started using Ubuntu 12 and didn't have any issues thus far until yesterday.

after googling around a bit, I tried a few stuff. These are the results I got:

```

$ dmesg | grep iwl
[   23.575514] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.575569] iwlwifi 0000:03:00.0: setting latency timer to 64
[   23.575618] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   23.575620] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900058a8000
[   23.575622] iwlwifi 0000:03:00.0: HW Revision ID = 0x67
[   23.575830] iwlwifi 0000:03:00.0: irq 52 for MSI/MSI-X
[   23.575925] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   23.576143] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   23.586380] iwlwifi 0000:03:00.0: device EEPROM VER=0x557, CALIB=0x6
[   23.586382] iwlwifi 0000:03:00.0: Device SKU: 0X150
[   23.586384] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   23.586412] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   23.586592] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   23.588348] iwlwifi 0000:03:00.0: loaded firmware version 41.28.5.1 build 33926
[   24.280686] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

```

```
$ rfkill list all
0: i2400m-usb:1-1.2:1.0: WiMAX
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

```
$ lsmod
Module                  Size  Used by
dm_crypt               23125  0 
snd_hda_codec_hdmi     32530  1 
joydev                 17693  0 
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
iwlwifi               401033  0 
uvcvideo               72627  0 
i2400m_usb             36569  0 
mac80211              506862  1 iwlwifi
i2400m                108073  1 i2400m_usb
cfg80211              205774  2 iwlwifi,mac80211
videodev               98259  1 uvcvideo
wimax                  34762  1 i2400m
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
toshiba_acpi           18582  0 
jmb38x_ms              17646  0 
memstick               16569  1 jmb38x_ms
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                97519  0 
bnep                   18281  2 
sparse_keymap          13890  1 toshiba_acpi
mac_hid                13253  0 
rfcomm                 47604  0 
mei                    41616  0 
parport_pc             32866  0 
v4l2_compat_ioctl32    17128  1 videodev
wmi                    19256  1 toshiba_acpi
serio_raw              13211  0 
ppdev                  17113  0 
dm_multipath           23275  0 
bluetooth             180113  10 bnep,rfcomm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
raid10                 35489  0 
raid456                58338  0 
async_pq               13187  1 raid456
async_xor              12879  2 raid456,async_pq
xor                    12894  1 async_xor
async_memcpy           12529  1 raid456
async_raid6_recov      12824  1 raid456
raid6_pq               88382  2 async_pq,async_raid6_recov
async_tx               13349  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
raid1                  35572  0 
raid0                  17229  0 
multipath              13145  0 
linear                 12894  0 
usbhid                 47238  0 
hid                    99883  1 usbhid
i915                  478556  4 
drm_kms_helper         46978  1 i915
drm                   241971  5 i915,drm_kms_helper
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
r8169                  62190  0 
i2c_algo_bit           13423  1 i915
video                  19651  1 i915

```

---

### Post by praseodym on 2014-05-30
Hi,

what kind of computer is it? Tried to reset the BIOS?

---

