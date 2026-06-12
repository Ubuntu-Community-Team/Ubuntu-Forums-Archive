---
title: "Best laptop sound card for Ubuntu?"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by aharown07 on 2009-08-26
Due to various problems w/the integrated sound driver on my Toshiba (got basic audio out working but can't record... can't use Skype even runing as root), I'm thinking about getting a sound card to plug in  (I know these are not called PCMCIA anymore, but what's the lingo? PC Card?)

So, can anybody recommend a sound card that configures easily and produces really good results in the Linux environment?
(I also want to avoid spending alot if possible)

Edit: I shd probably mention that I've done some googling but so far what I'm finding is a bit old so...

---

### Post by SunnyRabbiera on 2009-08-26
Did you play around with the sound settings yet, try ALSA, OSS, Pulse?
Some cards like one form Linux sound playback over another.
Try turning off Pulse too.

---

### Post by aharown07 on 2009-08-26
Yes, played w/ALSA quite a bit. I ended up having to set something to "Acer" in a certain file just to get audio playback to work (even though the laptop is Toshiba).

I could try turning PULSE off... what is it and where's the "off switch"?

---

### Post by SunnyRabbiera on 2009-08-26
> **aharown07 said:**
> Yes, played w/ALSA quite a bit. I ended up having to set something to "Acer" in a certain file just to get audio playback to work (even though the laptop is Toshiba).

I could try turning PULSE off... what is it and where's the "off switch"?

Acer is probably your soundcard maker, anyhow pulse is a experimental sound server for linux and Ubuntu includes it by default.
The issue with pulse is that its still new and experimental so it might not work on all audio devices.
To remove it you will need to go into synaptic, or enter a command line and remove it with apt.
I am not saying it will work, but anything is worth a shot.

---

