---
title: "How to set volume for my system?"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by baskar007 on 2009-10-14
hi friends,
i am using ubuntu with KDE. I can't set my PCM volume to 100%. each time it changes volume to 70% after reboot.

how can i fix this ?? 

i have tried to set volume by running alsamixer on terminal but no effect.

i am have AlsaMixer v1.0.18 .

---

### Post by mike1821 on 2009-10-14
Maybe you can try this command:

```
sudo /etc/init.d/alsa-utils store_levels
```

---

