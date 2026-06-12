---
title: "linked mic capture and playback in jaunty"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Doormat on 2009-05-12
Hello,

I have a desktop with a creative sound blaster xfi card. I installed jaunty 64 and was able to compile the creative driver from source and sound worked. Now my only issue is that to get my microphone working (plugged into the flexijack port) I need to turn up the microphone capture volume to get any microphone input (obviously). The issue is that this in turn raises the microphone playback (so whatever is heard through the mic is then sent through my speakers). How do I fix this? I'd like to be able to use skype without hearing myself through my speakers.

---

### Post by rajeev1204 on 2009-05-12
> **Doormat said:**
> Hello,

I have a desktop with a creative sound blaster xfi card. I installed jaunty 64 and was able to compile the creative driver from source and sound worked. Now my only issue is that to get my microphone working (plugged into the flexijack port) I need to turn up the microphone capture volume to get any microphone input (obviously). The issue is that this in turn raises the microphone playback (so whatever is heard through the mic is then sent through my speakers). How do I fix this? I'd like to be able to use skype without hearing myself through my speakers.

Try using alsamixer to get more individual control over your sound.

Its a terminal application.

---

### Post by Doormat on 2009-05-12
I have used alsamixer and it ties the mic playback and capture.

---

