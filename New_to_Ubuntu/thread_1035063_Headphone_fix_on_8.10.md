---
title: "Headphone fix on 8.10"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by atngplusultra on 2009-01-09
so,
I've had to enter the classic
```
options snd-hda-intel model=3stack
```
to the end of alsa-base,

and i've tried adding
```
position_fix=1
```
in there, but that didn't seem to do anything.

all in all, the volume of my headphones is linked to the volume of my speakers;
however, i can mute the headphones ***ONLY*** (not the speakers) by muting the "PCM-2" channel on my sound device, Realtek ALC861-VD (Oss Mixer). I'd like it to be the other way around, where I can mute a channel to get sound out of only my headphones, but I don't really know if that's even going to happen.

anything else to try?

---

### Post by floatingpoint on 2009-01-09
if it's just regular jack outputs couldn't you swap them around?

---

### Post by atngplusultra on 2009-01-09
sorry, I suppose I neglected to mention that this is a laptop
so, unfortunately, no, the only ways to get sound are the on-board speakers or the headphone out.

(it's a Toshiba A135-S4677, to be precise, and it's got a history of giving me problems with sound)

---

