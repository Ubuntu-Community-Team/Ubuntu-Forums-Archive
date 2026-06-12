---
title: "Creative X-Fi surround sound 5.1"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by Yami_Bas on 2011-06-09
Hello,

I recently switched to linux and I read something about a driver being up for this card but I can't find it :(. However this is not my biggest point. I don't really care about the crystaliser and stuff but I do care about the the SPDIF passthrough. Right now it doesn't work :( Can anybody help me with fixing it? Thanks in advance!

Edit: I have the correct settings in XBMC and right now I'm using PulseAudio mixer.

~~Yami_Bas

---

### Post by Yami_Bas on 2011-06-09
bump (A). Since it's pretty far in already.

---

### Post by GWBouge on 2011-06-09
I've got an X-Fi eXtreme Music, and while it works a LOT better now than it used to, PulseAudio still hates mine (and the feeling's mutual, ha).  May not be the answer you're looking for, but the first thing I do now on a fresh install is get rid of whatever pulseaudio packages I can without breaking the system, make sure there's nothing PulseAudio in the Startup Applications, and going an ALSA + jackd route.  You may not need jackd (it seems to provide better 5.1 for me), but alsamixergui is handy.

That's just a thought, though ... my experience with it.  Hopefully someone else has a good way to make it work properly with PulseAudio, because you really have to be careful which packages you get rid of if you try to remove it (keep an eye on the 'To be removed' box that pops up when you mark for removal!).

****EDIT****
Probably worth noting:  I don't use any of the default media apps, either, some of which may rely on PulseAudio.

---

### Post by Yami_Bas on 2011-06-10
I removed pulse with

sudo apt-get --purge remove pulseaudio; sudo apt-get --purge autoremove
then I did this:
sudo apt-get install alsa-base
sudo apt-get install alsa-utils
sudo apt-get install aslamixergui

However I can't find my USB soundcard in the ALSA GUI :( Any ideas?

---

### Post by GWBouge on 2011-06-10
I assume you've tried restarting since you changed the sound config?

Also, can you post the output of these two commands:
```
cat /proc/asound/cards
cat /proc/asound/modules
```

---

### Post by Yami_Bas on 2011-06-11
Yes I rebooted. However SPDIF and DTS works if I do
sudo gstreamer-properties and select ALSA and the USB soundcard. However my normal analog out and digital stereo is just gone when I do that then the SPDIF out (DTS and DD) only works... the sound just plays through my laptop speakers then while I selected the USB soundcard strangely enough.. any ideas?

Edit: Will post the output of those files later.

---

### Post by GWBouge on 2011-06-11
Hmm ... if gstreamer-properties lets you pick, at least you know everything's at least detected.  Are you able to tell an individual program which output to use?

---

