---
title: "Wifi not starting after resume post vivid upgrade"
date: 2015-03-16
forum: Networking &amp; Wireless
---

### Post by markisthejob on 2015-03-16
Hi guys. Ive upgraded to 15.04 and now my wifi dongle needs to be plugged out and back in again everytime I take my computer out of standby.
In previous versions of ubuntu, for a long time now, I got around this by adding ```
SUSPEND_MODULES="r8712u"
``` into /etc/pm/config.d/config

The module looks to be loading ok after the upgrade (heres lsmod before reconnecting the dongle) ```
mark@mark-MacPro:~$ lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23256  0 
vboxnetadp             25670  0 
vboxnetflt             27605  0 
vboxdrv               418184  3 vboxnetadp,vboxnetflt,vboxpci
binfmt_misc            18072  1 
cfg80211              539517  0 
nvidia              11364375  30 
xpad                   22369  0 
r8712u                188327  0 
ff_memless             13573  1 xpad
snd_usb_audio         176914  4 
snd_usbmidi_lib        30187  1 snd_usb_audio
joydev                 17344  0 
snd_hda_codec_realtek    83779  1 
snd_hda_codec_generic    68875  1 snd_hda_codec_realtek
snd_hda_intel          30520  3 
snd_hda_controller     31872  1 snd_hda_intel
snd_hda_codec         139421  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  2 snd_usb_audio,snd_hda_codec
snd_pcm               105534  5 snd_usb_audio,snd_hda_codec,snd_hda_intel,snd_hda_controller
coretemp               13441  0 
snd_seq_midi           13564  0 
kvm_intel             148519  0 
snd_seq_midi_event     14899  1 snd_seq_midi
drm                   335207  2 nvidia
kvm                   480315  1 kvm_intel
snd_rawmidi            30827  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
applesmc               19352  0 
snd_seq_device         14878  3 snd_seq,snd_rawmidi,snd_seq_midi
input_polldev          14607  1 applesmc
snd_timer              29513  3 snd_pcm,snd_seq
lpc_ich                21093  0 
i5000_edac             17420  0 
edac_core              51959  2 i5000_edac
snd                    87611  24 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              15052  2 snd,snd_hda_codec
ioatdma                63282  0 
i5k_amb                13159  0 
shpchp                 37040  0 
sbshc                  13858  0 
dca                    15130  1 ioatdma
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
autofs4                38830  2 
hid_generic            12559  0 
usbhid                 52608  0 
hid                   110426  3 hid_generic,usbhid
firewire_ohci          44323  0 
firewire_core          68671  1 firewire_ohci
pata_acpi              13053  0 
crc_itu_t              12707  1 firewire_core
e1000e                234671  0 
ptp                    19445  1 e1000e
pps_core               19333  1 ptp
```

Can't figure it out. Any ideas appreciated

---

### Post by markisthejob on 2015-03-18
Ok so I can manually restart the module to save me fumbling around behind the computer everytime by using

```
sudo rmmod r8712u
```

& then

```
sudo modprobe r8712u
```

This will work as a temporary fix but it would be nice to not have to do it everytime

---

### Post by ponkarthik on 2015-08-20
Hi, 

I found the following solution for this specific problem I also experienced. 

[https://mail.gnome.org/archives/networkmanager-list/2014-October/msg00091.html](https://mail.gnome.org/archives/networkmanager-list/2014-October/msg00091.html)

Just change the path of modprobe to /sbin/modprobe.

Hope this helps

---

