---
title: "USB external sound card"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by noorez on 2009-02-21
I have just bought an external USB sound card to use with a 5.1 sound system for my laptop. I managed to get the sound card working by first running:

asoundconf set-default-card Audio
 the two on the list were Intel and Audio. Intel is the internal one.

I then went to the Sound option in the menu and set everything from Autodetect to ALSA and I managed to get sound from the speakers while using media players such as Totem or VLC but could only get sound from the internal speakers while using firefox.

---

### Post by markbuntu on 2009-02-21
Read this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by noorez on 2009-03-05
This is not working for me. In fact, when I do this, no sound works at all...not even the built in speakers.

I think I'm confused on some settings:

First, in System->Pref->Sound: what do I set everything in Device to: 

so far, if I set everything to ALSA, the external sound card and speakers will work but flash videos in firefox will (i.e. YouTube) will only work through the built in speakers.

What do I set Default Mixer Tracks To? There are some options that have the name of the device via PulseAudio and ones that are without PulseAudio.

Also, what do I set the Default Sound Card to? Intel (built in), Audio (USB), PulseAudio (??)

---

