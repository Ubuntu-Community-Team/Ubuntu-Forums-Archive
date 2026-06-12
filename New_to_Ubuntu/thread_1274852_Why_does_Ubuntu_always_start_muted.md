---
title: "Why does Ubuntu always start muted?"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by rob86 on 2009-09-25
I'm not sure if this happens on gnome, but it happens with Xfce. Every time I boot up, the sound is muted and I have to go into the mixer and unmute it. It's very annoying, any idea why it always gets muted?

---

### Post by ~sHyLoCk~ on 2009-09-25
> **rob86 said:**
> I'm not sure if this happens on gnome, but it happens with Xfce. Every time I boot up, the sound is muted and I have to go into the mixer and unmute it. It's very annoying, any idea why it always gets muted?

```
alsamixer
```
Max the volume

```
sudo alsactl store
```

---

