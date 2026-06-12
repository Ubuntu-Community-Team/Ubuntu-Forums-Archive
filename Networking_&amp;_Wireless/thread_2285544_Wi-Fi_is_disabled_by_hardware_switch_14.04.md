---
title: "Wi-Fi is disabled by hardware switch 14.04"
date: 2015-07-06
forum: Networking &amp; Wireless
---

### Post by jayden4 on 2015-07-06
Hi,
I recently installed Ubuntu 14.04 to my old Lenovo T400 and my wireless connection does not want to connect, and it says its hard blocked. Ive tryed alt+f5 to turn on wireless but it does not work.

[HTML]0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes[/HTML]

Here is my lsmod

[HTML]Module                  Size  Used by
nls_utf8               12557  1 
udf                    93821  1 
dm_crypt               23216  0 
wl                   6367833  0 
arc4                   12608  2 
uvcvideo               81073  0 
iwldvm                232283  0 
mac80211              652777  1 iwldvm
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_codec_conexant    23109  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_conexant
snd_hda_intel          30469  3 
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
snd_hda_controller     30228  1 snd_hda_intel
pcmcia                 62299  0 
iwlwifi               179412  1 iwldvm
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
snd_hda_codec         139682  4 snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
yenta_socket           41040  0 
media                  21903  2 uvcvideo,videodev
coretemp               13441  0 
snd_hwdep              17698  1 snd_hda_codec
pcmcia_rsrc            18407  1 yenta_socket
kvm                   452047  0 
thinkpad_acpi          81027  0 
cfg80211              494362  4 wl,iwlwifi,mac80211,iwldvm
snd_pcm               104112  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
pcmcia_core            23592  3 pcmcia,pcmcia_rsrc,yenta_socket
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
joydev                 17393  0 
serio_raw              13483  0 
nvram                  14411  1 thinkpad_acpi
lpc_ich                21093  0 
mei_me                 19696  0 
shpchp                 37047  0 
snd                    79468  17 snd_hwdep,snd_timer,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
mei                    87875  1 mei_me
soundcore              15047  2 snd,snd_hda_codec
bnep                   19624  2 
mac_hid                13227  0 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
firewire_ohci          40551  0 
firewire_core          68769  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
i915                  906106  3 
psmouse               106722  0 
ahci                   34062  2 
i2c_algo_bit           13413  1 i915
libahci                32424  1 ahci
drm_kms_helper         61574  1 i915
drm                   311018  5 i915,drm_kms_helper
e1000e                226396  0 
ptp                    19395  1 e1000e
pps_core               19382  1 ptp
video                  20128  1 i915
[/HTML]

---

### Post by wildmanne39 on 2015-07-06
Thread moved to networking and wireless!

---

### Post by chili555 on 2015-07-06
What is the position of this switch? [http://i.stack.imgur.com/eecUT.jpg](http://i.stack.imgur.com/eecUT.jpg)

---

### Post by jayden4 on 2015-07-06
WOW, I feel dumb now. Thank you so much!:smile::smile:

---

### Post by chili555 on 2015-07-06
We're glad it's working by whatever means. Have fun!

---

