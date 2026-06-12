---
title: "error during the CUPS operation: client-error-not-possible"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by al.adab on 2010-05-05
this is turning into a rather frustrating experience...

on a fresh installation of Ubuntu 10.04, I'm no longer able to install a (printer) HP Photosmart C4485. 

This is what I've done: 

- I installed (what I thought I previously did) by typing *sudo apt-get install hplip-gui*

- went to system>administration>printing

- clicked on "ADD"...

...and a "New printer" window appears...in the previous installation of Ubuntu 10.04, the printer appeared in the box. Now it doesn't. It's locally installed (it's not a network printer, but if I try to through the "Network printer" option, I eventually get an error message re: some "CUPS" (see title). 

Can you please help? Thanks.

---

### Post by al.adab on 2010-05-05
I don't know if it's of any help, but here it is

[I]~$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
binfmt_misc             6587  1 
ipt_REJECT              1928  1 
ppdev                   5259  0 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  7 
ipt_addrtype            1631  4 
xt_state                1098  7 
joydev                  8708  0 
ip6table_filter         2343  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
arc4                    1153  2 
ip6_tables             11227  1 ip6table_filter
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
nf_nat_irc              1124  0 
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
snd_seq_dummy           1338  0 
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
snd_seq_oss            26726  0 
nf_conntrack_ipv4      10672  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
snd_seq_midi            4557  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_rawmidi            19056  1 snd_seq_midi
nf_conntrack           61583  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          2271  1 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  3 
ip_tables               9991  1 iptable_filter
iwl3945                68727  0 
drm_kms_helper         29297  1 i915
dell_wmi                1793  0 
x_tables               14299  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlcore               105922  1 iwl3945
drm                   162471  4 i915,drm_kms_helper
intel_agp              24177  2 i915
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
soundcore               6620  1 snd
dell_laptop             6856  0 
mac80211              204922  2 iwl3945,iwlcore
uvcvideo               56990  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
dcdbas                  5422  1 dell_laptop
i2c_algo_bit            5028  1 i915
led_class               2864  3 iwl3945,iwlcore,sdhci
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
cfg80211              126485  3 iwl3945,iwlcore,mac80211
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
r8169                  33884  0 
mii                     4381  1 r8169
ahci                   32008  2 
[/I]

---

### Post by al.adab on 2010-05-05
tried the following: 

[I]
sudo apt-get remove hplip-gui[/I]

*sudo apt-get install hplip-gui*

plus Applications>Office>HPLIP Utility (icon appears on panel)

plus right-click on HP icon>HP Device manager

somehow the printer was recognized and added...

---

### Post by al.adab on 2010-05-05
...forgotten to add that it's probably the first time I've felt I have no control whatsoever on things related to Ubuntu - despite my limited knowledge of its working...I have no idea of how that printer was eventually added to my computer!

---

