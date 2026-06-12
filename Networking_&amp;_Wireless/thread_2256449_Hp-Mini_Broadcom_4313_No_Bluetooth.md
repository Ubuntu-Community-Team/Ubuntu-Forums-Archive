---
title: "Hp-Mini Broadcom 4313 No Bluetooth"
date: 2014-12-12
forum: Networking &amp; Wireless
---

### Post by shamouna on 2014-12-12
Hi fellow Ubuntu-Users (:
I'm fairly new to Ubuntu, I've installed Ubuntu 14.04 LTS on my old HP-Mini-210-2001sg.
I've got the Wifi working with the Broadcom 4313 card.
But when i try to connect a Bluetooth device it just says: No Bluetooth-Adapters found.

Here is some specification:


```
~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
~$ lsmod
Module                  Size  Used by
ctr                    12905  1 
ccm                    17496  1 
nvram                  14027  0 
arc4                   12536  2 
brcmsmac              529837  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356470  0 
mac80211              546051  2 b43,brcmsmac
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
cfg80211              409394  3 b43,brcmsmac,mac80211
videobuf2_memops       13170  1 videobuf2_vmalloc
hp_wmi                 13702  0 
videobuf2_core         39258  1 uvcvideo
sparse_keymap          13708  1 hp_wmi
videodev              108503  2 uvcvideo,videobuf2_core
ssb                    51854  1 b43
snd_hda_codec_idt      48978  1 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
snd_seq_midi           13132  0 
coretemp               13195  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
i915                  710093  4 
joydev                 17101  0 
serio_raw              13230  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper         48868  1 i915
lpc_ich                16864  0 
snd_timer              28584  2 snd_pcm,snd_seq
drm                   244037  5 i915,drm_kms_helper
snd                    60939  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
parport_pc             31981  0 
i2c_algo_bit           13197  1 i915
wmi                    18673  1 hp_wmi
mac_hid                13037  0 
ppdev                  17391  0 
video                  18903  1 i915
bcma                   42043  3 b43,brcmsmac
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47070  0 
hid                    87604  2 hid_generic,usbhid
psmouse                91357  0 
ahci                   25579  2 
r8169                  61562  0 
libahci                27214  1 ahci
mii                    13654  1 r8169

```

```
~$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```

thank you in advance (:
if any other information is need I'm happy to help you out.

edit:

And yes i purged bcmwl-kernel-source like 20 times ;)
installed b43-fwcutter
tried alot solutions suggested in the Forums, sadly nothing really worked out for me ):

---

### Post by shamouna on 2014-12-18
i know some post get lost in here so I'm still hopeful somebody can help me :KS

---

### Post by Hadaka on 2014-12-18
Hi, you said " And yes i purged bcmwl-kernel-source like 20 times"
you dont have that driver. you have the native brcmsmac driver and some
pieces parts of the b43. though it is working,per your statements you can
get better performance by blacklisting ssb and b43..please COPY and paste this command..
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
you are getting the response 'No Bluetooth-Adapters found' because here you see...
```
~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```you ask for radio frequeny kill list. wireless is radio,bluetooth is radio
you have NO blue tooth ,therefore it is not likely to function.
good luck.

---

