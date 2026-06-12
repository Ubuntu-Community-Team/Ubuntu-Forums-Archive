---
title: "No sound..."
date: 2009-03-20
forum: New to Ubuntu
---

### Post by RAZRBAKK on 2009-03-20
So I seem to have no sound for my Amarok player, as well as no sound on youtube or any other video sites. Sound works for my Kopete IM, and obviously start up/shut down.

I ran the codes

```
sudo apt-get install ubuntu-restricted-extras
```

But I still have no sound.

---

### Post by hobo on 2009-03-20
Try this it may help.

> $ sudo asoundconf reset-default-card

---

### Post by markbuntu on 2009-03-20
If you are using Amarok 1.4 in KDE then you need to go to Settings/Configure Amarok/Engine/OutputPlugin and choose alsa. If you are using pulseaudio choose pulseaudio. There are also a bunch of xine and amarok plugins that you need to get with your package manager.

---

