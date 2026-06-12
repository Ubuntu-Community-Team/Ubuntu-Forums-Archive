---
title: "line in audio through speakers"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by bnhrobotics on 2010-02-06
In 9.04 I recall being able to set up my system so that I could play audio coming in through the 'line in' port directly through my speakers. In 9.10, this sound interface seems to have changed and I cannot do this anymore. Does anyone know how it can be done? Thank you.

---

### Post by jsmnuk on 2010-02-07
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

That's a good link to getting the latest version of Alsa. If it installs using those scripts, go to Applications>Sound&Video>Alsamixergui. When you open that, there should be a series of volume controls, and line-in should be one of them. Make sure it's not muted (the speakers above it should be green). I don't think that Alsa 1.0.20 had this feature, or at least I couldn't find it (I'm a newbie too).

---

