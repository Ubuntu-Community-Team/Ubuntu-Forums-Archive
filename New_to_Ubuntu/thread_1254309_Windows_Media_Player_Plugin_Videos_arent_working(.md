---
title: "Windows Media Player Plugin Videos arent working:("
date: 2009-08-31
forum: New to Ubuntu
---

### Post by yam.matt on 2009-08-31
Hello all, 
        I am using Ubuntu 8.04 LTS version, recently I installed Ubuntu restricted extras using the Add/Remove software manager, which is supposed to install many popular audio and video codecs, but when I play any video which requires Windows media player plug in, it doesn't play it, instead, nothing comes up :(, can anyone help me in this case? I would be really thankful:)

---

### Post by Perfect Storm on 2009-08-31
Which media player are you using?

---

### Post by zipperback on 2009-08-31
Are you trying to play Windows DRM protected files?

---

### Post by SlugSlug on 2009-08-31
install mozilla-mplayer

---

### Post by yam.matt on 2009-08-31
> **Artificial Intelligence said:**
> Which media player are you using?

I am using Totem and VLC player, Totem is my default player.

---

### Post by Perfect Storm on 2009-08-31
AFAIK, the w32codecs (for 64-bit the w64codecs) are aimed for Mplayer. VLC comes with its own codecs.

---

### Post by yam.matt on 2009-08-31
How do I install Mplayer:confused:

---

### Post by Perfect Storm on 2009-08-31
32-bit:
```
sudo apt-get install mplayer mplayer-fonts mozilla-mplayer w32codecs libdvdcss2
```

64-bit:
```
sudo apt-get install mplayer mplayer-fonts mozilla-mplayer w64codecs libdvdcss2
```


You might want to uninstall Totem mozilla plugin as well and vlc mozilla plugin;
```
sudo apt-get remove totem-mozilla mozilla-plugin-vlc
```

To prevent conflicts.

---

