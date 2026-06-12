---
title: "Weird Wireless problem"
date: 2013-11-23
forum: Networking &amp; Wireless
---

### Post by Jigawatt on 2013-11-23
I posted the other day about not being able to use and pick up wireless. The wireless works now, but the weird part is everytime I come out of standby mode or cutting my laptop back on It will not find or get on wireless unless I run the [ sudo iwlist wlan0 scan ] code in terminal. I have to run it twice also which is weird. The first time it wont pick up anything, but on the second try it will actually search and find the wifi signal and it will work. At least I've learned a bit about some of the networking commands. LOL

Thanks

---

### Post by praseodym on 2013-11-24
Please show both outputs of:
```

lsmod
lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' 
```

---

### Post by Jigawatt on 2013-11-24
lsmod reply
```

Module                  Size  Used by
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211552  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
arc4                   12509  2 
snd_hda_codec_idt      64649  1 
coretemp               13324  0 
kvm_intel             127786  0 
snd_hda_intel          38819  3 
b43                   364596  0 
snd_hda_codec         118650  2 snd_hda_codec_idt,snd_hda_intel
kvm                   384557  1 kvm_intel
joydev                 17329  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
i915                  550464  3 
snd_seq_midi           13132  0 
mac80211              541819  1 b43
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39854  0 
snd_timer              28931  2 snd_pcm,snd_seq
yenta_socket           27427  0 
drm_kms_helper         47749  1 i915
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   233935  4 i915,drm_kms_helper
cfg80211              453919  2 b43,mac80211
pcmcia_rsrc            18367  1 yenta_socket
dell_wmi               12601  0 
dell_laptop            17209  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                82769  0 
snd                    57014  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
microcode              18433  0 
dcdbas                 14065  1 dell_laptop
sparse_keymap          13658  1 dell_wmi
gpio_ich               13278  0 
soundcore              12600  1 snd
i2c_algo_bit           13316  1 i915
serio_raw              13031  0 
ssb_hcd                12781  0 
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lpc_ich                17048  0 
bcma                   39810  1 b43
wmi                    18744  1 dell_wmi
video                  19116  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35914  0 
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ssb                    51554  2 b43,ssb_hcd
tg3                   150733  0 
ptp                    18232  1 tg3
pps_core               13736  1 ptp

```

lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv'  reply 

```

mac80211              541819  1 b43
cfg80211              453919  2 b43,mac80211
mac_hid                13077  0 
firewire_ohci          35914  0 
firewire_core          62086  1 firewire_ohci

```

---

### Post by praseodym on 2013-11-24
Open this file:
```

sudo touch /etc/pm/config.d/00sleep_module 
sudo chmod +x /etc/pm/config.d/00sleep_module
gksudo gedit /etc/pm/config.d/00sleep_module
```
Add this line:```

SUSPEND_MODULES="$SUSPEND_MODULES b43 mac_hid firewire_ohci" 
```
Save, close the editor and try SUSPEND

---

### Post by Jigawatt on 2013-11-24
It didn't work.

---

### Post by Jigawatt on 2013-11-25
bump

---

### Post by mörgæs on 2013-11-25
Please stop repeat bumping of your thread.

---

