---
title: "running 8.04.1 on a 64 amd - download say wrong archetecture l386"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by infoanalysis on 2009-01-07
running 8.04.1 on 64 bit mad dual core
the downloads for drivers etc. always say wrong archetecture 'i386' when I try to install.
I did not intall 64 bit I installed 32 bit so that I would run into problems with video and audio feeds etc.

---

### Post by Paqman on 2009-01-07
Can you type this into a terminal and post the output:
```

uname -m

```

---

### Post by mikewhatever on 2009-01-07
Does it really say 'wrong architecture', or does it say 'couldn't find packages for i386 architecture'? If that's the case, make sure you are connected to the internet and/or enable your repositories in System->Admin->Software Sources.

---

