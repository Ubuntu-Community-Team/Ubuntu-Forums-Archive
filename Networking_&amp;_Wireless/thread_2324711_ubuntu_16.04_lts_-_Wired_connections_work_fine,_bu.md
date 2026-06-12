---
title: "ubuntu 16.04 lts - Wired connections work fine, but the wifi doesn't."
date: 2016-05-15
forum: Networking &amp; Wireless
---

### Post by guillermo20 on 2016-05-15
[COLOR=#000000]I'm running ubuntu 16.04 lts

i [/COLOR][COLOR=#000000]am not be [/COLOR][COLOR=#000000]able to lo[/COLOR][COLOR=#000000]ad [/COLOR][COLOR=#000000]any webp[/COLOR][COLOR=#000000]age despite of be connected to my home network[/COLOR][COLOR=#000000]

I tried re[/COLOR]ading many posts of this page to fix this problem, running many commands but nothing seems to work

comm[COLOR=#000000]ands th[/COLOR][COLOR=#000000]at i [/COLOR][COLOR=#000000]alre[/COLOR][COLOR=#000000]ady used being wired connected:
[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]```
sudo apt-get update
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get dist-upgrade
```[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
let me show you guys this:

```

guillermo@guillermo-Aspire-5735:~$ lspci | grep Wireless
03:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)
guillermo@guillermo-Aspire-5735:~$ 

```

```

guillermo@guillermo-Aspire-5735:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"
Linux guillermo-Aspire-5735 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:52:40 UTC 2016 i686 i686 i686 GNU/Linux
guillermo@guillermo-Aspire-5735:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 16)
    Subsystem: Acer Incorporated [ALI] 88E8071 PCI-E Gigabit Ethernet Controller [1025:013f]
    Kernel driver in use: sky2
    Kernel modules: sky2
03:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Quanta Microsystems, Inc EM303 802.11bgn Wireless Mini PCIe Card [AR9281] [1a32:0303]
    Kernel driver in use: ath9k
guillermo@guillermo-Aspire-5735:~$ iwconfig
lo        no wireless extensions.


enp2s0    no wireless extensions.


wlp3s0    IEEE 802.11bgn  ESSID:"INFINITUMx2re"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: D4:40:F0:91:1D:50   
          Bit Rate=11 Mb/s   Tx-Power=17 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0


guillermo@guillermo-Aspire-5735:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
guillermo@guillermo-Aspire-5735:~$ lsmod
Module                  Size  Used by
drbg                   28672  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek    73728  1
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
arc4                   16384  2
snd_hda_intel          36864  3
snd_hda_codec         118784  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           61440  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
uvcvideo               77824  0
snd_hwdep              16384  1 snd_hda_codec
videobuf2_vmalloc      16384  1 uvcvideo
snd_pcm                94208  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
ath9k                 135168  0
videobuf2_memops       16384  1 videobuf2_vmalloc
ath9k_common           36864  1 ath9k
videobuf2_v4l2         28672  1 uvcvideo
ath9k_hw              458752  2 ath9k_common,ath9k
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              155648  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
snd_seq_midi           16384  0
ath                    24576  3 ath9k_common,ath9k,ath9k_hw
snd_seq_midi_event     16384  1 snd_seq_midi
mac80211              659456  1 ath9k
media                  24576  2 uvcvideo,videodev
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
cfg80211              499712  4 ath,ath9k_common,ath9k,mac80211
coretemp               16384  0
snd                    69632  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
input_leds             16384  0
soundcore              16384  1 snd
joydev                 20480  0
serio_raw              16384  0
lpc_ich                20480  0
shpchp                 32768  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2
ums_realtek            20480  0
uas                    20480  0
usb_storage            57344  2 uas,ums_realtek
i915                 1130496  5
mxm_wmi                16384  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        131072  1 i915
syscopyarea            16384  1 drm_kms_helper
psmouse               118784  0
ahci                   36864  1
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
libahci                32768  1 ahci
fb_sys_fops            16384  1 drm_kms_helper
drm                   311296  7 i915,drm_kms_helper
sky2                   53248  0
wmi                    20480  1 mxm_wmi
video                  36864  1 i915
fjes                   28672  0


```

---

### Post by chili555 on 2016-05-16
> but the wifi doesn't.But it sure looks like it is connected and with good signal strength:> wlp3s0    IEEE 802.11bgn  ESSID:"[COLOR="#FF0000"]INFINITUMx2re[/COLOR]"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: D4:40:F0:91:1D:50   
          Bit Rate=11 Mb/s   Tx-Power=17 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=[COLOR="#FF0000"]70/70 [/COLOR] Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0Perhaps you can expand a bit on what you mean by "...wifi doesn't." 

We see nothing whatever wrong here, so you'll have to tell us in detail what is not working.

---

### Post by guillermo20 on 2016-05-16
Yes in f[COLOR=#000000]act,[/COLOR][COLOR=#000000] the router is just one room [/COLOR][COLOR=#000000]aw[/COLOR][COLOR=#000000]ay,
ple[/COLOR][COLOR=#000000]ase forgive me[/COLOR][COLOR=#000000], english is not my n[/COLOR][COLOR=#000000]ative lengu[/COLOR][COLOR=#000000]age
[/COLOR][COLOR=#000000]Well, i c[/COLOR][COLOR=#000000]an connect [/COLOR][COLOR=#000000]and disconnect [/COLOR][COLOR=#000000]to my home network[/COLOR] "INFINITUMx2re"[COLOR=#000000]* e*[/COLOR]asily, but i[COLOR=#000000]'m not still be [/COLOR]able to _load any webpage from any browser_ included in this copy of ubuntu[COLOR=#000000],
only being wired connected i c[/COLOR]an
pd: i[COLOR=#000000]'m gonn[/COLOR][COLOR=#000000]a[/COLOR][COLOR=#000000] correct the thre[/COLOR][COLOR=#000000]ad[/COLOR][COLOR=#000000]'[/COLOR][COLOR=#000000]s [/COLOR][COLOR=#000000]mist[/COLOR][COLOR=#000000]ake th[/COLOR][COLOR=#000000]anks[/COLOR]

---

### Post by Frogs Hair on 2016-05-16
Closed per OP request.

---

### Post by wildmanne39 on 2016-05-16
Please provide your solution so the whole community can benefit from the answer. Then please mark thread solved if you can after it has been closed.
Thanks

---

