---
title: "Sound not working"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by fairy._.queen on 2011-02-15
Hi all!
I´ve installed kubuntu on a friend´s notebook, but
1) strangely, kubuntu takes forever to load (that is, the black screen lasts for a very long time)
2) there is no sound. I tried installing pulseaudio and pavucontrol, but nothing changed.

As this is a unique opportunity to take him into the Open Source once and for all, I would like to succeed :-P

Some info:
a) Kubuntu 10.04 i386
b) I had to install kubuntu and swap on logical partitions

c) output of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC269 Digital [ALC269 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

d) output of lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)                                                                                                 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)                                                                                                       
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)                                                                                                          
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)                                                                                                          
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)                                                                                                  
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series

```

Thanks in advance for your help

---

### Post by fairy._.queen on 2011-02-15
ok, I shouldn't have put the "kubuntu" tag, it seems :-P
Guys, please, any hints will be fine, never mind the kubuntu tag.
Thank you!

---

### Post by mastablasta on 2011-02-15
for sound - try to upgrade alsa follow this guide to do it:- [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
if you suceed, then maybe it would be better to try with 10.10 (since it has new alsa drivers by default)). as on certain update they just overwrite this and you would need to upgrade and configure it again. or maybe there is another way but i am still searching for it and no one wants to respond to my quaesitons on this. locking ALSA packages doesn't seem to help.
 
for black screen on startup do you mean that the plymouth (the startup animation) doesn't load, but other thigns work afterwards?

---

### Post by fairy._.queen on 2011-02-15
Thanks SO much for replying!
Just found out my PCM volume bar was set to 0: i don't know what it is, but setting it to non-zero solved the problem!!!

As for th black screen, no i mean before the animation starts. That is, grub loads, i choose kubuntu and it takes forever before the lucid lynx animation starts.

Thnks SO much for replying,again!

---

### Post by mastablasta on 2011-02-15
Fantastic. that solution is so much better as you don't have to deal with ALSA being overwriten. :-(
 
What kind of procesor and how much ram are we talking here?
 
also this could be the culprint: Intel Corporation Mobile 4 Series Chipset Integrated Graphics 
do you have propper graphics drivers installed?
 
KDE is quite heavy on resources and graphics. Gnome can easilly be wattered down. I am running gnome on 224MB RAM and 1.2 Ghz processor. runs fine, just loads a bit slow :-)
 
Edit on a side note: KDE is heavy under developement. Even 10.10 doesn't have the latest where a few issues were polished and solved. the Ubuntu based Mint KDE will have the latest KDE though. It's not release yet though.... and i find Mint a bit heavier on resources but friendly for us newbies that switched from windows.

---

