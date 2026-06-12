---
title: "how do i remove totem from my system"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by bobin on 2009-05-29
hellllp

---

### Post by lisati on 2009-05-29
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by QIII on 2009-05-29
First, before you do anything .... WHY?



System -> Administration -> Synaptic Package Manger.

Enter your password.

Search for "totem".

Click the green boxes (most of them will have the Ubuntu symbol beside them).

Select Mark for Removal or Mark for Complete Removal.

---

### Post by Paqman on 2009-05-29
I uninstalled Totem a while back as I never use it. Or at least: I thought I never used it. Turns out that Gnome uses Totem to generate thumbnails for videos. So no Totem = no thumbnails.

---

### Post by kpkeerthi on 2009-05-29
> **Paqman said:**
> I uninstalled Totem a while back as I never use it. Or at least: I thought I never used it. Turns out that Gnome uses Totem to generate thumbnails for videos. So no Totem = no thumbnails.

Just install ffmpegthumbnailer and you will get your video thumbnails back.
```
sudo apt-get install ffmpegthumbnailer
```

---

### Post by Viva on 2009-05-29
I think it uses totem for audio preview too(when you hover over mp3 or wav files). Why delete it? Just leave it alone even if you don't use it.

---

### Post by Paqman on 2009-05-29
> **kpkeerthi said:**
> Just install ffmpegthumbnailer and you will get your video thumbnails back.
```
sudo apt-get install ffmpegthumbnailer
```

Just tried it, gconf didn't pick up the change. Lost audio and video thumbnails altogether. The man page for ffmpegthumbnailer doesn't seem to offer any clues, either.

---

