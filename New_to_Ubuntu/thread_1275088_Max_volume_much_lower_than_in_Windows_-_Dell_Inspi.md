---
title: "Max volume much lower than in Windows - Dell Inspiron 1525"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by Caddy2187 on 2009-09-25
I've just installed Ubuntu onto my laptop. Fairly new to it, only problem I'm having so far is that the max volume seems to be fairly low. Anyone any ideas of how to make it louder? Im running a Dell Inspiron 1525.
Thanks

---

### Post by NightwishFan on 2009-09-25
Open a terminal and type this command:
```
alsamixer -c0
```

You can see all the sliders from there. You can also use the mixer in the top right corner, it has a drop down menu with different settings.

---

### Post by Caddy2187 on 2009-09-28
> **NightwishFan said:**
> Open a terminal and type this command:
```
alsamixer -c0
```You can see all the sliders from there. You can also use the mixer in the top right corner, it has a drop down menu with different settings.

Sorry its taken me a few days to get back, I've been away! Thank you for your reply. In some of the other posts I read before I tried to fix it myself I read that OSS can produce higher volume than ALSA, so I switched over to that in the sound settings. I tried what you said and looked at the volume sliders. They are all high now, still doesnt seem to be quite as loud as Windows. Im not too bothered though! Thanks for you help

---

### Post by HarrisonNapper on 2009-09-28
Does your comp use PulseAudio? Sounds like the issue I had before. Also, if you're running ALSA, OSS emulation should do just fine for OSS apps. Unless you're trying to run a production setup, though, I wouldn't say ALSA is too critical.

---

