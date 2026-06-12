---
title: "amarok wont play"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by patchido on 2009-02-26
i plug in my ipod into my computer, and i want to listen to music thats inside my ipod but this shows up

Audio output unavailable; the device is busy.
xine parameters:

---

### Post by BOZG on 2009-02-26
Are there any other programmes using your sound card at the same time that you're using Amarok?  The error suggests that you're using the old OSS system.  Go to System->Preferences->Sound and make sure that all the options are set to use PulseAudio and if that doesn't work properly, try using ALSA.

---

### Post by patchido on 2009-02-26
so.... i can olny use sound with 1 program at the time???
i cant have msn with sounds and also amarok?

---

### Post by sandyd on 2009-02-26
are you using alsa or OSS?

---

### Post by BOZG on 2009-02-27
> **patchido said:**
> so.... i can olny use sound with 1 program at the time???
i cant have msn with sounds and also amarok?

If you currently using OSS, then you can't but if you change your setting so that they use ALSA or PulseAudio (depending on which gives you better sound quality), you'll be able to use both MSN and amaroK.

---

