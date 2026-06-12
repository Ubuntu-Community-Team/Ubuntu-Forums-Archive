---
title: "dell inspiron 1520 lost wifi ubuntu 12.04"
date: 2014-03-18
forum: Networking &amp; Wireless
---

### Post by Bryant_Arrington on 2014-03-18
house@house-Inspiron-1520:~$ lspci -nnk | grep -iA3 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01f1]
    Kernel driver in use: b44
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
    Kernel driver in use: wl
house@house-Inspiron-1520:~$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
bnep                   17736  2 
rfcomm                 37420  0 
bluetooth             202266  10 bnep,rfcomm
b44                    31292  0 
ssb                    50834  1 b44
lib80211_crypt_tkip    17229  0 
wl                   2906469  0 
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
coretemp               13131  0 
videodev               95806  2 uvcvideo,videobuf2_core
i915                  544217  3 
snd_hda_codec_idt      63896  1 
snd_hda_intel          38307  3 
snd_hda_codec         117617  2 snd_hda_codec_idt,snd_hda_intel
r852                   17873  0 
sm_common              16772  1 r852
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
nand                   53767  2 r852,sm_common
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
kvm                   376584  0 
drm_kms_helper         47545  1 i915
nand_ecc               13105  1 nand
snd_seq_midi           13132  0 
drm                   228489  4 i915,drm_kms_helper
nand_bch               13003  1 nand
snd_seq_midi_event     14475  1 snd_seq_midi
bch                    17226  1 nand_bch
snd_rawmidi            25114  1 snd_seq_midi
i2c_algo_bit           13197  1 i915
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
nand_ids                8547  1 nand
joydev                 17097  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
gpio_ich               13236  0 
mtd                    38922  2 nand,sm_common
dell_laptop            17161  0 
snd_timer              24411  2 snd_pcm,snd_seq
dcdbas                 14021  1 dell_laptop
r592                   17707  0 
snd                    56485  15 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
dell_wmi               12601  0 
memstick               15842  1 r592
soundcore              12600  1 snd
lib80211               14040  2 wl,lib80211_crypt_tkip
psmouse                81065  0 
sparse_keymap          13658  1 dell_wmi
mac_hid                13037  0 
microcode              18286  0 
cfg80211              440887  1 wl
wmi                    18590  1 dell_wmi
video                  18894  1 i915
serio_raw              13031  0 
lpc_ich                16925  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
firewire_ohci          35451  0 
firewire_core          61718  1 firewire_ohci
sdhci_pci              18158  0 
sdhci                  31959  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
house@house-Inspiron-1520:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

I don't know where to go from here.  Help!  
thanks

---

### Post by chili555 on 2014-03-18
Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-lpphy-installer
```Detach the ethernet, reboot and let us hear your report.

---

### Post by Bryant_Arrington on 2014-03-19
Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

---

### Post by chili555 on 2014-03-19
> **Bryant_Arrington said:**
> Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.I don't think that has anything to do with wireless. Did the lpphy firmware download? After a reboot, did the wireless work as expected?

---

### Post by Bryant_Arrington on 2014-03-19
It still doesn't work  Sorry, I said 12.04 but it is 13.04 and now says it will not get any more updates.

---

### Post by Hadaka on 2014-03-19
Hi, you have b44 for your ethernet driver...which is correct
however you have the wl module loaded and this is preventing
your b44 to load. Let's see if we can fix that.. please do..

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe wl
```
that "should" make the wired connection work.
if yes..then do the command chilli555 gave you...the lppy command
thanks.

---

