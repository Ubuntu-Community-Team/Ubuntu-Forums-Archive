---
title: "Broadcom Wifi Driver Won't Activate"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by Nick_Hassan on 2014-01-31
Im new to ubuntu and can't get the driver activated. I have a MacBook Pro Retina Display and I get an error message whenever I try to activate it. It tells me to look at jockey.log.

Sorry if this is a duplicate thread. I couldn't find any other threads relating to this topic.


Thanks, Nick

---

### Post by praseodym on 2014-01-31
Hi,

do you really need it? Lets check:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by Nick_Hassan on 2014-02-01
> **praseodym said:**
> Hi,

do you really need it? Lets check:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

uname -a:
Linux NICK-MBP-U 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

ispci -nnk | grep -iA2 net:
02:00.0 Ethernet controller [0200]: Broadcom Corporation Device [14e4:16a3] (rev 21)
    Subsystem: Broadcom Corporation Device [14e4:16a3]
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 21)
    Subsystem: Broadcom Corporation Device [14e4:96bc]
    Kernel driver in use: sdhci-pci
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
    Subsystem: Apple Inc. Device [106b:010f]
    Kernel modules: bcma

lsmod:
Module                  Size  Used by
asix                   27817  0 
usbnet                 31972  1 asix
snd_hda_codec_hdmi     37434  1 
snd_hda_codec_cirrus    24074  0 
coretemp               13596  0 
kvm_intel             137899  0 
kvm                   455932  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55495  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
aes_x86_64             17255  1 aesni_intel
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
joydev                 17613  0 
applesmc               19564  0 
input_polldev          13896  1 applesmc
microcode              23017  0 
btusb                  22431  0 
pcspkr                 12718  0 
usbmouse               12769  0 
bcm5974                17470  0 
apple_gmux             13406  0 
snd_hda_intel          44339  2 
snd_hda_codec         141716  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
apple_bl               13673  1 apple_gmux
evbug                  12661  0 
mac_hid                13253  0 
i2c_i801               22168  0 
uvcvideo               82214  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_core         40785  1 uvcvideo
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
videodev              130053  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13056  1 uvcvideo
lpc_ich                17144  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  620421  3 
drm_kms_helper         49597  1 i915
bnep                   18258  2 
snd                    69533  14 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 47864  12 
drm                   287564  4 i915,drm_kms_helper
bluetooth             247024  24 btusb,bnep,rfcomm
i2c_algo_bit           13564  1 i915
soundcore              12680  1 snd
mei                    41820  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
video                  19652  2 apple_gmux,i915
parport_pc             28284  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_generic            12540  0 
hid_apple              13382  0 
usbhid                 47346  0 
hid                   105549  3 hid_generic,hid_apple,usbhid
sdhci_pci              18721  0 
sdhci                  33141  1 sdhci_pci
ahci                   25879  1 
libahci                31606  1 ahci

iwconfig:
eth0      no wireless extensions.

lo        no wireless extensions.

rfkill list:
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by praseodym on 2014-02-01
Deactivate the driver, uninstall it (if applicable) and clean up the config. After that install the missing firmware for the native driver:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*) 
sudo apt-get install linux-firmware nonfree
```
Reboot. Error messeges can be ignored. You better copy/paste these lines ;)

---

### Post by Gneykan_ on 2014-02-03
i think it worked for me thank you so much

---

