---
title: "Sound card driver"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by thehereaway on 2010-07-03
Perhaps the entirely wrong website to post on, but i've just switched back to Windows from Ubunutu and I desperately need some help finding some drivers.

I'm looking for a driver for my sound card, it's an ATI IXP SB400 AC'97 Audio Controller. I can't find anything anywhere and am stuck without sound.  

I understand this isn't Ubunutu related, but this forum has always been very active and helpful in the past.

---

### Post by Silent Warrior on 2010-07-03
Sounds like a built-in card - I think IXP is what ATI calls/-ed their chipset-series before AMD stepped in. Have you looked at ALSA's matrix at alsa-project.org?
Anyway, what does
```
modprobe | grep snd-card-atiixp
``` produce?
(If entering 'modprobe -i snd-card-atiixp' gives you working sound, you may have to have that module load explicitly during start-up. I think I should wait for someone better suited for explaining how, though.)

---

