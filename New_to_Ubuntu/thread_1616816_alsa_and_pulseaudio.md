---
title: "alsa and pulseaudio"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by beew on 2010-11-08
Hi,

I have been messing with my system (Lucid)a bit. First I uninstalled pulseaudio and updated alsa from a ppa  to see if there is better performance (less cpu usage) in higher resolution video play back. Then I reinstalled pulseaudio again  since the improvement is marginal but audio is definitely worse (but a newer version of pulse audio from Maverick since after upgrading alsa  some components for pulse in the repo won't install because of dependency problems). Now I end up having the alsa mixer  along with whatever pulse audio tool to control volume and sound settings. 

Performancewise video play back (>=720p even locally) is still cpu intensive but audio seems to be better than when pulse was gone.

I am new to the audio-video stuffs and don't quite know what is the relationship between pulse and alsa. Is pulse just a layer on top of alsa? Do I need to uninstall some alsa component in order to give control back to pulse or should I keep both sets of control tools?

---

### Post by marshmallow1304 on 2010-11-10
Pulseaudio is a sound server that sits on top of ALSA or OSS.  ALSA or OSS handles the kernel-level hardware support and PA adds [quite a few features]("https://secure.wikimedia.org/wikipedia/en/wiki/PulseAudio").  It's possible and quite common when setting up a custom system to use ALSA without PA.  That said, I haven't had any problems with PA for at least a year.

---

