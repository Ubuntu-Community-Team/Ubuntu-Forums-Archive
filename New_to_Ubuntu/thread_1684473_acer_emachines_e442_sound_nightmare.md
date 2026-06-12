---
title: "acer emachines e442 sound nightmare"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by el_koraco on 2011-02-09
ok, so it's not really a nightmare, but the title is good. 

anyhoo, the problem i got is this. i got me a brand spanking new emachines e442 laptop, slapped on dual boot win xp and maverick. upon observing how everything works flawlessly, i just couldn't believe it, taking into account my previous experience with a toshiba-broken-cooling-fan-vista-monstrosity. 

however, just to keep things interesting, i went on to discover that there is no sound coming from my right speaker. zilch. both gnome vollume control and pavucontrol seem to think that the speaker is working,as does every cli and gui mixer i could find, i've tried everything i could in the mixers, but nothing seems to be doing the trick. 

dunno if it's a hw issue. i've tried mint julia and opensuse 11.3 live cd's, with the same results. i have no analog speakers, although the problem does not persist when i plug my earphones in. couldn't tell you how windows sees it, cuz there's absolutely no sound coming from xp whatsoever. don't wanna spend an hour installing win 7 just to see if everything checks out there. could be some pulseaudio vs alsa mixup with the chipset, but i'm not sure, being a linux n00b. 

it's not a major problem, since it doesn't really impair my music, video or browsing experience, and i do have a pair of usb speakers. i'd just like to see if anyone has had similar problems, or if a kind soul knows a solution to this. i'm doing a fresh install of ubuntu today or tomorrow, in order to fully eradicate windows, so i can pretty much do everything to the system you can throw at me. 

possible helpful hints 

uname-a

> Linux mreco 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

aplay -l

> card 0: SB [HDA ATI SB], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dpkg -l | grep "alsa"


> card 0: SB [HDA ATI SB], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mreco@mreco:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.23+dfsg-1ubuntu4                         ALSA driver configuration files
ii  alsa-firmware-loaders                          1.0.23-3ubuntu1                              ALSA software loaders for specific hardware
ii  alsa-source                                    1.0.23+dfsg-1ubuntu4                         ALSA driver sources
ii  alsa-utils                                     1.0.23-2ubuntu3.4                            Utilities for configuring and using ALSA
ii  alsamixergui                                   0.9.0rc2-1-9                                 graphical soundcard mixer for ALSA soundcard driver
ii  bluez-alsa                                     4.69-0ubuntu2                                Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                    ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.30-2                                    GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.35-24-generic    2.6.35-24.201101261600                       Ubuntu-supplied Linux modules for version 2.6.35-24-generic ALSA snapshots


the same for paudio


> ii  gstreamer0.10-pulseaudio                       0.10.25-4ubuntu2                             GStreamer plugin for PulseAudio
ii  libsdl1.2debian-pulseaudio                     1.2.14-6ubuntu3                              Simple DirectMedia Layer (with X11 and PulseAudio options)
ii  pulseaudio                                     1:0.9.22-0ubuntu1                            PulseAudio sound server
ii  pulseaudio-esound-compat                       1:0.9.22-0ubuntu1                            PulseAudio ESD compatibility layer
ii  pulseaudio-module-bluetooth                    1:0.9.22-0ubuntu1                            Bluetooth module for PulseAudio sound server
ii  pulseaudio-module-gconf                        1:0.9.22-0ubuntu1                            GConf module for PulseAudio sound server
ii  pulseaudio-module-x11                          1:0.9.22-0ubuntu1                            X11 module for PulseAudio sound server
ii  pulseaudio-module-zeroconf                     1:0.9.22-0ubuntu1                            Zeroconf module for PulseAudio sound server
ii  pulseaudio-utils                               1:0.9.22-0ubuntu1                            Command line tools for the PulseAudio sound server


devices codecs


> ==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC272X

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI

that's it. tell me if you need more info. thanks for the help, i wouldn't be bothering, but i couldn't seem to find a solution  for this specific problem by myself.

---

### Post by cariboo on 2011-02-09
If the speaker doesn't work with other distros, it may be a hardware problem, the speaker panel on most laptops come off fairly easily, so it shouldn't be to hard to check the connections.

---

### Post by el_koraco on 2011-03-29
so, yeah, after trying to remove pulseaudio and replacing it with alsa, then reinstalling pulseaudio, then purging it, upon which i managed to screw up xorg (don't get me started), i googled the goddamn machine and discovered that it actually has no right speaker. well, at least i didn't unscrew the lid and end up not being able to put it back together. 

word to the wise, before you go into hw/sw troubleshooting, google the machine.

---

