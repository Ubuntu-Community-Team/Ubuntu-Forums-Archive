---
title: "No Sound: Karmic and Skype 2.1"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by haychem on 2010-03-22
Hello, I am an absolute beginner.  I just downloaded ubuntu 9.1 yesterday.  So far everything has worked wonderfully except for the sound.  I fixed the problem by following some steps I found on this forum; I can't find the exact post that I followed, but this is what I think I did.
1.  Edited alsa-base:
     Code:
sudo gedit /etc/modprobe.d/alsa-base

2.  Added:
     Code:
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1

I really don't understand why, but my sound works now - hurrah!  Except, of course, when I use skype.  I downloaded Skype 2.1 32 bit.  I can hear skype's start-up sound, but then when I do the echo/sound test, all is silent.  I've tried to read about possible fixes on this forum. . .to no avail.  Like I said, I'm a complete beginner, so I would be appreciative of any help you can provide, but please keep it simple!  ;)

(Oh yeah, and I'm running everything on an HP Pavilion dv4-2045dx.)

Thanks!

---

### Post by quinnten83 on 2010-03-22
In skype you can choose input and output sounddevice.
Make sure you have the right one selected.
It doesn't sound like you removed pulse audio, so rightclick on the speaker icon on the panel, select soundspreferrences and make sure sound for skype is turned on.

---

