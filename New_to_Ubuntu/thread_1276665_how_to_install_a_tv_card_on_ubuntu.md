---
title: "how to install a tv card on ubuntu"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by Bliksimpie on 2009-09-27
hey!

I'm new to ubuntu and wow what a experience on using it. I have learned a lot about ubuntu in the few days, and i was able to use some programs and play .exe games on ubuntu, but the thing that i can't get to use on ubuntu is my tv card. The model of the tv card is a gigabyte gt-ptv-af rh. I have lost my driver and software disk.

I will appreciate any help on this. Please give the description on a low level. Remember i am new.

---

### Post by cariboo on 2009-09-27
Have a look [here]("http://www.linuxtv.org/") to see if your tuner card is supported.

Open an Applcations-->Accessories-->Terminal and type:

```
sudo lshw -C multimedia
```

The above command will tell you if your tuner card is detected, and if the driver for it is already loaded.

---

### Post by Bliksimpie on 2009-09-30
Okay. I have typed it in and it gave me the following

[php]"*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Multimedia controller
       product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 1
       bus info: pci@0000:03:01.0
       version: d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=128 maxlatency=32 mingnt=84 module=
saa7134"[/php]I don't see any driver for the tuner card so what do I do now. Where can i get the driver?

---

### Post by achase79 on 2009-09-30
make sure that libv4l and xserver-xorg-video-v4l are installed then use tvtime or xawtv programs to scan and view channels.

---

### Post by achase79 on 2009-09-30
if that doesn't work check [here]("http://www.techsupportteam.org/forum/linux-alternative-os/5417-saa7134-pci-tv-tuner-cards-linux.html").

---

### Post by rajeev1204 on 2009-09-30
> **Bliksimpie said:**
> Okay. I have typed it in and it gave me the following

[php]"*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Multimedia controller
       product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 1
       bus info: pci@0000:03:01.0
       version: d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=128 maxlatency=32 mingnt=84 module=
saa7134"[/php]I don't see any driver for the tuner card so what do I do now. Where can i get the driver?


Your tv card uses the philips tuner chip which works flawlessly in ubuntu.
No need of drivers or anything for this card.

Just install the program tvtime from synaptic , select frequency for tuning and enjoy.

---

### Post by Bliksimpie on 2009-09-30
I have dowloaded tvtimer and got it working, but when i open it shows a blank screen. How do change the frequency?

---

