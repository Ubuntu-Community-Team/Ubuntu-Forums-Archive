---
title: "Ubuntu 11.04 No Sound"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by amiddle on 2011-07-12
Hey People,

I am new to Ubuntu but not to Linux, usually used to RedHat. I have installed Ubuntu 11.04 on my Toshiba Satellite Pro A120 laptop and most of it seems fine but i cannot get the sound to play on it.
I have tried a few things, the obvious (unmuted, etc.), i have installed the Sound "Extras", tried removing and re-installing the alsa drivers,i have also tried adding the "options snd-hda-intel model=generic" to the alsa-base.conf file.
Now what i have noticed when i do a "aplay -l | grep card" it returns two entries, both using Card 0. Is this causing a conflict? Here is the output:
~$ aplay -l | grep card
card 0: SB [HDA ATI SB], device 0: ALC262 Analog [ALC262 Analog]
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]

Anyone got any ideas?
Thanks,
Aaron.

---

### Post by LowSky on 2011-07-12
use terminal and use the command 

```
 alsamixer
```

see if anything is muted... you also see if things are muted from sound preferences too from ubuntu panel. see if the right card is picked and the correct settings.

---

### Post by computingchap on 2011-08-05
This problem was frustrating me for ages. I then realised that if I booted into Windows (dual boot) and unmuted the sound, then booted back into ubuntu 11.04, everything was OK without modding anything. I also have the Tosh Satellite Pro A120.

---

### Post by jamesisin on 2011-11-12
computingchap - So then... Windows' mute changed something at the hardware level?

---

