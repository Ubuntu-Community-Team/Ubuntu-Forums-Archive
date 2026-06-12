---
title: "Wifi card network unclaimed"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by papa.jinzu on 2014-01-03
Hello,

I have an Asus U56E notebook. Just received a replacement wireless card: Centrino Wireless-N 1030
I do not know how to configure the wifi card. How do I get it working? Says network unclaimed, no 
driver has been installed, do not know how to properly do this. Help would be appreciated.

---

### Post by chili555 on 2014-01-03
Either you installed an older Ubuntu version where your relatively new device isn't covered, or else the driver simply failed to load as expected. First, let's gather some troubleshooting data. Please open a terminal, run and post:> lsb_release -a
lspci -nn | grep 0280
dmesg | grep iwl

---

### Post by papa.jinzu on 2014-01-04
```

lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

```

```

lspci -nn | grep 0280

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 1a)

```

```

dmesg | grep iwl

...nothing displayed

```

---

### Post by praseodym on 2014-01-04
Please show:
```

rfkill list
```
If a block shows "yes" add the following module parameter:

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
and reboot. Check afterwards:
```

rfkill list
lsmod
dmesg | grep iwl
iwconfig
```

---

### Post by chili555 on 2014-01-04
The module iwlwifi isn't loading, but it should. Please try:```
sudo modprobe iwlwifi
dmesg | grep iwl
```

---

### Post by papa.jinzu on 2014-01-04
> **praseodym said:**
> Please show:
```

rfkill list
```

```

echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf

```

```

rfkill list
lsmod
dmesg | grep iwl
iwconfig

```


```
rfkill list
```

```

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```

echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf

```

```

options asus_nb_wmi wapf=1

```

...rebooted

```
rfkill list
```

```

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```

Module                              Size  Used by
nvram                             14362  0 
parport_pc                       32701  0 
ppdev                             17671  0 
binfmt_misc                     17468  1 
arc4                                12608  2 
carl9170                          87065  0 
ath                                 23827  1 carl9170
mac80211                      597268  1 carl9170
uvcvideo                         80885  0 
videobuf2_vmalloc           13216  1 uvcvideo
videobuf2_memops          13362  1 videobuf2_vmalloc
videobuf2_core                40499  1 uvcvideo
cfg80211                       480503  3 ath,mac80211,carl9170
videodev                       133509  2 uvcvideo,videobuf2_core
btusb                              28267  0 
bluetooth                       372041  1 btusb
x86_pkg_temp_thermal     14162  0 
intel_powerclamp             14705  0 
coretemp                        13435  0 
kvm_intel                     138567  0 
kvm                             431720  1 kvm_intel
joydev                           17377  0 
crct10dif_pclmul              14289  0 
crc32_pclmul                  13113  0 
ghash_clmulni_intel         13259  0 
aesni_intel                     55624  1 
aes_x86_64                    17131  1 aesni_intel
lrw                                13286  1 aesni_intel
gf128mul                        14951  1 lrw
glue_helper                     13990  1 aesni_intel
ablk_helper                     13597  1 aesni_intel
cryptd                            20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
asus_nb_wmi                  16990  0 
asus_wmi                       24191  1 asus_nb_wmi
sparse_keymap               13948  1 asus_wmi
snd_hda_codec_hdmi       41117  1 
snd_hda_codec_realtek    55704  1 
i915                            661261  2 
snd_hda_intel                 48171  3 
snd_hda_codec              188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep                     13602  1 snd_hda_codec
snd_pcm                       102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc                18710  2 snd_pcm,snd_hda_intel
snd_seq_midi                  13324  0 
snd_seq_midi_event         14899  1 snd_seq_midi
snd_rawmidi                   30095  1 snd_seq_midi
snd_seq                         61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device               14497  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper             52710  1 i915
drm                             297056  3 i915,drm_kms_helper
microcode                      23576  0 
psmouse                        97655  0 
snd_timer                      29433  2 snd_pcm,snd_seq
snd                               69141  17      
 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
