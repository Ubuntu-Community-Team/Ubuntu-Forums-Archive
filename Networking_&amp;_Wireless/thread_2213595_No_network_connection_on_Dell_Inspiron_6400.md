---
title: "No network connection on Dell Inspiron 6400"
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by Justice_Simon on 2014-03-27
Hello all, I am have a problem with my network connection on the aforementioned laptop. I am using Ubuntu 13.10 (dual booting with XP) and have read a bunch of the other problems and solutions for this combination, but none of them are working for me. I have figured out that the problem (as far as I can see) is that Ubuntu is blocking the B44 driver. Image of hardware (hope this helps): [http://i.imgur.com/q9eeBoW.png?1](http://i.imgur.com/q9eeBoW.png?1). Any help would be appreciated! And thanks anyways.

---

### Post by Hadaka on 2014-03-27
Hi, please do..
*Ignore any errors
also IGNORE ANY offer of proprietary or additional drivers...you do NOT want these.
```
sudo modprobe -rf wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
boot..your wired connection should be working.
from the wired internet connected ethernet,
  please do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
your wireless connection should now be working.

---

### Post by Justice_Simon on 2014-03-27
I did "[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get remove --purge bcmwl-kernel-source" last time when trying to solve this and it just sat there, how long should it take?[/FONT][/COLOR]

---

### Post by Hadaka on 2014-03-27
it should say..
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
but...no big deal...run each command anyway...IF
 you dont get the connecion working...post the output of..
```
lsmod
```
thanks.

---

### Post by Justice_Simon on 2014-03-27
It didnt work, the "[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -rf wl[/FONT][/COLOR]" said that the process was in use and "[COLOR=#000000][FONT=Ubuntu Mono]sudo rm /etc/modprobe.d/blacklist-bcm43.conf[/FONT][/COLOR]" said no such file exists? lsmod said 
> Module                  Size  Used bynls_iso8859_1          12617  1 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323534  10 bnep,rfcomm
coretemp               13195  0 
gpio_ich               13229  0 
joydev                 17097  0 
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
dell_laptop            17161  0 
dcdbas                 14383  1 dell_laptop
b43                   356285  0 
bcma                   40966  1 b43
microcode              18830  0 
r852                   17925  0 
mac80211              513247  1 b43
radeon               1307301  3 
sm_common              16772  1 r852
nand                   58914  2 r852,sm_common
psmouse                90642  0 
serio_raw              13189  0 
nand_ecc               13136  1 nand
nand_bch               13067  1 nand
r592                   17711  0 
lpc_ich                16864  0 
cfg80211              401436  2 b43,mac80211
ttm                    71886  1 radeon
nand_ids                8547  1 nand
ssb_hcd                12749  0 
memstick               16008  1 r592
bch                    17197  1 nand_bch
drm_kms_helper         46867  1 radeon
mtd                    52735  2 nand,sm_common
drm                   242354  5 ttm,drm_kms_helper,radeon
snd_hda_codec_idt      44605  1 
i2c_algo_bit           13197  1 radeon
snd_hda_intel          42658  3 
mac_hid                13037  0 
snd_hda_codec         164003  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
wmi                    18590  1 dell_wmi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
video                  18777  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_logitech_dj        18165  0 
usbhid                 47361  0 
hid                    87192  3 usbhid,hid_logitech_dj
usb_storage            48294  1 
b44                    31043  0 
firewire_ohci          35257  0 
firewire_core          57656  1 firewire_ohci
sdhci_pci              18481  0 
sdhci                  37468  1 sdhci_pci
ssb                    51596  3 b43,b44,ssb_hcd
mii                    13654  1 b44
crc_itu_t              12627  1 firewire_core


---

### Post by Hadaka on 2014-03-27
ok, please do..
```
sudo modprobe b44
sudo apt-get install linux-firmware-nonfree
```
are you able to get online with the wired conection?
also...please post the output of..
```
lspci -nn | egrep '0200|0280'
```
thanks.

---

### Post by Justice_Simon on 2014-03-27
Thank! I can now surf to my hearts content, and also the lspci results:
[QUOTE}
justice@justice-MM061:~$ lspci -nn | egrep '0200|0280'

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
[/QUOTE]

Thanks again!

---

### Post by Hadaka on 2014-03-27
Great...thanks for your time
please mark this thread SOLVED
How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

