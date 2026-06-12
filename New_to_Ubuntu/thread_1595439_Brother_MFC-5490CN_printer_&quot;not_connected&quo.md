---
title: "Brother MFC-5490CN printer &quot;not connected&quot;"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by MHC on 2010-10-13
I have just bought a PC with Ubuntu 10.04 pre-installed (without Windows). I also wanted a compatible printer. The vendor said the Brother MFC-5490CN  would work, and tested it to be sure. Now I have set everything up at home, and the printer does not work. The PC recognises the printer, but says "Printer not connected?" when I try to print a document or a test page. I replaced the USB cable, but same result. I ran the Troubleshooting test from System>Admin>Printing and got quite a long error log. The first line of the latest job (after I had cancelled all those in the queue 'pending'), was: 

D [13/Oct/2010:14:09:15 +0200] [Job 28] usb_find_devices=0

Under Printer Properties>Settings are the following:

Description: MFC5490CN
Location: <blank>
Device URl: usb://Brother/MFC-5490CN
Make and Model:Brother MFC-5490CN CUPS v1.1

Does anyone know why it would have worked in the shop but not at home? 

Thanks for any suggestions.

---

### Post by Hippytaff on 2010-10-13
Is cups still configured correctly (looking in the right place)...might it be a driver problem?

---

### Post by MHC on 2010-10-13
I'm not sure about that. How can I find out?

---

### Post by Hippytaff on 2010-10-13
with the printer plugged in what is the output when you type
 
```

lsusb

```
 
in the terminal?
 
and after thought...Have you tried restarting the pc?

---

### Post by ibizatunes on 2010-10-13
```
lsusb
```
```
sudo restart cups
``` might work

---

### Post by MHC on 2010-10-13
lsusb gave me: 


Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0732 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by MHC on 2010-10-13
Yes, I have tried restarting it, but that did not help. 

Trying sudo restart cups  gave me:  

restart: Unknown job: cups

---

### Post by ibizatunes on 2010-10-13
service restart cups
sorry my mistake!
but if you have restarted your pc that will restart the service anyway!

---

### Post by ibizatunes on 2010-10-13
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-5490CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-5490CN)

select your printer and the 2 deb files and install that!!

FYI brother linux support sucks!

---

### Post by Hippytaff on 2010-10-13
Doesn't look like ubuntu can see the printer...sorry about this questions, but is it switched on :-D

---

### Post by MHC on 2010-10-13
No problem, it could be something like that :) 

But yes, it is turned on, and photocopies nicely. But no printing or scanning. That is why I replaced the USB cable from printer to PC, but that did not help.

---

### Post by ibizatunes on 2010-10-13
I think you will have to install the drivers manually
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-5490CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-5490CN)   -download the drive .deb
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html) - install LPR driver
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html) - install cpus driver

---

### Post by MHC on 2010-10-13
OK, I'll give that a try. Thanks everyone for your help.

---

### Post by Hippytaff on 2010-10-13
> **ibizatunes said:**
> I think you will have to install the drivers manually
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-5490CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-5490CN) -download the drive .deb
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html) - install LPR driver
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html) - install cpus driver
 
agreed - might be worth checking what drivers are there first
 
```

lsmod

```

---

### Post by MHC on 2010-10-13
lsmod gave:


Module                  Size  Used by
binfmt_misc             7960  1 
dm_crypt               13043  0 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_realtek   279040  0 
snd_hda_intel          25773  2 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6375  0 
snd                    71187  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 11072  0 
parport_pc             29958  1 
psmouse                64576  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
xhci                   41830  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
dm_raid45              75532  0 
xor                     4685  1 dm_raid45
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
radeon                740890  3 
ttm                    60847  1 radeon
drm_kms_helper         30742  1 radeon
usbhid                 41084  0 
hid                    83472  1 usbhid
drm                   198948  5 radeon,ttm,drm_kms_helper
r8169                  39650  0 
mii                     5237  1 r8169
i2c_algo_bit            6024  1 radeon
pata_jmicron            2747  0 
ahci                   37870  5 
intel_agp              29095  0

---

### Post by Hippytaff on 2010-10-13
Looks like you'll have to install it again, strange how it was there in the shop and it's not there now!?

---