video                            19318  2 i915,asus_wmi
soundcore                      12680  1 snd
lp                                 17759  0 
mei_me                         18421  0 
parport                          42299  3 lp,ppdev,parport_pc
serio_raw                       13413  0 
i2c_algo_bit                    13413  1 i915
wmi                              19070  1 asus_wmi
mac_hid                         13205  0 
mei                               77782  1 mei_me
lpc_ich                           21080  0 
ahci                   25819  4 
libahci                31928  1 ahci
atl1c                  46086  0 

```

[CODE/
dmesg | grep iwl

...nothing displayed
[/CODE]

```
iwconfig
```

```

wlan1     IEEE 802.11bgn  ESSID:"bluesky2"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: C8:60:00:AB:74:0A   
          Bit Rate:54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:150   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

```

---

### Post by praseodym on 2014-01-04
Unplug your stick and check chili555's posting

---

### Post by papa.jinzu on 2014-01-04
> **chili555 said:**
> The module iwlwifi isn't loading, but it should. Please try:```
sudo modprobe iwlwifi
dmesg | grep iwl
```

Nothing displayed and sill cannot use the wireless card Intel Centrino 1030.

I unplugged the stick and ran the commands mention by chili555. But nothing was displayed and the wifi card is not working.

---

### Post by praseodym on 2014-01-04
Driver is installed?
```

modinfo iwlwifi
```

---

### Post by papa.jinzu on 2014-01-04
> **praseodym said:**
> Driver is installed?
```

modinfo iwlwifi
```

I think so. I downloaded iwlwifi-6000g2b-ucode-18.168.6.1 driver directly from Intel for Intel Centrino 1030.
Here is the output from the command.

```
filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     B690FF1883B2CA894BA5B6C
alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000370bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000472bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000272bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C02Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C26Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C760bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C770bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C06Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000402Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005070bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000446Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000426Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000406Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000446Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd0000426Abc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000406Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C228bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001318bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001328bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001308bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001118bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001128bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001108bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
```

---

### Post by praseodym on 2014-01-04
Are there others installed?
```

locate iwlwifi.ko | grep lib
grep iwl /etc/modprobe.d/*
```

---

### Post by papa.jinzu on 2014-01-04
```

locate iwlwifi.ko | grep lib

```

```
/lib/modules/3.11.0-14-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.2.0-52-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.2.0-57-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.2.0-58-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.2.0-58-generic/updates/cw-3.8/iwlwifi.ko
/lib/modules/3.5.0-44-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
/lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
```

```
grep iwl /etc/modprobe.d/*
```

```
/etc/modprobe.d/iwlwifi.conf:# /etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/iwlwifi.conf:# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
/etc/modprobe.d/iwlwifi.conf:# microcode file installed on the system.  When removing iwlwifi, first
/etc/modprobe.d/iwlwifi.conf:# remove the iwl?vm module and then iwlwifi.
/etc/modprobe.d/iwlwifi.conf:remove iwlwifi \
/etc/modprobe.d/iwlwifi.conf:(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \

```

---

### Post by praseodym on 2014-01-04
Load the modules like this:
```

sudo modprobe -v iwldvm
sudo modprobe -v iwlwifi
```

---

### Post by papa.jinzu on 2014-01-04
> **praseodym said:**
> Load the modules like this:
```

sudo modprobe -v iwldvm
sudo modprobe -v iwlwifi
```

Do I need to restart after this? It still is not working.
Is the asus u56e not compatible with intel centrino 1030?

---

### Post by chili555 on 2014-01-04
You have the correct driver on your system. It claims your device. The module *iwlwifi* loads without complaint. Something, we wonder what, is stopping it from creating an interface wlan0 and marching forward. Please reboot so you have a clean slate and, with the USB detached, run:```
sudo modprobe iwlwifi  >  wifi.txt
iwconfig  >>  wifi.txt
dmesg  >>  wifi.txt
```Find the file wifi.txt in your user directory and post it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by papa.jinzu on 2014-01-04
> **chili555 said:**
> You have the correct driver on your system. It claims your device. The module *iwlwifi* loads without complaint. Something, we wonder what, is stopping it from creating an interface wlan0 and marching forward. Please reboot so you have a clean slate and, with the USB detached, run:```
sudo modprobe iwlwifi  >  wifi.txt
iwconfig  >>  wifi.txt
dmesg  >>  wifi.txt
```Find the file wifi.txt in your user directory and post it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)


sudo modprobe iwlwifi > wifi.txt (created a blank txt file named wifi)
iwconfig >> wifi.txt (did not add any data to this file wifi.txt)
dmesg >> wifi.txt (see here: [http://paste.ubuntu.com/6694472/](http://paste.ubuntu.com/6694472/))

---

### Post by praseodym on 2014-01-05
Thats weird. Please check in the BIOS settings if the wifi can be booted/started _before_ the operating system

---

### Post by chili555 on 2014-01-05
Weird, indeed! 

I noticed this:> [    0.208303] pci 0000:02:00.0: [[COLOR="#FF0000"]8086:008a[/COLOR]] type 00 class 0x028000
[    0.208348] pci 0000:02:00.0: reg 0x10: [mem 0xde800000-0xde801fff 64bit]
[    0.208572] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.208619] pci 0000:02:00.0: [COLOR="#FF0000"]System wakeup disabled by ACPI[/COLOR]The pci.id 8086:008a is your wireless card. It is on PCI bus 02:00:0. It appears that some ACPI setting prevents the device from resuming from suspend. Are there any unusual settings related to ACPI in the BIOS? Generally, setting the BIOS to defaults will work well for Ubuntu.

I also notice this in your boot options:> pcie_aspm=forceThis may or may not be related. Frankly, this is beyond the areas that I usually study, so I can't recommend further. Perhaps praseodym has some insights.

I am stumped.

---

### Post by praseodym on 2014-01-05
We had something similar in the German forum, check these boot options in the grey boxes:

[http://forum.ubuntuusers.de/topic/wlan-hardware-geht-nicht-notebook/2/#post-6231507](http://forum.ubuntuusers.de/topic/wlan-hardware-geht-nicht-notebook/2/#post-6231507)

The problem was there, that either USB or WLAN worked. After changes in the **/boot/grub/grug.cfg** do
```

sudo update-grub
```
and reboot.
If you are unsure what to do, come back.

