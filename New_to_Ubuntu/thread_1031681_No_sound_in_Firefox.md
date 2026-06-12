---
title: "No sound in Firefox"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by neigun on 2009-01-05
Hi Guys

I've tried a number of things to resolve this, but I am getting nowhere fast!:confused:

All of the relevant software has been downloaded, I think, from Medibuntu. DVD's play, including sound, though the video footage is rather jerky with Totem Movie Player. However, in other packages there is no sound- Gnome Mplayer, Mplayer or in Firefox. The picture quality in Firefox is great.

TTFN Neil

System Spec:

Ubuntu 8.10 64 bit
Kernel 2.6.27-9-generic
AMD 64 3200
ATI Radeon HD 3650 AGP
1.25Gb Ram
86Gb HD

---

### Post by donkyhotay on 2009-01-05
Sounds like a volume configuration issue. Try running
```
sudo apt-get install alsamixergui
```
then run it from applications > sound & video > alsamixergui. This will allow you to configure the volume for different audio I/O channels. Chances are one of the muted ones is affecting those specific programs since the others sound just fine.

---

### Post by Titan8990 on 2009-01-05
If you are attempting to use multiple programs at the same time that could possible use sound, you will need to set up pulseaudio: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by neigun on 2009-01-06
> **donkyhotay said:**
> Sounds like a volume configuration issue. Try running
```
sudo apt-get install alsamixergui
```
then run it from applications > sound & video > alsamixergui. This will allow you to configure the volume for different audio I/O channels. Chances are one of the muted ones is affecting those specific programs since the others sound just fine.
The Alsa Mixer gui installed but it only includes two channels for the Master, both have now been set at max, but the only other two channels for capture and blanked out.

I didn't say originally but I have a SB 5.1 audigy card installed- if it makes any difference?

Thanks for the help.

Neil

---

