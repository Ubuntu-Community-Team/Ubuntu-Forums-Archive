---
title: "broke my sound"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by portets on 2009-05-03
just tried updating to alsa 1.0.19 in kubuntu to enable my internal mic.
now when i login it says something like "hda intel alc888 stopped working, reverting back to ." i assume the space means "nothing". i have no sound now.:confused:

any help appreciated

---

### Post by inobe on 2009-05-03
open mixer window and turn up pcm or anything else like master and front.

---

### Post by portets on 2009-05-03
kmix wont open. pretty sure i lost my sound card driver. and i tried reverting back to alsa 1.0.18 using the package manager.

---

### Post by inobe on 2009-05-03
locate kmix in the menu and click it, tell me what errors you get.

---

### Post by portets on 2009-05-03
okay, i got kmix to work by replacing alsa-base.conf with an older backed up file.

how would i find out which version of alsa my computer is using?

---

### Post by Master_Odin on 2009-05-03
```

cat /proc/asound/version

```

---

