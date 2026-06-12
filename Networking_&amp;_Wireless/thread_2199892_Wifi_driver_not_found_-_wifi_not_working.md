---
title: "Wifi driver not found - wifi not working"
date: 2014-01-16
forum: Networking &amp; Wireless
---

### Post by olly3 on 2014-01-16
Hi, I've jut installed Ubuntu 12.04 on my PB Easynote-TS13HR. However it will not find the wifi driver. When I type ```
lspci -nn | grep 0280
```, I get ```
Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
```

I've tried using ndisgtk, but it does not list any installed drivers. 

When I entered ```
rfkill list all
``` I got ```
Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

I then tried ```
sudo modprobe wl


```, which returned ```
FATAL: Module wl not found.
```

I'm rather confused now as to what to do. Any help would be greatly appreciated. :)

---

### Post by praseodym on 2014-01-16
You only need to install the package **linux-firmware-nonfree**. Which kernel is it? Check 

uname -a

---

### Post by olly3 on 2014-01-16
Its ```
3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by olly3 on 2014-01-16
I've done ```
sudo apt-get install linux-firmware-nonfree
```

---

### Post by praseodym on 2014-01-16
Reboot

---

### Post by olly3 on 2014-01-16
I'm afraid its still not working :( Is there any more diagnostic information that I could post here?

---

### Post by praseodym on 2014-01-16
Yes, lets check:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
grep brcm /etc/modprobe.d/*
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by olly3 on 2014-01-16
[

---

### Post by praseodym on 2014-01-16
You dont need that one normally, there's a native driver available. Uninstall that one completely:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*) 
```
Reboot and check the outputs. You better copy/paste these lines ;)

---

### Post by olly3 on 2014-01-16
Ok, I got the following:

```
lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    Kernel driver in use: tg3
--
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    Kernel driver in use: sdhci-pci
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04da]
    Kernel modules: bcma
olly@olly-EasyNote-TS13HR:~$ lsmod
Module                  Size  Used by
bnep                   18258  2 
rfcomm                 47864  0 
bluetooth             247024  10 bnep,rfcomm
parport_pc             28284  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     37434  1 
snd_hda_codec_realtek    79916  1 
snd_hda_intel          44339  3 
snd_hda_codec         141716  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
coretemp               13596  0 
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
uvcvideo               82214  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_core         40785  1 uvcvideo
kvm_intel             137899  0 
videodev              130053  2 uvcvideo,videobuf2_core
kvm                   455932  1 kvm_intel
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
videobuf2_vmalloc      13056  1 uvcvideo
ghash_clmulni_intel    13259  0 
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
cryptd                 20501  1 ghash_clmulni_intel
videobuf2_memops       13202  1 videobuf2_vmalloc
joydev                 17613  0 
i915                  620421  3 
acer_wmi               32858  0 
sparse_keymap          13890  1 acer_wmi
psmouse                97873  0 
drm_kms_helper         49597  1 i915
microcode              23017  0 
serio_raw              13215  0 
drm                   287564  4 i915,drm_kms_helper
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
soundcore              12680  1 snd
wmi                    19256  1 acer_wmi
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lpc_ich                17144  0 
i2c_algo_bit           13564  1 i915
mei                    41820  0 
video                  19652  2 i915,acer_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
tg3                   165622  0 
ptp                    18668  1 tg3
pps_core               14080  1 ptp
ahci                   25879  2 
libahci                31606  1 ahci
sdhci_pci              18721  0 
sdhci                  33141  1 sdhci_pci
olly@olly-EasyNote-TS13HR:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

olly@olly-EasyNote-TS13HR:~$ grep brcm /etc/modprobe.d/*
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcm80211
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcmfmac
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcmsmac
olly@olly-EasyNote-TS13HR:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
olly@olly-EasyNote-TS13HR:~$ iwlist chan
eth0      no frequency information.

lo        no frequency information.


```

---

### Post by olly3 on 2014-01-16
oh thanks so much :3 It's working now. And sorry I was lagging behind a bit on your replies!

---

### Post by praseodym on 2014-01-16
Great. As you see the native driver was blacklisted:

> /etc/modprobe.d/blacklist-bcm43.conf:blacklist brcmsmac

---

