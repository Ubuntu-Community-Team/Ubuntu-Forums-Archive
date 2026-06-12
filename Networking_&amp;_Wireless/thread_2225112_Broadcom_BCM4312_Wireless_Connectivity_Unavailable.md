---
title: "Broadcom BCM4312 Wireless Connectivity Unavailable"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by z-buildrocks on 2014-05-19
After trying all the methods listed, I have not gotten wireless connectivity. I used to have wireless, but I lost connectivity since I installed Linux Mint on a separate partition. I don't know how this would affect my wireless though.

---

### Post by Hadaka on 2014-05-19
Hi,it;s possible that mint uses a different driver....let's find out
from the mint connection
please do and post..
```
lspci -nnk | grep -iA3 net
rfkill list all
lsmod
```
thanks

---

### Post by eobdtool on 2014-05-19
Hello, did you try to connect the customer service for help?

---

### Post by z-buildrocks on 2014-05-19
**First command- **[COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA3 net[/FONT][/COLOR]**:**
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: sky2
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: wl


**Second Command- **[COLOR=#000000][FONT=Ubuntu Mono]rfkill list all[/FONT][/COLOR]**:**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


**Third Command- **[COLOR=#000000][FONT=Ubuntu Mono]lsmod[/FONT][/COLOR]**:**
Module                  Size  Used by
b43                   387371  0 
bcma                   52096  1 b43
mac80211              626489  1 b43
ssb                    62379  1 b43
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
gpio_ich               13476  0 
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
lib80211_crypt_tkip    17619  0 
coretemp               13435  0 
snd_hda_codec_idt      54645  1 
wl                   4207846  0 
joydev                 17381  0 
serio_raw              13462  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
snd_hda_intel          52355  8 
snd_hda_codec         192906  2 snd_hda_codec_idt,snd_hda_intel
lpc_ich                21080  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
cfg80211              484040  3 wl,b43,mac80211
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  25 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
ums_realtek            18029  0 
usb_storage            62209  1 ums_realtek
psmouse               102222  0 
ahci                   25819  1 
libahci                32168  1 ahci
sky2                   58191  0 
i915                  783485  5 
video                  19476  1 i915
i2c_algo_bit           13413  1 i915
wmi                    19177  1 dell_wmi
drm_kms_helper         52758  1 i915
drm                   302817  6 i915,drm_kms_helper

---

### Post by Hadaka on 2014-05-19
hi, please copy and paste these commands,,
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
boot
and then while connected via ethernet cable please do,,,
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by z-buildrocks on 2014-05-19
Well, It did not appear to be working, since the wireless menu wouldn't let me turn wifi on, but I opened the connections menu, opened the settings for my wireless network and hit ok. Then it connected. No idea what was going on there, but thanks for your help!

---

### Post by z-buildrocks on 2014-05-19
How do I mark this as solved?

---

### Post by Hadaka on 2014-05-19
hi,glad you got it working.
you had wl driver loaded by default and you
needed linux-firmware-nonfree. One that was
sorted all was well,, please dont forget to do..
```
sudo apt-get update
```
thanks
to mark SOLVED ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

