---
title: "Sound Problems"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by BloodyPintle on 2009-10-10
I just installed Ubuntu yesterday and I've been having some sound problems.

First of all, some of the system sounds (Alert Sound and Logout) just seem to play as really loud beeps. I can preview them fromthe Sound Preferences just fine, but when they play normally they're just beeps.

Second of all, it doesn't matter what site I'm on, EVERY flash animation has a 2 sec. delay between when a sound SHOULD happen, and when it DOES happen.

Edit: Also, Pidgin makes a buzzing noise whenever someone sends me a message.

---

### Post by Gannon8 on 2009-10-10
I do not believe flash is well supported on Linux, so your mileage with that will vary. As for the others, maybe your speakers are getting old? I'm not sure, sorry :(

---

### Post by RichardLinx on 2009-10-10
Are you using pulse audio? If you are follow this guide: [http://linsux.org/blog/grubby/2009/09/06/howto-remove-pulseaudio-install-esound/](http://linsux.org/blog/grubby/2009/09/06/howto-remove-pulseaudio-install-esound/)

That guide will show you how to remove pulse audio and install esound. To be blunt, pulse audio sucks and is most likely what's messing up your sound.

---

### Post by BloodyPintle on 2009-10-10
> **Gannon8 said:**
> maybe your speakers are getting old?
I doubt it. I just got this laptop last year

Edit: Installing esound fixed the flash problem, but not the beeping

---

