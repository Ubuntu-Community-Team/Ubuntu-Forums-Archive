---
title: "Libsdl1.2debian-alsa/pulseaudio"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2010-04-17
I was recently asked if I could help a group of friends with the editing of their music videos and found that my best free option would be Openshot. When I go to install it however, it says that it needs to remove "libsdl1.2debian-alsa" and it seems to want to replace it with the pulseaudio version "libsdl1.2debian-pulseaudio." What are these two packages for and what are the differences between them? Will using pulseaudio and removing alsa break any of my other programs, like Totem or Rhythmbox?

---

### Post by Martin Marshalek on 2010-04-17
Bump, I really don't want to mess up my sound and I'm not sure what to do.

---

### Post by kostkon on 2010-04-17
This package will not change your general sound configuration.

It will just make the SDL-based software (mostly games) to send their sound directly to PulseAudio instead of first sending it to the ALSA software mixer.

Actually, replacing libsdl1.2debian-alsa with libsdl1.2debian-pulseaudio will improve the sound of SDL-based apps in most cases.

---

### Post by Martin Marshalek on 2010-04-18
Okay, that's good then. I just didn't want my audio software malfunctioning so I can still listen to music, watch movies, and edit audio after installing this.

Thank you.

---

