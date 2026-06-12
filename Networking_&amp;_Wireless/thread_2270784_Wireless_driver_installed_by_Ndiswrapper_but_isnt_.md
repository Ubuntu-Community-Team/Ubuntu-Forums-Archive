---
title: "Wireless driver installed by Ndiswrapper but isnt used"
date: 2015-03-25
forum: Networking &amp; Wireless
---

### Post by spamillpass on 2015-03-25
Today, i Installed Ndiswrapper for my WNDA3100V2 wireless adapter.
Its installed and when i type ndiswrapper -l i get
bcmn43xx32 : driver installed
  device (0846:9011) Present

when i type Iwconfig i get

eth0   no wireless extensions 

lo       no wireless extensions


i ran sudo modprobe ndiswrapper and everything said to get the driver to work how ever i still cannot use the driver i manually set up all the details for it to connect to my wireless network through add connection still nothing


what should i do?

all help is appreciated

---

### Post by praseodym on 2015-03-25
Please run the wireless-script from the sticky thread and show the outputs.

Thanks.

---

### Post by spamillpass on 2015-03-26
I do not have ethernet on the pc as it does not have a ethernet port so i am installing everything from a different pc and then putting on usb....

dylan@dylan-HP-Compaq-dc5700-Small-Form-Factor:~$ lspci -nn -d 14e4:
3f:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express [14e4:167b] (rev 02)
dylan@dylan-HP-Compaq-dc5700-Small-Form-Factor:~$ sudo apt-get purge bcmwl-kernel-source
[sudo] password for dylan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dylan@dylan-HP-Compaq-dc5700-Small-Form-Factor:~$ sudo apt-get install 14e4:167b
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 14e4
dylan@dylan-HP-Compaq-dc5700-Small-Form-Factor:~$

---

### Post by praseodym on 2015-03-27
Lets check:
```

ndiswrapper -l
dpkg -l ndiswrapper | grep ii
iwconfig
lsmod
```

---

### Post by spamillpass on 2015-03-28
This is the output:

    dylan@dylan-HP-Compaq-dc5700-Small-Form-Factor:~$ ndiswrapper -lbcmn43xx32 : driver installed
dylan@dylan-HP-Compaq-dc5700-Small-Form-Factor:~$ dpkg -l ndiswrapper | grep ii
dpkg-query: no packages found matching ndiswrapper
dylan@dylan-HP-Compaq-dc5700-Small-Form-Factor:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


dylan@dylan-HP-Compaq-dc5700-Small-Form-Factor:~$ lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
binfmt_misc            17468  1 
joydev                 17393  0 
gpio_ich               13586  0 
hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
coretemp               13441  0 
serio_raw              13483  0 
nouveau              1206577  3 
snd_hda_codec_realtek    72791  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
mxm_wmi                13021  1 nouveau
video                  20128  1 nouveau
ttm                    85314  1 nouveau
drm_kms_helper         61574  1 nouveau
drm                   311018  6 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13413  1 nouveau
snd_hda_intel          30469  3 
snd_hda_controller     31056  1 snd_hda_intel
lpc_ich                21093  0 
snd_hda_codec         139682  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
wmi                    19193  3 hp_wmi,mxm_wmi,nouveau
soundcore              15047  2 snd,snd_hda_codec
mac_hid                13227  0 
parport_pc             32741  1 
ppdev                  17671  0 
shpchp                 37047  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  2 hid_generic,usbhid
psmouse               106561  0 
tg3                   166618  0 
pata_acpi              13053  0 
ptp                    19395  1 tg3
pps_core               19382  1 ptp
floppy                 69662  0 
dylan@dylan-HP-Compaq-dc5700-Small-Form-Factor:~$

---

### Post by praseodym on 2015-03-29
Anything installed?
```

sudo apt-get install --reinstall linux-headers-generic build-essential dkms ndisgtk ndiswrapper-dkms
```

---

### Post by spamillpass on 2015-03-29
No internet connection failed and i do not have ethernet to install

---

### Post by praseodym on 2015-03-30
Is it 32 or 64 bit?

---

### Post by spamillpass on 2015-03-31
It Was 64 bit, I uninstalled ubuntu and put windows back on as i have school work i need to do maybe i will reinstall on a later date but for now i am to frustrated ill use ubuntu on my chromebook for now thanks for trying :)

---

### Post by praseodym on 2015-04-01
Download the files from these links:

[http://forum.ubuntuusers.de/topic/zugang-zum-internet/2/#post-7458863](http://forum.ubuntuusers.de/topic/zugang-zum-internet/2/#post-7458863)

save them in "Downloads" and install as described.

---

