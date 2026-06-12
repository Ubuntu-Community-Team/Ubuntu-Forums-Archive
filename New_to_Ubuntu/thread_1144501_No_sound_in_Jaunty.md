---
title: "No sound in Jaunty"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by AgHawke on 2009-04-30
Hi all:

After installing Jaunty 9.04 I lost the sound on my computer.I'm using a Audigy Se  soundblaster sound card.In my sound pref are as follows 

Sound events
Audigy Se [SB0570] CA0106 (oss)

Music & Movies
Audigy Se [SB0570] CA0106 (oss)

Audio Conferencing
Sound Playback  Audigy Se [SB0570] CA0106 (oss)
Sound Capture  Pulse Audio Soundserver

Default mixer tracs
Capture CA0106 - CA0106 PulseAudio Mix

Is this the right config?,if not what should I have.
Thanks
AgHawke

---

### Post by MontelEdwards on 2009-04-30
> **AgHawke said:**
> Hi all:

After installing Jaunty 9.04 I lost the sound on my computer.I'm using a Audigy Se  soundblaster sound card.In my sound pref are as follows 

Sound events
Audigy Se [SB0570] CA0106 (oss)

Music & Movies
Audigy Se [SB0570] CA0106 (oss)

Audio Conferencing
Sound Playback  Audigy Se [SB0570] CA0106 (oss)
Sound Capture  Pulse Audio Soundserver

Default mixer tracs
Capture CA0106 - CA0106 PulseAudio Mix

Is this the right config?,if not what should I have.
Thanks
AgHawke
In the volume control, is the PCM up?

---

### Post by AgHawke on 2009-05-01
Hi All:

Monte my volumn is turned up all the way - still no sound???

Thanks
AgHawke

---

### Post by MontelEdwards on 2009-05-01
> **AgHawke said:**
> Hi All:

Monte my volumn is turned up all the way - still no sound???

Thanks
AgHawke


Yes but is the PCM up?
When you click open the volume control, I think it is properties or settings and it should say channels and make sure you check PCM.

and if none works run
```
pulseaudio -k ; start-pulseaudio-x11
```:guitar:
 i dont know if that needs to be run or not in root, so if it spews out an error add sudo to it.
Of course i think you know how to run this in the terminal,
Applications>Accessories>Terminal

---

### Post by AgHawke on 2009-05-01
Hi All:

Monty it refuses to let me do the command you gave me.

thanks
AgHawke

---

### Post by Eisenwinter on 2009-05-01
When you play a file, does it play regularly, but without sound?

Or, do you get an error message saying you can't open the device or the device doesn't exist?

Elaborate.

---

### Post by AgHawke on 2009-05-01
Hi All:

Eisenwinter I can play files in Audacity but no sound I'm at a loss on what I should do next.
Thanks
AgHawke

---

### Post by JoePits on 2009-06-29
what worked for me just now was to go into the mixer and hit the "Switches" tab and then put a check in the box for "audigy analog/digital output jack"  

i dont know why this works but it does.

---

