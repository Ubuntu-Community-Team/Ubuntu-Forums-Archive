---
title: "mic and speaker switch off (alsamixer)"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by spazznie on 2009-08-30
I got my speakers to work by using the /etc/modprobe.d/alsa-base.conf fix, but then I tried to get my microphone to work. Here's the funny part. they switch off. Sometimes I'll enter alsamixer and there will be the extra columns including an ability to select "front mic" as a capture device--then the microphone works. other times the options are absent, but my speakers work. The alternating seems to be between reboots. 

Before this fiasco, I followed a guide to disable pulseaudio, which was causing problems in the cases I read about on threads.

Also, whenever I click on the sound icon on the taskbar, all the options under recording are muted--but when the extra columns in alsamixer are unmuted, the microphone still works.

Help please? I've been working on this for two days and have looked in every thread I could find. 

Currently my speakers aren't working (but sound works through the headphone jack) but the microphone is. 

Also, right now when I do "*sudo alsamixer force-reload," instead of all my sound-using applications restarting and hearing the popping noise from my speakers, alsamixer just opens. I tried using the 'rcalsarestart' sudo command but even when I log in as root it doesn't work.*

I run jaunty on an HP HDX 16.

---

### Post by spazznie on 2009-08-30
So new development in this issue.

in /etc/modprobe.d/alsa-base.conf, whenever I set 
options snd-hda-intel model=hp-hdx
the capture options in alsamixer increase and I can see the microphone reacting to tapping in SoundRecorder.

but whenever I use model=hp-m4
the capture options disappear and I can usually get sound out of my speakers.

Hope this helps other people desperate to get their mics working.

Right now I'm back to options snd-hda-intel model=hp-m4, a working speaker, non-working headphone jack, and a microphone that does not record even whether it's set to capture0, capture1, digital, DAC0, DAC1, Import0 Mux, Import1 Mux, Mux, or Mux 1. This seems like a disgusting load of options to me. Also, my speakers are working despite the sound icon in the taskbar showing a mute symbol. 

Additionally, whenever I enter the volume control preferences, all options under the capture tab always have the microphone option muted. As soon as I unmute them, exit the window, and reenter (immediately), they're muted again.

update 2:
restarted and now gksudo gedit /etc/init.d/alsa-base.conf brings up an empty window. but my speakers work and my headphone jack works. SoundRecorder plays back static and clearly is not detecting noise.
In other words, I'm right back to where I started.

---

