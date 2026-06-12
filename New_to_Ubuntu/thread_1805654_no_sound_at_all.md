---
title: "no sound at all"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by jbi.octave@gmail.com on 2011-07-16
Hi everyone !
my dell inspiron laptop running on dual booting win 7 with ubuntu 10.10. once on ubuntu , it has no sound , please help me in fixing it .
its alsa information is 

!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Thu Jul 14 15:24:55 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      Inspiron N5010
Product Version:   A13


!!Kernel Information
!!------------------

Kernel release:    2.6.36-020636rc1-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 06)
    Subsystem: 1028:0447
--
01:00.1 0403: 1002:aa68
    Subsystem: 1028:0447


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!ALSA configuration files
!!------------------------

!!User specific config file (~/.asoundrc)

 pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:240: no soundcards found...

ARECORD

arecord: device_list:240: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
nls_utf8
udf
crc_itu_t
binfmt_misc
parport_pc
ppdev
rfcomm
sco
bnep
lib80211_crypt_tkip
l2cap
joydev
fglrx
wl
btusb
bluetooth
video
output
uvcvideo
psmouse
videodev
lib80211
v4l1_compat
serio_raw
intel_agp
agpgart
lp
dell_wmi
dell_laptop
dcdbas
parport
usbhid
hid
ahci
r8169
libahci
mii


!!ALSA/HDA dmesg
!!------------------


please some one help ! its boring with no sound !

---

### Post by Kal Sho on 2011-07-16
Is your sound muted? I know it sounds like a silly question, but for some reason when I first installed Ubuntu 10.10 mine was. Click the sound control icon and the first line will say "Mute" or "Unmute". If it says "Unmute" click it.

---

### Post by jbi.octave@gmail.com on 2011-07-17
No Kal, i have not muted any sound , i hav no sound icon .:popcorn: It was working properly till one day it stop , then i install oss , it gave a very low sound then i install bask the alsa then no sound . By the way i have been using ubuntu for some month.
Can smbody help me over there ?

Octave,

---

### Post by jbi.octave@gmail.com on 2011-07-20
ok ! it looks like i have got to roll back to ubuntu 10.04 ,

---

### Post by Bodsda on 2011-07-20
Thats quite a drastic response to what will probably be a simple problem.
 
Please run this in a terminal
```

alsamixer

```
 
Press F5, and move all slider bars to maximum using the arrow keys. Then press F6 to see if you have any other sound devices. If you do, select them in turn and max all the sliders again.
 
If this doesnt work, please pastebin the output of ```
dmesg
``` and ```
lspci
```
 
Thanks,
Bodsda
 
EDIT: Interestingly, that alsa info shows no devices under 'Soundcards recognised by alsa' -- Could you also try this command please.
```

sudo killall pulseaudio

```
And tell us if you got any ouput from it?

---

