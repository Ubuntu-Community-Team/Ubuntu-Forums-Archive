---
title: "Trying to blacklist network card"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by davidmclifton on 2010-12-23
Greetings,

  I'm trying to blacklist one of my two wireless network cards, so that it will stop trying to connect to my wireless network.

  Just trying to figure out what I should put into the blacklist setting - I can't seem to connect the dots between the network card info and the drivers to determine what driver Ubuntu automatically associated with the card so I can make it go 'bye bye' :p

Appreciate any help.

from lshw:
```

  *-network               
       description: Wireless interface
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 03
       serial: 00:1e:4c:6c:60:59
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:fe8fc000-fe8fffff memory:d0000000-d00fffff

```

from lsmod:

```

Module                  Size  Used by
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
snd_hda_codec_atihdmi     3079  1 
joydev                 11363  0 
usbhid                 42062  0 
snd_hda_codec_idt      64667  1 
hid                    84678  1 usbhid
rt2870sta             446078  0 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
arc4                    1497  2 
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
rt2800usb               9955  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800lib              31970  1 rt2800usb
lib80211_crypt_tkip     8732  0 
rt2x00usb              11316  2 rt2800usb,rt2800lib
rt2x00lib              31575  2 rt2800lib,rt2x00usb
led_class               3393  1 rt2x00lib
mac80211              266657  2 rt2x00usb,rt2x00lib
fglrx                2523725  90 
snd                    64117  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              170293  2 rt2x00lib,mac80211
crc_ccitt               1699  2 rt2870sta,rt2800usb
wl                   1965231  0 
psmouse                62080  0 
dcdbas                  6910  0 
x38_edac                3627  0 
serio_raw               4910  0 
edac_core              46822  2 x38_edac
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lib80211                6175  2 lib80211_crypt_tkip,wl
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usb_storage            50372  0 
firewire_ohci          24679  0 
ahci                   21857  0 
libahci                26199  6 ahci
firewire_core          54327  1 firewire_ohci
e1000e                151787  0 
crc_itu_t               1739  1 firewire_core

```

---

### Post by TBABill on 2010-12-23
From what I can tell you have a Broadcom card that uses the wl driver and you have a Ralink chipset on another card that uses the rt2870 or rt2800. Seems like you have 3 drivers loading. What you do is open /etc/modprobe.d/blacklist.conf and at the end just add the drivers you want to blacklist (each on a separate line). Then save and restart. But you MUST edit as root. Easy way is ```
sudo gedit /etc/modprobe.d/blacklist.conf
```

---

### Post by davidmclifton on 2010-12-23
Thanks TBABill - I understand, my problem is identifying the name of the driver. I'm not sure where in the output of the second command I can find the name of the driver for the card I pulled from the output of the first command, or even how to tell which drivers are network cards so I can try cycling through them.

Is there a good way to understand the output to tell which are network, or to link the output from the first command to the driver name?

---

### Post by wep940 on 2010-12-23
Look in the first output - the network device - and look at driver=.  In this case it says wl0, but the module is just name is just wl , so add wl to the end of the blacklist.conf file.
 
As far as looking at the output of lsmod and determining what is what, we know what some are from experience, but you would really need to search the net on the module name to find out what device it is for.  It's not as simple as looking for something in the output that says "I'm a wireless driver".

---

