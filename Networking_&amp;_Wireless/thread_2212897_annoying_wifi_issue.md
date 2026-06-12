---
title: "annoying wifi issue"
date: 2014-03-23
forum: Networking &amp; Wireless
---

### Post by Jacob_Jackson on 2014-03-23
ok, so here lies the problem.  after freshly installin ubuntu 12.10, my wireless card wasnt showing any connections.after installing the b43, it started showing them. yay. new problem arised however. i stay at ft. Lee, and the wifi here is Czee wifi. decent service, however when i try to connect, it gives me issues. i try to open my web browser, and it wont even take me to the login website. any ideas? im not extremely edumacated in linux (yet) so any help? id greatly appreciate it :D

---

### Post by Hadaka on 2014-03-23
hi, let's verify b43 is the best driver for you.
please post the output of..
```
lspci -nnk | grep -iA2 net
lsmod
cat /etc/network/interfaces
cat  /etc/modules
```
thanks.

---

### Post by Jacob_Jackson on 2014-03-23
jacob@PVT-Jackson:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44
--
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
jacob@PVT-Jackson:~$ lsmod
Module                  Size  Used by
rndis_wlan             28041  0 
rndis_host             13567  1 rndis_wlan
cdc_ether              13278  1 rndis_host
usbnet                 25169  3 rndis_wlan,rndis_host,cdc_ether
arc4                   12473  2 
joydev                 17161  0 
coretemp               13168  0 
gpio_ich               13159  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            17161  0 
dcdbas                 14054  1 dell_laptop
snd_hda_codec_idt      59761  1 
microcode              18209  0 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
r852                   17905  0 
sm_common              16737  1 r852
nand                   49496  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    38602  2 sm_common,nand
r592                   17707  0 
psmouse                84843  0 
parport_pc             31968  0 
nand_bch               13003  1 nand
bch                    17199  1 nand_bch
memstick               15842  1 r592
rfcomm                 37276  0 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
nand_ecc               13070  1 nand
bnep                   17707  2 
bluetooth             183228  10 rfcomm,bnep
ppdev                  12817  0 
serio_raw              13031  0 
lpc_ich                16925  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
b43                   347284  0 
mac80211              461161  1 b43
snd                    61991  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ssb_hcd                12749  0 
cfg80211              175375  3 rndis_wlan,b43,mac80211
bcma                   34483  1 b43
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
ext2                   67204  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
xts                    12723  2 
gf128mul               14503  1 xts
dm_crypt               22402  1 
i915                  457161  3 
drm_kms_helper         45271  1 i915
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
sdhci_pci              18155  0 
b44                    31326  0 
sdhci                  27830  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
wmi                    18590  1 dell_wmi
ssb                    50087  3 b43,ssb_hcd,b44
video                  18847  1 i915
usb_storage            39350  0 
jacob@PVT-Jackson:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
jacob@PVT-Jackson:~$ cat  /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
jacob@PVT-Jackson:~$ 



this is what i get.

---

### Post by Hadaka on 2014-03-23
looks like everything you need is there for the type of cards
you have. let's do a couple things just to polish the edges a
bit.  from a wired connection...please do..
this file may or may not be there...ignore any error..
  ```
rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do...
this file has a few more b43 goodies and your 14e4:4311 card
prefers this driver..please do..
```
sudo apt-get install linux-firmware-nonfree
```
then check your encryption settings...omitt any tkip..and try to go with wpa2
thanks.

---

### Post by Jacob_Jackson on 2014-03-23
another new question. how do i change that in my encription settings? i didnt find it anywere in my settings.
also. its a wireless network that requires you to connect to the wifi, then open browser and log in. so changing the wifi settings would be kind of pointless wouldnt it? its not like a personal router.

---

### Post by Hadaka on 2014-03-23
yeah...usual answers dont apply here..try this..see if you can ping google
```
ping -c5 8.8.8.8
sudo iwlist wlan0 scan

```
you might try changing your dns to 8.8.8.8,8.8.4.4
google.

---

### Post by Jacob_Jackson on 2014-03-23
and now its really throwing me off. now it randomly connects to the wifi  access point, i conncted to my roomates wifi hotspot no problem, but it  was refusing to allow me to conect to the czee network. now its  connecting like its not a problem. any clues as is to why?

thank you for your help by the way. the community always seems to help with my problems.

---

