---
title: "Can't connect to either wired router connection or wifi"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by M80 on 2014-05-16
As stated in the thread title, I cannot connect to either wired router connections or wifi.  Previously, setting a static IP and ignoring IPV6 worked, but this no longer allows me to connect.

My other operating systems can connect without any issues, as can mobile devices;

Can someone help me with this problem?

---

### Post by varunendra on 2014-05-16
Please open a terminal (Ctrl-Alt-T) and post back the output of following commands :
```
uname -mr
lspci -nnk | grep -iA2 net
lsusb
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by M80 on 2014-05-16
```
user1@d620:~$ uname -mr
3.2.0-58-generic x86_64
user1@d620:~$ lspci -nnk | grep -1A2 net
        Kernel modules: yenta_socket
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
        Subsystem: Dell Latitude D620 [1028:01c2]
        Kernel driver in use: tg3
user1@d620:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 003 Device 009: ID 1c4f:0016 SiGma Micro
Bus 004 Device 004: ID 1c4f:0003 SiGma Micro HID controller
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
user1@d620:~$ lsmod
Module                  Size  Used by
snd_hda_codec_idt      70795  1
snd_hda_intel          33719  6
snd_hda_codec         127706  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
dell_wmi               12681  0
sparse_keymap          13890  1 dell_wmi
bnep                   18281  2
dell_laptop            18119  0
dcdbas                 14490  1 dell_laptop
pcmcia                 49353  0
parport_pc             32866  0
rfcomm                 47604  0
bluetooth             180113  10 bnep,rfcomm
ppdev                  17113  0
joydev                 17693  0
snd_seq_midi           13324  0
snd_rawmidi            30748  1 snd_seq_midi
yenta_socket           28084  0
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
psmouse                97519  0
binfmt_misc            17540  1
serio_raw              13211  0
b43                   365983  0
nouveau               775039  3
snd_timer              29990  2 snd_pcm,snd_seq
mac_hid                13253  0
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              506862  1 b43
ttm                    76949  1 nouveau
drm_kms_helper         46978  1 nouveau
drm                   241971  5 nouveau,ttm,drm_kms_helper
snd                    79041  21 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205774  2 b43,mac80211
bcma                   26696  1 b43
i2c_algo_bit           13423  1 nouveau
mxm_wmi                13021  1 nouveau
wmi                    19256  2 dell_wmi,mxm_wmi
soundcore              15091  1 snd
video                  19651  1 nouveau
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0
hid                    99883  1 usbhid
tg3                   152144  0
ssb                    52752  1 b43
user1@d620:~$

```

---

### Post by varunendra on 2014-05-17
> **M80 said:**
> ```
user1@d620:~$ lspci -nnk | grep **-[COLOR="#FF0000"]1[/COLOR]A2** net

```

The command option was "-iA2.." (small "I" for "ignore", not numeric "1" before "A"), please post the output of the corrected command again.

Guessing by your "lsmod" output, please try this -

[INDENT]**1)** Download the "linux-firmware-nonfree" package from this link : [http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

**2)** Copy this downloaded file onto your desktop. Then open a terminal, and run the following commands (you may copy-paste them to avoid errors) -
```
cd Desktop
sudo dpkg -i linux-firmware*.deb
```[/INDENT]

Then reboot and see if you wireless is working. If not, please follow the instructions in this post to show us a detailed report of your system : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

