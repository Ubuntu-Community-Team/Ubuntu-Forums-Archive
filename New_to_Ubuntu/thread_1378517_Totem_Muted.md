---
title: "Totem Muted"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Psumi on 2010-01-11
Totem is currently muted, according to the posts in this thread: [http://ubuntuforums.org/showthread.php?p=8046635](http://ubuntuforums.org/showthread.php?p=8046635)

I had to remove all the pulseaudio stuff and made sure gstreamer-properties was set to autodetect. It's all as such, but totem is still muted.

Installing pulseaudio doesn't help either, still muted.

---

### Post by warfacegod on 2010-01-11
Is the System Master Volume muted?

---

### Post by Psumi on 2010-01-11
> **warfacegod said:**
> Is the System Master Volume muted?

alsamixer says master is unmuted. But apparently, Master Mono was muted, now it works.

Also, what's the command to store alsa prefs?

---

### Post by warfacegod on 2010-01-11
> Also, what's the command to store alsa prefs?

I would imagine that ALSA would save your settings automatically.

---

### Post by Psumi on 2010-01-11
> **warfacegod said:**
> I would imagine that ALSA would save your settings automatically.

I found it, I guess:

```
sudo alsactl store
```

But whenever I start totem, it starts muted, I can obviously unmute it, but that's a bit out of the way.

---

### Post by warfacegod on 2010-01-11
```
sudo apt-get purge gnome-media
```


```
sudo apt-get install gnome-media
```

That will remove Alsa and then reinstall it. Hopefully that will zero out whatever is causing it to start in mute.

---

### Post by warfacegod on 2010-01-11
Wait, is it Totem itself that's muted or the system volume? If it's Totem then remove it and reinstall.

---

### Post by Psumi on 2010-01-11
> **warfacegod said:**
> Wait, is it Totem itself that's muted or the system volume? If it's Totem then remove it and reinstall.

It works now suddenly after doing the multimedia codec guide and rebooting. Well, this is solved now, so I'll mark it as such.

And no, I don't even have gnome-media, I installed alsa-utils manually.

---

