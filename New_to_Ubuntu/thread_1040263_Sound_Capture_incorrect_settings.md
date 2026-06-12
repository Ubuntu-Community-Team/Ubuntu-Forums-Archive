---
title: "Sound Capture incorrect settings"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by syntrichia.ruralis on 2009-01-15
Hey :)

I was using my microphone in Ubuntu 8.04, but it stopped working. I have followed some how-to and tutorials and now my sound works perfectly with PulseAudio and Alsa apart from the microphone.

When I open Sound Recorder, it shows 'Your Audio Capture settings are invalid. Correct them in Multimedia settings'. I go to System, Preferences and find no Multimedia settings.

When I go to Sound Preferences and try to test the devices it says 'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused'

When I go to PulseAudio Volume Control it says 'Connection failed: Connection refused'.

Please help...
Bye,
k

---

### Post by neu2buntu on 2009-01-15
try opening up >soundrecorder > file > open volume control , and @ top > device. change the device ,i think it defaults to alsa

---

### Post by neu2buntu on 2009-01-15
also in this volume control window choose playback or recording tab and click preferences and in pop up box make sure microphone is ticked

---

### Post by syntrichia.ruralis on 2009-01-15
Already tried to do that, unfortunately that doesn't help.
Thanks for tips anyway :)

---

### Post by syntrichia.ruralis on 2009-01-16
I followed [SOLVED] Multiple Sound Solution (ALSA w Pulseaudio) and now i am not seeing all this strange messages when I try to open Sound Preferences, but still I have problems with recording myself.

When I test sound capture in Sound Preferences i can hear humming, but not a proper test sound.

I remember reading somewhere about this, but as people title those threads "microphone doesn't work" it is extremely difficult to find it again.

---

