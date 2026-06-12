---
title: "Can't find Dell 1390 wlan minicard after Lubuntu 13.04 install"
date: 2014-07-14
forum: Networking &amp; Wireless
---

### Post by plutokrat on 2014-07-14
hello ich have also a Dell 1390 wlan minicard. but  have an Inspiron E1501

i did the update, but it doesnt work.

here the commands (after your update):

```
computer@Dell:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
computer@Dell:~$ lspci -nnk | grep -iA3 net
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01f5]
    Kernel driver in use: b44
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)

```
```
computer@Dell:~$ lsmod
Module                  Size  Used by
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342263  10 bnep,rfcomm
arc4                   12536  2 
snd_hda_codec_idt      48877  1 
snd_hda_intel          42730  1 
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
radeon               1416373  2 
snd_hwdep              13272  1 snd_hda_codec
joydev                 17101  0 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
b43                   356470  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
dell_wmi               12665  0 
ttm                    72698  1 radeon
snd_rawmidi            25135  1 snd_seq_midi
sparse_keymap          13708  1 dell_wmi
bcma                   42043  1 b43
drm_kms_helper         47182  1 radeon
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
drm                   244037  4 ttm,drm_kms_helper,radeon
mac80211              546051  1 b43
dell_laptop            17808  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
dcdbas                 14448  1 dell_laptop
psmouse                91033  0 
sp5100_tco             13643  0 
cfg80211              409394  2 b43,mac80211
serio_raw              13230  0 
i2c_algo_bit           13197  1 radeon
k8temp                 12842  0 
snd                    60871  12 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_piix4              17723  0 
ssb_hcd                12749  0 
parport_pc             31981  0 
soundcore              12600  1 snd
ppdev                  17391  0 
ati_agp                13177  0 
shpchp                 32128  0 
lp                     13299  0 
wmi                    18673  1 dell_wmi
video                  18903  0 
mac_hid                13037  0 
parport                40836  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
b44                    31275  0 
sdhci_pci              18535  0 
ahci                   25579  2 
sdhci                  37779  1 sdhci_pci
pata_atiixp            13058  0 
mii                    13654  1 b44
libahci                26754  1 ahci
ssb                    51854  3 b43,b44,ssb_hcd
```

---

### Post by chili555 on 2014-07-14
Please hook up the ethernet temporarily and open a terminal and run:```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and let us hear your report.

---

### Post by plutokrat on 2014-07-15
linux-firmware-nonfree is already the newest version

---

### Post by chili555 on 2014-07-15
Please tell us more about "it doesnt work." Could this be the problem? [http://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing](http://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing)

---

### Post by plutokrat on 2014-07-16
thank you, now it works fine :)

---

