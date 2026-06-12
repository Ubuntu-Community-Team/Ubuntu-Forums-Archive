---
title: "Ubuntu doesn't recognize wireless networks with Inspiron 530 computer"
date: 2014-03-13
forum: Networking &amp; Wireless
---

### Post by abraham4 on 2014-03-13
I recently installed Ubuntu into my old Dell Inspiron 530 computer that had windows OS. It would read wireless networks normally with it, but with ubuntu it doesn't. Can someone help me? I don't much about Ubuntu

---

### Post by Hadaka on 2014-03-14
Hi,lets see what your wirless card is...
please post the output of..
```
lspci -nnk | grep -iA2 net
```
are you able to get online with the ethernet
cable...hard wired?
thanks.

---

### Post by abraham4 on 2014-03-15
I can't use an ethernet cable because my router is really far away from my room. 

this is the output i received:

00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
	Subsystem: Dell Inspiron 530 [1028:020d]
	Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: ASUSTeK Computer Inc. WL-138G v2 / WL-138gE / WL-100gE [1043:100f]
	Kernel driver in use: b43-pci-bridge

---

### Post by Hadaka on 2014-03-15
hi, please post the output of..
```
lsmod
cat /etc/modules
cat /etc/network/interfaces
sudo iwlist wlan0 scan
rfkill list all

```
then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
thanks

---

### Post by abraham4 on 2014-03-15
I should also mention that I am using the trail version. I haven't fully installed it yet. 

Here's the output: 

Module                  Size  Used by
wl                   4161817  1 
lib80211               14040  1 wl
nls_iso8859_1          12617  1 
dm_crypt               22280  0 
usblp                  18236  0 
mac80211              513247  0 
coretemp               13195  0 
snd_usb_audio         119227  4 
dcdbas                 14383  0 
joydev                 17097  0 
dm_multipath           22402  0 
scsi_dh                14458  1 dm_multipath
snd_hda_codec_realtek    45473  1 
snd_usbmidi_lib        24326  1 snd_usb_audio
snd_hda_intel          42658  6 
cfg80211              401436  2 wl,mac80211
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
snd_pcm                89488  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
microcode              18830  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
serio_raw              13189  0 
lpc_ich                16864  0 
snd                    60790  32 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
parport_pc             31981  0 
soundcore              12600  1 snd
ppdev                  17391  0 
bnep                   18893  2 
mac_hid                13037  0 
lp                     13299  0 
rfcomm                 53664  0 
parport                40795  3 lp,ppdev,parport_pc
bluetooth             323534  10 bnep,rfcomm
squashfs               46391  1 
overlayfs              27158  1 
nls_utf8               12493  1 
isofs                  39211  1 
dm_mirror              21715  0 
dm_region_hash         15984  1 dm_mirror
dm_log                 18072  2 dm_region_hash,dm_mirror
hid_microsoft          12693  0 
usbhid                 47361  0 
hid                    87192  2 hid_microsoft,usbhid
nouveau               834976  3 
mxm_wmi                12893  1 nouveau
wmi                    18590  2 mxm_wmi,nouveau
video                  18777  1 nouveau
i2c_algo_bit           13197  1 nouveau
ttm                    71886  1 nouveau
drm_kms_helper         46867  1 nouveau
usb_storage            48294  1 
drm                   242354  5 ttm,drm_kms_helper,nouveau
floppy                 55378  0 
e1000e                222921  0 
ptp                    18156  1 e1000e
pps_core               18546  1 ptp
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.


ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ rfkill list all
ubuntu@ubuntu:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms fakeroot linux-headers-generic linux-image-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,943 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.

---

### Post by Hadaka on 2014-03-15
hi..the    wl   module was loaded in your lsmod dump.
once that was removed..bcmwl-kernel-source*
it should have come to life on a boot.  lets take a look at
the moule file again please.   please do.
```
lsmod
```
post the output
thanks

---

### Post by abraham4 on 2014-03-15
Module                  Size  Used by
wl                   4161817  1 
lib80211               14040  1 wl
nls_iso8859_1          12617  0 
dm_crypt               22280  0 
usblp                  18236  0 
mac80211              513247  0 
coretemp               13195  0 
snd_usb_audio         119227  4 
dcdbas                 14383  0 
joydev                 17097  0 
dm_multipath           22402  0 
scsi_dh                14458  1 dm_multipath
snd_hda_codec_realtek    45473  1 
snd_usbmidi_lib        24326  1 snd_usb_audio
snd_hda_intel          42658  6 
cfg80211              401436  2 wl,mac80211
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
snd_pcm                89488  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
microcode              18830  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
serio_raw              13189  0 
lpc_ich                16864  0 
snd                    60790  32 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
parport_pc             31981  0 
soundcore              12600  1 snd
ppdev                  17391  0 
bnep                   18893  2 
mac_hid                13037  0 
lp                     13299  0 
rfcomm                 53664  0 
parport                40795  3 lp,ppdev,parport_pc
bluetooth             323534  10 bnep,rfcomm
squashfs               46391  1 
overlayfs              27158  1 
nls_utf8               12493  1 
isofs                  39211  1 
dm_mirror              21715  0 
dm_region_hash         15984  1 dm_mirror
dm_log                 18072  2 dm_region_hash,dm_mirror
hid_microsoft          12693  0 
usbhid                 47361  0 
hid                    87192  2 hid_microsoft,usbhid
nouveau               834976  3 
mxm_wmi                12893  1 nouveau
wmi                    18590  2 mxm_wmi,nouveau
video                  18777  1 nouveau
i2c_algo_bit           13197  1 nouveau
ttm                    71886  1 nouveau
drm_kms_helper         46867  1 nouveau
usb_storage            48294  0 
drm                   242354  5 ttm,drm_kms_helper,nouveau
floppy                 55378  0 
e1000e                222921  0 
ptp                    18156  1 e1000e
pps_core               18546  1 ptp

---

### Post by Hadaka on 2014-03-15
yup...wl still hangin on in there,,,lets get that rascal gone..Please do..
```
sudo modprobe -rf wl
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
boot..then do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer

sudo modprobe b43
```
working now?

---

### Post by Hadaka on 2014-03-15
I just realized..we need to do this like you are offline...because the apt-get requires internet acess to work..so
do this...down load the b43 zip file frst..it's last in red letters on this page...see it?
[ATTACH=CONFIG]251197[/ATTACH]              <--b43 zip
ok once that is down loaded to Downloads....drag and drop it to Desktop then please do.
rightclick the b43 file...choose...OPEN HERE..EXTRACT HERE., then
open a trminal...ctrl/alt/t and do..
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
and thats how you do it with no internet access or if yer
too lazy to drag the computer to the modem with a cable.

---

### Post by abraham4 on 2014-03-15
That worked! thank you very much.

---

### Post by Angi on 2014-03-16
Had the same problem on dell inspiron 15, followed instructions here and it works. Thanks !!!

---

### Post by Hadaka on 2014-03-16
Great ! glad that worked for you.

---

