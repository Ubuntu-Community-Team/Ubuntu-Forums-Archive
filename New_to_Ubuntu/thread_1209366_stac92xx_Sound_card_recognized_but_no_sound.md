---
title: "stac92xx Sound card recognized but no sound"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by OliverBarker on 2009-07-10
I have just completed a fresh install of 9.04 after tinkering around with theming, applications and more but realized there was no sound coming out of the speakers or headphones. Now, I've looked around for help with my stac92xx sound card but the only things I've been able to find either didn't work or I couldn't work out how to use! I'm a OS X user with a Ubuntu netbook (still looking into Hackint0sh)  but would prefer to keep Ubuntu. When putting "aplay -l" into terminal it seems to recognize my sound card yet even with volumes turned up I can't figure it why I don't get sound when listening to music or watching videos. It comes up with the following text.

> card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any ideas? Its a Compaq Mini 702 Netbook.

---

### Post by OliverBarker on 2009-07-10
/* Bump */

Just so this topic doesn't get lost...

---

### Post by halitech on 2009-07-10
first off, only bump a thread once every 24 hours so you don't get the mods upset with you :)

as far as your sound issue goes, have you installed the ubuntu-restricted-extras yet?

open a terminal and type
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by OliverBarker on 2009-07-10
Sorry, I didn't realize! Its installing as I speak, thanks for replying at least, lots of terminal activity. I'll restart afterwards just in case.

YES! Success with headphones anyway, speakers are still inoperable.

---

### Post by halitech on 2009-07-10
just noticed its a laptop, built in speakers or external speakers? maybe run alsamixer and make sure nothing is muted.

---

### Post by viljun on 2009-07-10
I just had similar problems with a new install (but different sound card)... 

I opened mixer (the speaker image on the panel) and I think the master volume (and speaker / line out) was defaultly muted and volume was down. Just turn everything up and unmute all - and make sure your speaker cable is ok and plugged in the right hole.

---

### Post by OliverBarker on 2009-07-10
There bult in speakers, its a Compaq 702 if you want to look it up. Speakers are just below the screen on the hinge between the base and screen.

---

