---
title: "Upgraded ALSA, no no sound"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by mangurt on 2009-06-21
Greetings all;
In my quest to get sound working via HDMI, I completely screwed it up.

I updated ALSA via the 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

And I thought everything was working.  When I did the first reboot, I had no sound.

Here's what I am getting from aplay -l



**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

There's days I should not mess around with anything, because now I can't use skype or anything.

Any help would be greatly appreciated.

---

### Post by Troll_the_Great on 2009-06-21
Hy! I used this guide and it worked beautifully for me.
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
Try it out and post back the results.
Cheers!

---

### Post by mangurt on 2009-06-21
Ok,  I started working with that guide, and I can't launch PulseAudio Device Chooser.  When I type pulseaudio in terminal, I get this error:

pulseaudio: error while loading shared libraries: libpulsecommon-0.9.15.so: cannot open shared object file: No such file or directory

---

### Post by mangurt on 2009-06-21
Searching around for that error, I found out that I had to type 
```
sudo apt-get install libpulse0
```

And now I have sound!  Yeah!

---