---

### Post by papa.jinzu on 2014-01-05
This seemed to get the job done on the German forums.

```
 acpi=force pnpbios=off pci=acpi acpi_irq_nobalance irqpoll
```

But I have none of these found in my grub.cfg file.
My bios does not mention anything related to ACPI.
What to do?

Also I reset the defaults in BIOS but the card is not working.

---

### Post by praseodym on 2014-01-05
Sorry, it has to be the file /etc/default/grub:

```
gksudo gedit /etc/default/grub
```

Add the parameters one after another or in combination to the line:

```
[COLOR="#FF0000"]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR]="quiet splash video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap"
```
(this is my one, yours will look different!) so that it looks e.g. like

```
[COLOR="#FF0000"]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR]="quiet splash video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap [COLOR="#FF0000"]acpi=force pnpbios=off pci=acpi acpi_irq_nobalance irqpoll[/COLOR]"
```
Save, close the editor and
```

sudo update-grub
```
after each try. Reboot.

---

### Post by papa.jinzu on 2014-01-05
o

---

### Post by praseodym on 2014-01-05
Typo

**gksudo gedit /etc/default/grub**

;)

---

### Post by papa.jinzu on 2014-01-05
Am getting the following warning in terminal after saving the file and exiting the file editor

```
(gedit:2528): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:2528): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

having to use recovery mode in xubuntu because mouse and touchpad stopped working after
changing the file.

---

### Post by papa.jinzu on 2014-01-05
I am able to use my touchpad again. I had a problem with the setting
```
acpi=off
```
my file looks like this now:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.lvds_downclock=1 drm.vblankoffdelay=1  i915.semaphores=1
pnpbios=off acpi=force irqpoll pci=acpi"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

unfortunately the wifi card is not working from the changes.
also is it worth noting the card does not work in my windows partition either. even after
downloading the drivers directly from intel.

---

### Post by praseodym on 2014-01-05
Maybe its broken?! Reverse the settings and check if Windows shuts the card off.

---

### Post by papa.jinzu on 2014-01-05
What do you mean shut the card off? The card is recognized as a network controller with the yellow icon meaning it is not configured. The device ID and vendor ID define it as Intel Centrino Wireless N 1030 wifi card. But it will not update in device manager. I am beginning to think the card is not compatible with my laptop...

With this card not working, I have to buy another wifi card. Does anyone have any suggestions for some that are know to work?

---

