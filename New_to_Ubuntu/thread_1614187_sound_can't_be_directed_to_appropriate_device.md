---
title: "sound can't be directed to appropriate device"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by Norman Thom on 2010-11-05
Despite having used Ubuntu off and on since release 6.04 I am becoming increasingly frustrated with the sound performance over the last few releases.
The problem I am having now is that I am not able to have the sound play through the desired device on my desktop.
Since Pulseaudio is just too restrictive I uninstalled it.  This of course left me with no graphical means of directing my sound file output so I added 2 different Alsa mixers 'alsamixer gui' and the 'GNOME Alsa Mixer' ( this one is undesirably complex and confusing)
For example I use Rhythmbox for my mp3 manager.  Yesterday it played fine over my stereo speakers today it plays through my Skype handset.
Can anybody show me a method of selecting which sounds (ie which applications) to play over specific output devices

Thanking you in advance

Norm

---

### Post by Norman Thom on 2010-11-05
Again to emphasise my frustration.  The system seems to in part at least cured itself.  I simply rebooted my computer and now mp3 sounds go through my speakers.  I will try to run skype and see if that works.  I have some more rustrations but will leave those for subsequent posts

Norm

---

### Post by kostkon on 2010-11-05
> **Norman Thom said:**
> Since Pulseaudio is just too restrictive I uninstalled it.
PulseAudio too restrictive?! Quite the contrary, I believe. It gives you the option to set an input/output device per application, and many other nice things.
> **Norman Thom said:**
> Can anybody show me a method of selecting which sounds (ie which applications) to play over specific output devices
Yes, PulseAudio + the PulseAudio Volume Control utility.

---

