---
title: "Why is windows sound so much easier?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by spidermagicat on 2009-05-03
How does windows sound work? I don't have to do anything to make it work, it just does.

By contrast I seem to have got my head around the sound in Linux now: 

I have pulseaudio for concurrent sound outputs

ALSA for the applications which don't work with pulseaudio, going through pulseaudio when it can (basically for everything other than skype)

Surround sound settings through pulseaudio

Microphone settings, switch settings and separate headphone and speaker volume settings through ALSA

Jack for low latency sound and low latency recording (vital for me)

now, I've had to go through many fiddly settings to avoid underuns and the enevitable popping with pulseaudio and cut out with jack, and I still have to switch the ALSA sound card from pulse to the built in card when ever I use skype.

All of this work has led to a usable system and one that appears easy to someone who doesn't know how much effort it took.

All of this is apparently based on a further system, OSS, which I am frankly clueless about.

Why is windows so much easier, does it do all this stuff itself without telling me, is it reliant on software to do it itself, does it just interface with the hardware properly????

Any responses appreciated :-)

---

### Post by Bölvaður on 2009-05-03
you can think of how windows does it like if all applications you got used OSS + you cannot have proper low latency (did you get the low latency kernel?). Windows is not going through stages when it get's better and better audio control, it just stays the same.
When pulse will be dominant you will not have almost no work to do with your audio except if you need some special config like have films play in 7.1 system and games in your 5.1 usb headphones, playing at the same time... windows cannot provide you with that configure ability, pulse does.

---

