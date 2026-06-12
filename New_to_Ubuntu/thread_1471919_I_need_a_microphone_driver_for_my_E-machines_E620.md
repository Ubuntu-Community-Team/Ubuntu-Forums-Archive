---
title: "I need a microphone driver for my E-machines E620"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Absolome on 2010-05-03
But I'm not sure where to look!

help please!

---

### Post by GSF1200S on 2010-05-03
> **Absolome said:**
> But I'm not sure where to look!

help please!

How do you know you need a driver? It should be part of the driver that provides you with sound. Type:
```
alsamixer
```
in a terminal and take a look at the controls. Perhaps the microphone channel is muted? You can tell as a muted channel will have MM below the slider, while a unmuted channel will have a 00 under the slider. Take a look..

---

### Post by Absolome on 2010-05-03
no mm's under anything

Audio mixer says it recognizes mic, but mic isn't picking up sound

I have on that output

Master 00
Headphones 00
PCM nothing, but bar is colored like the others
Front 00
Front Mic nothing, and bar is not colored
Mic Boost ^same^
Beep 00, nothing in the bar

---

### Post by GSF1200S on 2010-05-03
> **Absolome said:**
> no mm's under anything

Audio mixer says it recognizes mic, but mic isn't picking up sound

I have on that output

Master 00
Headphones 00
PCM nothing, but bar is colored like the others
Front 00
Front Mic nothing, and bar is not colored
Mic Boost ^same^
Beep 00, nothing in the bar

The bar SHOULD be colored. To navigate in alsamixer press left or right to move between channels, and press up and down to change the volume level. M mutes or unmutes a channel. I suggest raising the volume on both Front Mic and Mic Boost...

---

### Post by Absolome on 2010-05-03
> **GSF1200S said:**
> The bar SHOULD be colored. To navigate in alsamixer press left or right to move between channels, and press up and down to change the volume level. M mutes or unmutes a channel. I suggest raising the volume on both Front Mic and Mic Boost...
 according to skype people, mic boost makes static and front mic does nothing at all when I raise it

oh also, I can't mute wither one of these channels, there is no box under them where the 00 would appear

---

### Post by Absolome on 2010-05-03
bump

---

