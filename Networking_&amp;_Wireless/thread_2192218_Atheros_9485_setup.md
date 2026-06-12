---
title: "Atheros 9485 setup"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by leroyklotz on 2013-12-06
I notice there are alot of threads on this already however I have read through so many of them and tried such a wide amount of commands that I'm pretty much lost as to where I have already been and what I might have messed up.. I have also tried following youtube tutorials on how to achieve it but they all seem to be fairly specific towards the card that the makers have in their video..

This is the card that I'm hoping to get to work..

03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)

I hope one of you people out there has the magic that its begging for.. 

Thanks in advance!

---

### Post by praseodym on 2013-12-08
Please hsow these outputs
```

lsmod
grep ath /etc/modprobe.d/*
iwconfig
rfkill list
cat /etc/resolv.conf
```
Does LAN work?

---

### Post by leroyklotz on 2013-12-08
Hi there praseodym! LAN works just fine.
Here are the results to the commands that you asked me to run.
> [B]
lsmod[/B]
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19564  2 
rfcomm                 69070  0 
bluetooth             371880  10 bnep,rfcomm
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_realtek    55704  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
cryptd                 20329  1 ghash_clmulni_intel
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
joydev                 17377  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
arc4                   12608  2 
snd_timer              29433  2 snd_pcm,snd_seq
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
ath9k                 151173  0 
microcode              23518  0 
ath9k_common           13859  1 ath9k
ath9k_hw              444645  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
psmouse                97626  0 
serio_raw              13413  0 
mac80211              596969  1 ath9k
rtsx_pci_ms            18151  0 
cfg80211              479757  3 ath,ath9k,mac80211
snd                    69141  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
nouveau               943295  1 
lpc_ich                21080  0 
memstick               16760  1 rtsx_pci_ms
soundcore              12680  1 snd
mxm_wmi                13021  1 nouveau
ttm                    83995  1 nouveau
i915                  655752  3 
drm_kms_helper         52651  2 i915,nouveau
wmi                    19070  3 mxm_wmi,nouveau,asus_wmi
drm                   296739  7 ttm,i915,drm_kms_helper,nouveau
video                  19318  3 i915,nouveau,asus_wmi
mac_hid                13205  0 
mei_me                 18421  0 
mei                    77692  1 mei_me
i2c_algo_bit           13413  2 i915,nouveau
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   105818  2 hid_generic,usbhid
rtsx_pci_sdmmc         23527  0 
r8169                  67341  0 
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25819  2 
libahci                31898  1 ahci
mii                    13934  1 r8169

> 
**grep ath /etc/modprobe.d/***
/etc/modprobe.d/blacklist:blacklist ath_pci
/etc/modprobe.d/blacklist:blacklist ath_hal
/etc/modprobe.d/blacklist:blacklist ath9k
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath_pci

> 
**iwconfig**
[SIZE=1]*:o = : o (ofcourse)*[/SIZE]

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

> 
**rfkill list**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

> **cat /etc/resolv.conf**
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search sitecomwl342

---

### Post by praseodym on 2013-12-08
```
rfkill list
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: [COLOR="#FF0000"]yes[/COLOR]
```
Your wireless is turned off. Any button, switch or key combination? 

Alternatively try

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
and reboot.

---

### Post by leroyklotz on 2013-12-08
Well yes there is a button on the keyboard accessable by holding down FN and then typing F2. But it was not responsive whatsoever.

However, as soon as i typed in the echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf and rebooted it asked me if I would like to connect to a wifi network.

So, solved. Thanks a million. Wish I had such knowledge! :)

---

