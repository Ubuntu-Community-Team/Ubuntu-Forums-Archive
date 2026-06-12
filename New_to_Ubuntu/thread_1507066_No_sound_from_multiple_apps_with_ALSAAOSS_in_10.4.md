---
title: "No sound from multiple apps with ALSA/AOSS in 10.4"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Elph-kun on 2010-06-11
I realize this problem has been addressed multiple times, but I still can't get more than one program to use sound at a time. This is a huge deal-breaker for me, as someone interested in migrating away from Windows. So far I've tried everything in these threads:

[http://ubuntuforums.org/showthread.php?t=503586](http://ubuntuforums.org/showthread.php?t=503586)

which led me to this thread:

[http://ubuntuforums.org/showthread.php?t=8882](http://ubuntuforums.org/showthread.php?t=8882)

Here in the first post it mentions going into GNOME Sound properties and "Enable sound server startup," but I don't see that anywhere. I assume this is a Lucid thing? Most of these how-to's seem to be written for Hoary or earlier.

[http://ubuntuforums.org/showthread.php?t=101125](http://ubuntuforums.org/showthread.php?t=101125)
Again with the lack of "Enable Sound Server startup," this time for Breezy. Also, this had a link to here:

[http://fort.xdas.com/~kor/oss2jack/install.html]("http://fort.xdas.com/%7Ekor/oss2jack/install.html")

which seemed promising, but I was met with failure when module-installer would not download the source for realtime-ldm. Also, the list of errors I received when trying to compile Fusd was... stunning, to say the least. So I gave that up.

As well as this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

which was a great help in getting my sound to work in the first place, but not with multiple applications.

According to aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
...I have the dreaded HDA architecture. I'm beginning to worry that this is the killer here, but I can hear sound, period. 

My goal here is simply to get Second life viewer (Emerald) and VLC to coexist. I'm running SL using AOSS (even though it should be using ALSA anyway) and VLC with ALSA, and from what I'm reading the fact that I'm *using* ALSA for everything should take care of this problem, given the fact that the only posts I can find on the subject are all 3+ years old. Has this been fixed yet, and if not, why the heck not?

---

