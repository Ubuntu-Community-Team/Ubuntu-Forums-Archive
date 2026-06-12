---
title: "HP Altec Lansing Sounds NOT Working?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by jonnyboy7012 on 2008-12-07
i have an HP TX2110us, i couldn't get the touch screen drivers to work exactly, but whats even worse is that the sound driver isn't working. To be honest I'm mostly new at this, and cant live without sound. The sounds dont work with headphones and without... 

can anyone help me?

---

### Post by jpyanowski on 2008-12-07
> **jonnyboy7012 said:**
> i have an HP TX2110us, i couldn't get the touch screen drivers to work exactly, but whats even worse is that the sound driver isn't working. To be honest I'm mostly new at this, and cant live without sound. The sounds dont work with headphones and without... 

can anyone help me?

jb, 

I have a HP 2210us that also has Altec Lansing speakers. I have no problem with sound. Go to System>Preferences>Sound and tell me what device is listed there.[HTML][/HTML]

---

### Post by jonnyboy7012 on 2008-12-07
The devices list as follows:
HDA NVidia (Alsa mixer)
Realtek ALV861-VD (OSS Mixer)
Playback: ALSA PCM on front: 0 (ALC861VD Analog)...
Capture: Monitor SOurce of ALSA PCM on front: 0 (AL...
Capture: ALSA PCM on front: 0 (ALC861VD Analog) vi...

and when i try to test the sound playback i leave it on autodetect and it gives me this message:
audiotestsrc wave=sine freq=512 !
audioconvert ! audiosample!
gconfaudiosink: failed to connect stream:
invalid argument

---

### Post by dakid on 2008-12-22
I hope this works. I figured this out by reading different forums that didn't work. As a result, I combined ideas. 

In the terminal type: 

gksudo gedit /etc/modprobe.d/alsa-base

then at the the bottom paste the following:

options snd-pcsp index=-2
options snd-hda-intel enable_msi=1

Then reboot.

I hope this works for you like it did for me.

---

