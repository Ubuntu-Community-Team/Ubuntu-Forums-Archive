---
title: "No Audio (Playing Way Too Fast) after Karmic Upgrade"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Newvin on 2009-12-16
My sound was working fine in Jaunty, but after upgrading to Karmic I have very strange audio problems.  In any media player (Banshee, Rhythmbox, etc...) MP3s will "play" about 20x too fast--the play bar chops along skipping quickly at 4 second intervals and producing no sound.  Additionally, I have no sound on the web.  Curiously, though, when I reboot I hear a very choppy version of the boot-up drum sequence.

For days, I have been reading every post I can find, and I have tried many things.  Most people suggest killing, reinstalling, or clearing the configuration of pulseaudio, but none of these solutions have helped me.  I've checked my alsamixer, and none of the channels are muted.

When I do an ```
aplay -l
``` I get:

```
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any help would be greatly appreciated, as my system is not a stable computing solution in its current form.  

Thanks!

---

### Post by Newvin on 2009-12-17
It's fixed! After trying many different solutions, I think what did the trick was this:

```
# first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload
```

I found it here:

[http://ubuntuforums.org/showthread.php?t=1243064&page=2](http://ubuntuforums.org/showthread.php?t=1243064&page=2)

---

