---
title: "USB Wifi Adapter Randomly Stopped working on Ubuntu"
date: 2015-06-24
forum: Networking &amp; Wireless
---

### Post by EvanEjk on 2015-06-24
My Belkin N150 Wireless USB Adapter that normally works on Ubuntu has stopped working only on Ubuntu. I tried completely reinstalling Ubuntu on my tower pc and it still didn't work. I also tried it on my laptop with Ubuntu and it didn't work there either but my laptop's wifi card is still working fine. It seems like it is broken but it still works on Windows. Like it is broken only for Ubuntu!

Normally right after installing Ubuntu before any updates I can plug it in a usb slot and it works fine. I think maybe an update broke it.

Do any of you know how I can get it to work?

EDIT: It is only broken for setting up connections to hidden networks.

---

### Post by Daniel_Pinel on 2015-07-16
Does the key (i mean card, but they look like a USB stick) exhibit any sign of life? lsusb, LED on the USB?

---

### Post by EvanEjk on 2015-09-20
> **Daniel_Pinel said:**
> Does the key (i mean card, but they look like a USB stick) exhibit any sign of life? lsusb, LED on the USB?

Yes it does. After several attempts I found that it works fine connecting to a non hidden network. However I don't like broadcasting my network name to everybody. How can I get it to work again connecting to a hidden network? If I didn't have access to the rotor settings I use it would be way worse.

---

### Post by praseodym on 2015-09-20
Please show the outputs of "lsusb" and "lsmod"

---

### Post by EvanEjk on 2015-09-20
Okay Odym here are the outputs you asked for
```
Bus 003 Device 002: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0461:4e2a Primax Electronics, Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0461:0010 Primax Electronics, Ltd HP Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
```
Module                  Size  Used by
cfg80211              524288  0 
bnep                   20480  2 
rfcomm                 69632  0 
bluetooth             491520  10 bnep,rfcomm
nls_iso8859_1          16384  1 
dm_crypt               24576  0 
fglrx               12460032  159 
r8712u                184320  0 
kvm_amd                61440  0 
snd_hda_codec_realtek    81920  1 
kvm                   479232  1 kvm_amd
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1 
snd_hda_intel          32768  5 
snd_hda_controller     32768  1 snd_hda_intel
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
serio_raw              16384  0 
snd_hwdep              20480  1 snd_hda_codec
snd_rawmidi            32768  1 snd_seq_midi
k10temp                16384  0 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    86016  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_piix4              24576  0 
soundcore              16384  2 snd,snd_hda_codec
shpchp                 40960  0 
amd_iommu_v2           20480  1 fglrx
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
pata_acpi              16384  0 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
psmouse               114688  0 
r8169                  81920  0 
mii                    16384  1 r8169
pata_atiixp            16384  0 
wmi                    20480  0 
ahci                   36864  2 
libahci                32768  1 ahci
```

---

### Post by praseodym on 2015-09-21
Try these module parameters:

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
```
Hiding networks is not a security upgrade

---

### Post by EvanEjk on 2015-09-22
> **praseodym said:**
> Try these module parameters:

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
```
Hiding networks is not a security upgrade

I did this and it didn't fix the problem but I found out something.

If I make my network visible and set up a connection it works. After I have it set up in network manager I can go into my router setting and change my network to invisible and it still works! Even after restarting the computer the connection I set up in network manager to connect to the visible network works to connect to the now invisible wifi. However the bug is still there where the "connect to a hidden network" button never connects and asks for the password over and over again.

---

### Post by EvanEjk on 2015-10-19
> **Daniel_Pinel said:**
> Does the key (i mean card, but they look like a USB stick) exhibit any sign of life? lsusb, LED on the USB?

Not after putting the computer to sleep and waking it back up. I have to unplug it and plug it back in for it to come back alive.

---

### Post by EvanEjk on 2015-10-26
> **EvanEjk said:**
> Not after putting the computer to sleep and waking it back up. I have to unplug it and plug it back in for it to come back alive.

I fixed this problem with the instructions here [http://ubuntuforums.org/showthread.php?t=2004690](http://ubuntuforums.org/showthread.php?t=2004690)
I found out the driver name with "sudo lshw -C network"

---

