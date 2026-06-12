---
title: "digital stereo sound not working"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by newleaf on 2010-06-23
Hi.  I'm very new to Ubuntu, and not well-versed in computer programming, etc., but willing to try new things.  I bought a new laptop a couple of weeks ago, Toshiba T-135, and installed Ubuntu 10.04.  Right away, the sound worked and I heard the cool Ubuntu drums.  However, the first glitch came when I couldn't connect to my home wireless network, which I fixed by following advice on these help forums.  Next, I realized that I needed to install Flash in Firefox.  No problem, got it installed.  But now I'm having a mind-boggling sound problem.  At one point sound was playing both through the regular speakers and the headphones at the same time, and so I muted all sound for a while (was in the library!) and turned it back on later, but I couldn't get it to come back on via speakers or headphones. After reading advice on these forums and trying different things that didn't work, today I realized that if I switch my settings in Sound Preferences to analog instead of digital, I have sound.  So my question is now, how can I have digital sound again?

Thanks in advance for help.  My info:

christine@christine-laptop:~$ uname -a
Linux christine-laptop 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686 GNU/Linux

christine@christine-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

christine@christine-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

christine@christine-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20582 (Pebble)
==> /proc/asound/card0/codec#1 <==
Codec: Intel G45 DEVCTG

---

