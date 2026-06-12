---
title: "No sound in Adobe flash."
date: 2009-10-28
forum: New to Ubuntu
---

### Post by Treeh on 2009-10-28
Hello,

I've reinstalled Flash in different manners countless times for my x64 9.04 version of Ubuntu, yet it refuses to play sound.

I'm using PulseAudio, and it doesn't even list flash as a source if a video is playing.

I'm using ALSA 1.0.2.0 coupled with an ASUS Xonar STX Essence sound card.

Anyone have any idea how to fix this? It did work once, briefly--but then I restarted and it was broken again.

---

### Post by JDShu on 2009-10-28
Try getting rid of everything flash on your system before installing it with:

```
sudo apt-get purge flash*
```

---

### Post by Treeh on 2009-10-29
I updated to 9.10, did a clean install.

Installed flash via Adobe's official alpha version of x64 flash.

Installed Alsa 1.0.21 to get my soundcard to work, then used KMIX to select the "headphone" channel from my audio card.

Sound STILL doesn't work.

---

### Post by Treeh on 2009-10-29
I reinstalled, skipped the ALSA installation, and used a converter cable to switch to my card's default output and it works fine.

I feel like an idiot.

---

