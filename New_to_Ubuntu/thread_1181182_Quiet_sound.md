---
title: "Quiet sound"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Sedative on 2009-06-07
Hey, it's me again. 

I have managed to fix all of my problems in Ubuntu.
Fixing my lack of sound has led to one more.

The sound is quiet with all of my volume on max. I don't know if the speakers have gotten bad (unlikely, I got this laptop around February), or if it's a problem with Ubuntu. 

When I play music in AmaroK or on Youtube or something, the sound is quiet and I can hardly hear it. Help?

---

### Post by Johan-Steyn on 2009-06-07
Hi,

Are you using Alsa or Pulse?

Please go to System>Preferences>Sound and check which one you're using.

Regards,

JS

---

### Post by Sedative on 2009-06-07
**Sound Events**
Sound playback: Autodetect


**Music and Movies**
Sound playback: Autodetect

**Audio Conferencing**
Sound Playback: Autodetect
Sound Capture: HDA Intel STAC92xx Analog (ALSA)

**Default Mixer Tracks**
Device: Capture: HDA Intel STAC92xx Analog (PulseAudio)

---

### Post by Johan-Steyn on 2009-06-07
OK,

Now we are going to play around with the settings until we can find the one that will work for you.

Change all your devices in System>Preferences>Sound to Pulse. Click the test button to test each one before moving to the next.

Change the Default mixer tracks to HDA Intel (Alsa Mixer).

Click close.

Go to the speaker icon on the top task bar. Right click. Select the Open Volume Control option.

Make sure all sliders are at maximum.

Check the effect, and post back.

Regards,

JS

---

### Post by Sedative on 2009-06-07
Thanks! I got my sound to work fully! I really appreciate the time.

---

### Post by Johan-Steyn on 2009-06-07
My Pleasure.

I hope you enjoy your Ubuntu experience.

Regards,


JS

---

### Post by mscyber07 on 2009-06-19
I second the above and would like to add for anyone else that I had the same problem, but found it to be that my "Front" setting in Volume Control was less than max.  I toyed with it for a good chunk of time before realizing that I dislike pulseaudio.  Especially after it kept messing up firefox's sound.  (The problem's been rectified, but it was an obvious mistake that should've never occurred in the first place)

          Anyway, good luck and happy Ubuntu-ing!

---

### Post by noworldorder on 2010-06-20
in terminal type alsamixer.    Play wround with the levels

---

