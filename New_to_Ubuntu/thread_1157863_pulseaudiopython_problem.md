---
title: "pulseaudio/python problem"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-05-13
From my user log....it says the kernal is broken.....sounds bad!!

May 13 21:41:20 pj-indulgence pulseaudio[3499]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
May 13 21:41:20 pj-indulgence pulseaudio[3499]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.
May 13 21:41:44 pj-indulgence python: hp-systray[3595]: error: option -s not recognized

---

### Post by dunbrokin on 2009-05-14
bump

---

### Post by kostkon on 2009-05-14
They are just warning messages, nothing serious or catastrophic.

The second *PulseAudio* message says that the driver for one of your sound devices is not of good quality. It is a warning message from *PulseAudio*, nothing to worry about.

The first message from *PulseAudio*, although, seems to suggest that *PulseAudio* is changing the sound coming out from this device from stereo to mono, although it is not certain that this is actually happening.

The other message looks like a harmless warning message from the *hp-systray* utility that belongs to the *HP Linux Printing and Imaging System (HPLIP)* application.

---

### Post by dunbrokin on 2009-05-15
Much obliged...thank you.

---

