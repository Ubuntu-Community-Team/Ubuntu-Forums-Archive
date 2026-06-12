---
title: "A2DP - bluetooth stereo problem"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by darkzavulon on 2011-06-16
Hey.
I've bought nokia BH-504 headset. I've paired it, using my bluetooth adapter, and I can output sound in HSP mode.
But if I switch to A2DP mode, sound begins to pause like every 0.5 sec. Since HSP isn't about good quality, I'm looking for the solution.
Google gave me almost nothing.

---

### Post by darkzavulon on 2011-06-19
BUMP.

I figured out what happens with sound. Syslog is full of messages like
```

dark-MS-7226 pulseaudio[1817]: module-bluetooth-device.c: Skipping 17697 us (= 3120 bytes) in audio stream

```

---

