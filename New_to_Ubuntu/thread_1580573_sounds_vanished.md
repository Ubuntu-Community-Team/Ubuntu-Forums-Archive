---
title: "sounds vanished"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by daveboy23 on 2010-09-23
hi everyone,
my sound used to work perfectly (on acer 4820tg).  i've changed a couple of settings on alsamixer (as indicated by the ubuntu help) so i can work with skype (mic was not working).  after that, everything worked fine (inc. mic)

today, i've changed the sound settings in the normal audio mixer and now my sound is gone, except for youtube (so i'm guessing internet).
thanks people

---

### Post by khelben1979 on 2010-09-23
If Alsamixer is the source of your problem, it would help if you posted a screen dump on how it looks like with your current sound settings.

Do you know what [sound server]("http://en.wikipedia.org/wiki/Sound_server") your Ubuntu system is configured to use?

---

### Post by lkjoel on 2010-09-23
> **daveboy23 said:**
> hi everyone,
my sound used to work perfectly (on acer 4820tg).  i've changed a couple of settings on alsamixer (as indicated by the ubuntu help) so i can work with skype (mic was not working).  after that, everything worked fine (inc. mic)

today, i've changed the sound settings in the normal audio mixer and now my sound is gone, except for youtube (so i'm guessing internet).
thanks people
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by daveboy23 on 2010-09-24
perfect, sound fix thing was great.  but i only followed up to the OSS installation.  could you explain what are all these things all about? do i need that OSS thing?

---

### Post by lkjoel on 2010-09-24
> **daveboy23 said:**
> perfect, sound fix thing was great.  but i only followed up to the OSS installation.  could you explain what are all these things all about? do i need that OSS thing?
If your sound isn't fixed, yes.
If you have followed: Fix your sound!, then use Post-Fix your sound!.

---

### Post by daveboy23 on 2010-09-25
Thanks so much for your help

---

### Post by khelben1979 on 2010-09-25
Just a note: you don't need to install [OSS]("http://en.wikipedia.org/wiki/OSS") since it's part of the [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture") sound system which is part of your Linux kernel. However, if you find that this installation of OSS 4 works better, then you can get rid of your ALSA as have been suggested in this thread.

Check the wiki links if you're uncertain about what's all this is about and what you're doing. For instance, ALSA emulates OSS and so every application in Ubuntu which requires OSS will have no problems unless they require the latest version of OSS version 4.

---

### Post by lkjoel on 2010-09-25
> **khelben1979 said:**
> Just a note: you don't need to install [OSS]("http://en.wikipedia.org/wiki/OSS") since it's part of the [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture") sound system which is part of your Linux kernel. However, if you find that this installation of OSS 4 works better, then you can get rid of your ALSA as have been suggested in this thread.

Check the wiki links if you're uncertain about what's all this is about and what you're doing. For instance, ALSA emulates OSS and so every application in Ubuntu which requires OSS will have no problems unless they require the latest version of OSS version 4.
OSS 3 is part of ALSA.
OSS 4 is not.

---

