---
title: "Can't connect to secure wireless network WEP"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by tn88test on 2013-09-19
I can connect to non secure network but not secure wireless network WEP. Ubuntu did't recognise the correct type of secure wireless. It was WEP 40/128 bit key(Hex or ASCII). The password is only 9 character, so I had to Edit Connection and choosed WEP 128 bit passphase instead. I also tried WPA but it did't work either. The password is fine. It worked on Windows XP but not Ubuntu.

```
home@home-PC:~$ lspci -nnk | grep -iA3 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MC Gigabit Network Connection [8086:104d] (rev 03)
    Subsystem: Intel Corporation Device [8086:0000]
    Kernel driver in use: e1000e
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
--
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
    Subsystem: Intel Corporation Device [8086:1001]
    Kernel driver in use: iwl4965
04:09.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
--
04:0a.0 Network controller [0280]: Siemens Nixdorf AG SIMATIC NET CP 5611 (Profibus Adapter) [110a:3141] (rev 02)
    Subsystem: PLX Technology, Inc. Device [10b5:0001]
home@home-PC:~$ lsmod
Module                  Size  Used by
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
snd_hda_codec_si3054    12864  1 
snd_hda_codec_analog    75266  1 
coretemp               13131  0 
kvm_intel             126842  0 
kvm                   376505  1 kvm_intel
ppdev                  12817  0 
gpio_ich               13236  0 
pcmcia                 39544  0 
arc4                   12543  2 
microcode              18286  0 
iwl4965               106850  0 
snd_hda_intel          38307  2 
snd_hda_codec         117580  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec_analog
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_si3054,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
parport_pc             27504  1 
yenta_socket           27095  0 
snd_rawmidi            25114  1 snd_seq_midi
iwlegacy               87575  1 iwl4965
pcmcia_rsrc            18191  1 yenta_socket
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
mac80211              526519  2 iwl4965,iwlegacy
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
i915                  535507  3 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
mac_hid                13037  0 
video                  18894  1 i915
drm_kms_helper         47545  1 i915
psmouse                81038  0 
drm                   228750  4 i915,drm_kms_helper
serio_raw              13031  0 
lpc_ich                16925  0 
snd                    56485  14 snd_hda_codec_si3054,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
cfg80211              436177  3 iwl4965,iwlegacy,mac80211
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
floppy                 55441  0 
e1000e                174519  0 
usb_storage            47684  1 
```

---

### Post by carl4926 on 2013-09-20
> [COLOR=#000000][FONT=Ubuntu Mono]Siemens Nixdorf AG SIMATIC NET CP 5611 (Profibus Adapter) [110a:3141][/FONT][/COLOR]Not sure what this part is - are you?

---

