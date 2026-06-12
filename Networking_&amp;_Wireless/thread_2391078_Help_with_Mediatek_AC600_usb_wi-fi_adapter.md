---
title: "Help with Mediatek AC600 usb wi-fi adapter"
date: 2018-05-05
forum: Networking &amp; Wireless
---

### Post by serapis5 on 2018-05-05
Hi:

I know my profile says I'm running 17.10 but there is no option yet to change it to 18.04.  At any rate, I just purchased a mediatek AC600 usb wi-fi adapter with MT7610U chipset, which states that it is compatible with Linux and the driver disk which came with the adapter came with Linux drivers (source code).  I have seen issues with this driver all over the forums from versions past and tried installing various "corrected" options, but all with the same result:  they fail to Make giving "Error 2".  Does anyone have any suggestions on how I can obtain a good source code to compile from or even a .deb file that I can't locate on the internet?  Any help is greatly appreciated.

Bart

---

### Post by praseodym on 2018-05-06
Please show
```

lsusb
lsmod
iwconfig
```

---

### Post by serapis5 on 2018-05-06
```
lsusb

Bus 001 Device 004: ID 1307:0330 Transcend Information, Inc. 63-in-1 Multi-Card Reader/Writer
Bus 001 Device 005: ID 0e8d:7610 MediaTek Inc. 
Bus 001 Device 006: ID 0781:5575 SanDisk Corp. 
Bus 001 Device 002: ID 04f9:0021 Brother Industries, Ltd HL-5140 series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
```
lsmod

Module                  Size  Used by
nls_iso8859_1          16384  1
ccm                    20480  6
edac_mce_amd           28672  0
kvm_amd                86016  0
snd_hda_codec_realtek   102400  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
kvm                   593920  1 kvm_amd
irqbypass              16384  1 kvm
input_leds             16384  0
serio_raw              16384  0
k10temp                16384  0
snd_hda_codec_hdmi     49152  1
arc4                   16384  2
snd_hda_intel          40960  8
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
ath5k                 147456  0
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  27 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
usblp                  20480  0
ath                    28672  1 ath5k
mac80211              778240  1 ath5k
soundcore              16384  1 snd
shpchp                 36864  0
nvidia_uvm            757760  0
cfg80211              622592  3 mac80211,ath,ath5k
mac_hid                16384  0
wmi                    24576  0
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
uas                    24576  0
usb_storage            69632  2 uas
nvidia_drm             40960  6
nvidia_modeset       1110016  7 nvidia_drm
nvidia              14340096  446 nvidia_modeset,nvidia_uvm
drm_kms_helper        167936  1 nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   401408  9 nvidia_drm,drm_kms_helper
psmouse               147456  0
ipmi_devintf           20480  0
pata_acpi              16384  0
ipmi_msghandler        53248  2 nvidia,ipmi_devintf
forcedeth              69632  0
sata_nv                32768  1
pata_amd               20480  0
i2c_nforce2            16384  0
```

```
iwcofig

lo        no wireless extensions.

wlp1s6    IEEE 802.11  ESSID:"ARACHUS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 34:68:95:F5:CF:FB   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:134  Invalid misc:8657   Missed beacon:0

enp0s7    no wireless extensions.
```

---

### Post by praseodym on 2018-05-06
[https://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver](https://www.tp-link.com/lb/download/Archer-T2U_V1.html#Driver)

Try this linux driver. It compiled up to kernel 4.4 here. Maybe it works, too. What about the internal Atheros card (module ath5k)?

---

### Post by slickymaster on 2018-05-07
> **serapis5 said:**
> Hi:

I know my profile says I'm running 17.10 but there is no option yet to change it to 18.04.  ........

Bart

I've correct that for you.

---

### Post by chili555 on 2018-05-07
Please see my post #18 here: [https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u](https://ubuntuforums.org/showthread.php?t=2367163&highlight=mt7610u)

---

### Post by serapis5 on 2018-05-07
That works okay at 2.4 Ghz.  The goal was to get a card that supported 5 Ghz.

---

### Post by serapis5 on 2018-05-07
Chili555::

I tried your solution but it still comes out with errors in the 4.15 kernal (couldn't even get to step 2).  Thanks for trying though.

---

### Post by chili555 on 2018-05-07
> **serapis5 said:**
> Chili555::

I tried your solution but it still comes out with errors in the 4.15 kernal (couldn't even get to step 2).  Thanks for trying though.*What *solution?? My post #18 to which I referred you, says, pretty clearly that it can't and won't ever work. Did you read this?> Put this under the wheel of your car as you drive down to the store to get a different device.

---

### Post by jeremy31 on 2018-05-07
Even some of the latest code on github won't even compile in kernel 4.15, like [https://github.com/rebrane/mt7610u](https://github.com/rebrane/mt7610u) even though it claims to work in other kernels.  We have seen code for this chipset compile and not work at all

---

