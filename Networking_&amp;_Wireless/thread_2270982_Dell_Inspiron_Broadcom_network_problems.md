---
title: "Dell Inspiron Broadcom network problems"
date: 2015-03-26
forum: Networking &amp; Wireless
---

### Post by dsnc on 2015-03-26
I'm fairly new to Ubuntu, and I recently installed 14.04 on my Dell Inspiron E1705.  During the install networking (hard-wired) worked fine, and I did all recommended updates, etc.  When I boot the new install I can't get a network connection though, either wired or wireless.  I did follow the advice in this [post]("http://ubuntuforums.org/showthread.php?t=2203842"), but haven't had any luck.  If I boot the LiveCD, everything works fine.  I've appended the info requested in the previous post; I hope somebody can help me out with this one.  Thanks in advance!

_Booting from LiveCD (networking works properly)_


```
uname -a 

Linux ubuntu 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


lspci -nnk | grep -iA2 net

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 9400 Laptop [1028:01cd]
	Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: b43-pci-bridge


lsmod

Module                  Size  Used by
nls_iso8859_1          12713  1 
usb_storage            62209  1 
snd_hda_codec_idt      54645  1 
b43                   387371  0 
snd_hda_intel          52355  3 
dm_crypt               23177  0 
snd_hda_codec         192906  2 snd_hda_codec_idt,snd_hda_intel
gpio_ich               13476  0 
snd_hwdep              13602  1 snd_hda_codec
r852                   18058  0 
dell_wmi               12761  0 
bcma                   52096  1 b43
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
sm_common              16860  1 r852
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
coretemp               13435  0 
nand                   64233  2 r852,sm_common
mac80211              630653  1 b43
dcdbas                 14928  1 dell_laptop
nand_ecc               13312  1 nand
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
joydev                 17381  0 
snd_seq_midi           13324  0 
nand_bch               13227  1 nand
bch                    17397  1 nand_bch
dm_multipath           22873  0 
serio_raw              13462  0 
lpc_ich                21080  0 
snd_seq_midi_event     14899  1 snd_seq_midi
scsi_dh                14882  1 dm_multipath
snd_rawmidi            30144  1 snd_seq_midi
r592                   18023  0 
btusb                  32412  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
nand_ids                8627  1 nand
memstick               16966  1 r592
mtd                    55529  2 nand,sm_common
cfg80211              484040  2 b43,mac80211
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ssb_hcd                12869  0 
bnep                   19624  2 
snd                    69238  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
rfcomm                 69160  8 
bluetooth             391196  22 bnep,btusb,rfcomm
soundcore              12680  1 snd
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
squashfs               48362  1 
overlayfs              27916  1 
nls_utf8               12557  1 
isofs                  39835  1 
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
b44                    40234  0 
psmouse               106678  0 
sdhci_pci              23172  0 
firewire_ohci          40409  0 
sdhci                  43015  1 sdhci_pci
firewire_core          68769  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
mii                    13934  1 b44
radeon               1522422  3 
ssb                    62379  3 b43,b44,ssb_hcd
i2c_algo_bit           13413  1 radeon
ttm                    85115  1 radeon
drm_kms_helper         53081  1 radeon
video                  19476  0 
drm                   303102  5 ttm,drm_kms_helper,radeon
wmi                    19177  1 dell_wmi


rfkill list

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


_Booting from the installed OS (no networking)_

uname -a

Linux Freedom2 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux



lspci -nnk | grep -iA2 net

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 9400 Laptop [1028:01cd]
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: wl



lsmod

Module                  Size  Used by
nls_iso8859_1          12713  1 
usb_storage            62209  1 
gpio_ich               13476  0 
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
ssb                    62379  1 
mii                    13934  0 
snd_hda_codec_idt      54645  1 
coretemp               13435  0 
wl                   4207846  1 
snd_hda_intel          52355  3 
snd_hda_codec         192906  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
joydev                 17381  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
r852                   18058  0 
serio_raw              13462  0 
sm_common              16860  1 r852
snd_timer              29482  2 snd_pcm,snd_seq
rfcomm                 69160  8 
nand                   64233  2 r852,sm_common
bnep                   19624  2 
btusb                  32412  0 
nand_ecc               13312  1 nand
lpc_ich                21080  0 
bluetooth             391196  22 bnep,btusb,rfcomm
nand_bch               13227  1 nand
bch                    17397  1 nand_bch
nand_ids                8627  1 nand
lib80211               14381  1 wl
snd                    69238  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mtd                    55529  2 nand,sm_common
r592                   18023  0 
memstick               16966  1 r592
soundcore              12680  1 snd
cfg80211              484040  1 wl
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
xts                    12914  1 
gf128mul               14951  1 xts
dm_crypt               23177  1 
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
psmouse               106678  0 
firewire_ohci          40409  0 
sdhci_pci              23172  0 
sdhci                  43015  1 sdhci_pci
radeon               1522422  3 
firewire_core          68769  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
i2c_algo_bit           13413  1 radeon
ttm                    85115  1 radeon
drm_kms_helper         53081  1 radeon
video                  19476  0 
drm                   303102  5 ttm,drm_kms_helper,radeon
wmi                    19177  1 dell_wmi



rfkill list

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

---

### Post by jeremy31 on 2015-03-26
Try ```
sudo apt-get install firmware-b43-installer
``` and reboot, the firmware for b43 was removed from linux-firmware-nonfree last August or September

---

### Post by wildmanne39 on 2015-03-26
Please use code tags for terminal output, click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by wildmanne39 on 2015-03-26
I believe the soluton in this post will fix both your issues.
[http://ubuntuforums.org/showthread.php?t=2270549&p=13251419#post13251419](http://ubuntuforums.org/showthread.php?t=2270549&p=13251419#post13251419)
Thanks

---

### Post by dsnc on 2015-03-27
Thank you both for your help--that did the trick!  Thanks also for the posting tip; I'll keep it in mind.  Cheers!

---

### Post by wildmanne39 on 2015-03-27
Glad it worked. Wired connection is working too correct?

---

