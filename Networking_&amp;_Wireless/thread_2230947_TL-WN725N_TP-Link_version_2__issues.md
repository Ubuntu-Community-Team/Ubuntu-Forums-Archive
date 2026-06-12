---
title: "TL-WN725N TP-Link version 2  issues"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by absurdcakes on 2014-06-22
Hey guys, I am running ubuntu 13.10. I have a TL-WN725N TP-Link version 2. It's connected, blinks, connects at a 100 percent strength or whatever, but it doesn't actually load my webpages. I can't figure it out. Sometimes IT DOES CONNECT THO. I used this guide to install its driver:

[http://brilliantlyeasy.com/ubuntu-linux-tl-wn725n-tp-link-version-2-wifi-driver-install/](http://brilliantlyeasy.com/ubuntu-linux-tl-wn725n-tp-link-version-2-wifi-driver-install/)

Besides fixing a few sudos, it looks pretty legit. Halp

---

### Post by absurdcakes on 2014-06-22
```

uname -alsusb
lsmod
iwconfig
iwlist chan
sudo iwlist scan
```


I did that and this is the results:

```
pizza@pizza-ThinkPad-T440 ~/Desktop $ uname -aLinux pizza-ThinkPad-T440 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
pizza@pizza-ThinkPad-T440 ~/Desktop $ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 04f2:b39a Chicony Electronics Co., Ltd 
Bus 002 Device 005: ID 0bda:8761 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 138a:0017 Validity Sensors, Inc. 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pizza@pizza-ThinkPad-T440 ~/Desktop $ lsmod
Module                  Size  Used by
joydev                 17377  0 
cfg80211              479757  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  16 
bnep                   19564  2 
x86_pkg_temp_thermal    14162  0 
coretemp               13435  0 
kvm                   431315  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
binfmt_misc            17468  1 
dm_multipath           22843  0 
scsi_dh                14882  1 dm_multipath
8188eu                781467  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
microcode              23518  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
psmouse                97626  0 
serio_raw              13413  0 
rtsx_pci_ms            18151  0 
snd_hda_codec_realtek    51465  1 
snd_hda_codec_hdmi     41276  1 
memstick               16760  1 rtsx_pci_ms
lpc_ich                21080  0 
btusb                  28267  0 
bluetooth             371874  22 bnep,btusb,rfcomm
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
mei_me                 18421  0 
mei                    77692  1 mei_me
thinkpad_acpi          80701  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
nvram                  14362  1 thinkpad_acpi
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
tpm_tis                19123  0 
soundcore              12680  1 snd
intel_smartconnect     12690  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
dm_mirror              22056  0 
dm_region_hash         20784  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
hid_logitech_dj        18581  0 
usbhid                 53014  0 
hid                   101512  3 usbhid,hid_logitech_dj
rtsx_pci_sdmmc         23527  0 
i915                  655752  5 
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25819  3 
libahci                31898  1 ahci
i2c_algo_bit           13413  1 i915
drm_kms_helper         52651  1 i915
e1000e                250025  0 
ptp                    18580  1 e1000e
pps_core               19027  1 ptp
drm                   296739  4 i915,drm_kms_helper
video                  19318  1 i915
wmi                    19070  0 
pizza@pizza-ThinkPad-T440 ~/Desktop $ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan5     IEEE 802.11bg  ESSID:"MemarRouter"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:7F:74:D4:38:5E   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-40 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


pizza@pizza-ThinkPad-T440 ~/Desktop $ iwlist chan
eth0      no frequency information.


lo        no frequency information.


wlan5     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.437 GHz (Channel 6)


pizza@pizza-ThinkPad-T440 ~/Desktop $ sudo iwlist scan
[sudo] password for pizza: 
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan5     Scan completed :
          Cell 01 - Address: 68:7F:74:D4:38:5E
                    ESSID:"MemarRouter"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie =dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie =30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Quality=0/100  Signal level=7/100  
          Cell 02 - Address: 68:7F:74:D4:38:5F
                    ESSID:"MemarRouter-guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality:0  Signal level:0  Noise level:0


pizza@pizza-ThinkPad-T440 ~/Desktop $ ^C



```

---

