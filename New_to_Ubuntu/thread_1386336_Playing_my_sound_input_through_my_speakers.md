---
title: "Playing my sound input through my speakers"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by themusicalduck on 2010-01-20
How could I make the line input on my soundcard playback through the output on the soundcard using pulseaudio?

I would like to be able to play the bass guitar through my computer speakers while I don't have a proper amp with me, but I can only persuade it to record sound that I can playback afterwards.

Everything appears to be right in sound preferences and alsamixer. I'm on Ubuntu 9.10.

---

### Post by kitserve on 2010-01-21
A word of warning: computer/hifi speakers aren't really designed for this sort of use! There is a significant chance that you'll blow your speakers trying it (I should know, I've done it myself in the past)!

---

### Post by themusicalduck on 2010-01-21
Hmm, I don't think that should be a problem as long as I keep the volume down. I have it running through a mixing desk so I have full control over the input. I suppose I could put a bass cutoff on it to be safe.

How did you blow your speakers in the past?

---

### Post by kitserve on 2010-01-25
I tried running a guitar through them without keeping the volume down! Since blowing my speakers I just avoid running guitars and mics through computer speakers or hifis out of fear of doing it again! Bass cutoff sounds like a good idea, it sounds like you have a better idea of what you're doing than I did so maybe you'll be alright.

---

### Post by bobbysmith007 on 2010-09-15
In the mean time you can:
 * go the terminal
 * Type "alsamixer" and hit enter
 * go right a bunch till you find the input you are looking for ( you may have to go past the end of the screen)
 * make sure you turn the volume up and press m to unmute (if necessary)
 * you should hear your guitar / tv / game console etc (with no lag)

---

