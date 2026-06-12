---
title: "Netgear A620 Connects to Wifi, Stay Connected, Cannot Resolve Any Sites After ~4 minu"
date: 2015-02-26
forum: Networking &amp; Wireless
---

### Post by Guxx on 2015-02-26
Hello,

I used this to get the USB Netgear Adapter to work ([http://askubuntu.com/questions/460277/how-to-get-netgear-a6200-to-work-on-14-04](http://askubuntu.com/questions/460277/how-to-get-netgear-a6200-to-work-on-14-04)). The wifi stays connect without issue, but fails to resolve any sites after about ~4 mins. 


```
$ cat /etc/lsb-release; uname -aDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"
Linux guxx-Desk 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

```
$ lspci -nnk | grep -iA2 net04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8439]
    Kernel driver in use: sky2
```

```
$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 125f:c72a A-DATA Technology Co., Ltd. 
Bus 002 Device 002: ID 1c6b:a222 Philips & Lite-ON Digital Solutions Corporation DVD Writer Slimtype eTAU108
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0846:9050 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 06a3:0ccb Saitek PLC 
Bus 004 Device 002: ID 046d:c22d Logitech, Inc. G510 Gaming Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan1     IEEE 802.11g  ESSID:"ATT379"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 60:FE:20:77:0C:1A   
          Bit Rate=130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:103  Invalid misc:39495   Missed beacon:0
```

```

$ rfkill list all
$ lsmod
Module                  Size  Used by
cfg80211              494330  0 
nls_iso8859_1          12713  1 
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  2 hid_generic,usbhid
snd_hda_codec_hdmi     47548  2 
bnep                   19624  2 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
binfmt_misc            17468  1 
ndiswrapper           283985  0 
uas                    23159  0 
usb_storage            66545  2 uas
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_hda_codec_via      31956  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_via
kvm_amd                60328  0 
kvm                   452043  1 kvm_amd
snd_hda_intel          30469  7 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
serio_raw              13483  0 
k10temp                13144  0 
edac_core              56549  0 
edac_mce_amd           22578  0 
sp5100_tco             13999  0 
i2c_piix4              22166  0 
radeon               1408739  5 
asus_atk0110           18666  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
ttm                    85314  1 radeon
snd                    79468  25 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         61574  1 radeon
parport_pc             32741  0 
drm                   311018  8 ttm,drm_kms_helper,radeon
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
wmi                    19193  0 
i2c_algo_bit           13413  1 radeon
soundcore              15047  2 snd,snd_hda_codec
mac_hid                13227  0 
shpchp                 37047  0 
pata_acpi              13053  0 
psmouse               106561  0 
pata_atiixp            13279  0 
sky2                   58206  0 
firewire_ohci          40551  0 
firewire_core          68769  1 firewire_ohci
ahci                   34062  2 
pata_jmicron           12775  0 
crc_itu_t              12707  1 firewire_core
libahci                32424  1 ahci
```

Thanks!

---

### Post by Guxx on 2015-02-26
As a quick update, it seems like once a speed of 1G/S is reached the adapter locks up. I tested this out a few times with Steam, and every time the rate hit ~900MB/S the speed tailed off to 0 very quickly (within 5 seconds). This doesn't seem like a time issue.

---

