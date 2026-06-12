---
title: "Proprietary wireless driver"
date: 2014-06-16
forum: Networking &amp; Wireless
---

### Post by The musmula on 2014-06-16
On the Kubuntu live cd I have had the option to install a proprietary driver for my wireless card, and I did install it and it worked,
Now I made a full install of the Kubuntu OS, and I dont have that option anymore... can anybody tell me how to find it?

and btw
should I use the ubuntu software center on kubuntu? (since kazam, chromium, or anything else I used on ubuntu is not in muon discover)

---

### Post by Hadaka on 2014-06-16
hi, please open a terminal   crl/alt/t
then COPY  and paste the followng
```
lspci -nnk | grep -iA2 net
lsmod
rfkill list all
```
post the output
thanks.

---

### Post by The musmula on 2014-06-16
Thank you for the quick answer, but before I got your answer I made a system update and after the restart... boom, kubuntu says the good news :)

here is the output anyway:
```

doly@Komputator:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82562GT 10/100 Network Connection [8086:10c4] (rev 03)
        Subsystem: Hewlett-Packard Company Device [103c:30d8]
        Kernel driver in use: e1000e
--
10:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
        Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137d]
        Kernel driver in use: b43-pci-bridge
doly@Komputator:~$ lsmod          
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             395423  10 bnep,rfcomm
b43                   387371  0 
snd_hda_codec_analog    15049  1 
snd_hda_intel          52355  6 
snd_hda_codec         192906  2 snd_hda_intel,snd_hda_codec_analog
bcma                   52096  1 b43
joydev                 17381  0 
mac80211              626557  1 b43
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
cfg80211              484040  2 b43,mac80211
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
coretemp               13435  0 
snd                    69238  22 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog,snd_seq_midi
psmouse               102222  0 
serio_raw              13462  0 
soundcore              12680  1 snd
lpc_ich                21080  0 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ahci                   25819  3 
libahci                32168  1 ahci
ssb                    62379  1 b43
wmi                    19177  1 hp_wmi
i915                  783703  3 
e1000e                254433  0 
video                  19476  1 i915
i2c_algo_bit           13413  1 i915
drm_kms_helper         52758  1 i915
ptp                    18933  1 e1000e
pps_core               19382  1 ptp
drm                   302817  4 i915,drm_kms_helper
doly@Komputator:~$ rfkill list all


```

and muon works perfectly fine now :)

---

### Post by Hadaka on 2014-06-16
Excellent ! Glad you got it working !

Please take the time to mark your thread SOLVED
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks

---

