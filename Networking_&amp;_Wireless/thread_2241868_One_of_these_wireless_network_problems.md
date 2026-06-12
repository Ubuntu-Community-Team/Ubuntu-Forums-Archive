---
title: "One of these wireless network problems"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by erik19 on 2014-08-28
Hi, i installed Ubuntu two days ago and to my disappointment i have spent 24 hours only trying solve how to get my internet up and running.
I have googled, read threads and watched youtube videos but nothing really works for me.:(

So, my internet only works with a cable and no wireless connections shows up at all.
I cant scan for available networks since it says: interface doesnt support scanning.
And there are only nvidia tingys at additional drivers... 

I have tried doing sudo apt-get install firmware-b43-installer and fwcutter etc but no success. 
Please note im very new to linux ):P

---

### Post by Hadaka on 2014-08-28
Hi, please run and post..
```
lspci -nn | grep 0280
rfkill list all
lsmod
lsusb
```
thanks.

---

### Post by erik19 on 2014-08-28
Alright, thanks by the way. This is much appreciated!

> Erik@Laptop:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
Erik@Laptop:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
Erik@Laptop:~$ lsmod
Module                  Size  Used by
bbswitch               13943  0 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391196  10 bnep,rfcomm
nls_iso8859_1          12713  1 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
b44                    40234  0 
snd_hda_intel          52355  6 
ssb                    62379  1 b44
parport_pc             32701  0 
kvm_intel             143060  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
wl                   4207846  0 
ppdev                  17671  0 
kvm                   451511  1 kvm_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
bcma                   52096  0 
mac80211              630653  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
lib80211               14381  1 wl
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17381  0 
snd_rawmidi            30144  1 snd_seq_midi
serio_raw              13462  0 
nvidia              10675249  35 
rtsx_pci_ms            18151  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
memstick               16966  1 rtsx_pci_ms
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
lpc_ich                21080  0 
lp                     17759  0 
cfg80211              484040  2 wl,mac80211
parport                42348  3 lp,ppdev,parport_pc
snd                    69238  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
mei_me                 18627  0 
mei                    82276  1 mei_me
wmi                    19177  2 mxm_wmi,asus_wmi
mac_hid                13205  0 
dm_crypt               23177  1 
rtsx_pci_sdmmc         23274  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  1065 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  535 ghash_clmulni_intel,aesni_intel,ablk_helper
i915                  783805  2 
psmouse               106678  0 
i2c_algo_bit           13413  1 i915
drm_kms_helper         53081  1 i915
drm                   303102  5 i915,drm_kms_helper,nvidia
ahci                   25819  3 
r8169                  67581  0 
libahci                32560  1 ahci
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    13934  2 b44,r8169
video                  19476  2 i915,asus_wmi
Erik@Laptop:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b40a Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0489:e069 Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Erik@Laptop:~$ 



---

### Post by Hadaka on 2014-08-28
Hi, in the future please use code tags, there are no linux drivers
for your wifi card. I would suggest removing it, and replacing with
an intel card or a broadcom card, and speaking of broadcom cards
you currently do not have any, yet you loaded broadcom drivers for
both the wireless and the wired, you cant just toss any drivers in the
os and expect them to work, they need to be for the type of card you have,
so let's get rid of the the modules before they cause any problems,
please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rmmod ssb
sudo rmmod bcma
sudo rmmod b44
sudo rmmod wl
```
you may get some errors or not found on these but it doesnt really matter
do them anyway.
Please mark this thread SOLVED as its as solved as its going to get with no
drivers available.
once you relpace the card if you require help, post a new thread
thanks.

---

### Post by cqfd93 on 2014-09-01
Hi,

Check out comment #161 (and if it doesn't work for you, comment #125) of bug #1220146

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/161](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/161)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/125](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/125)

Hope this helps

---

