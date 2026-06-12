---
title: "Using Alsa Mixer instead of PulseAudio"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by DanPiazza on 2011-01-11
PulseAudio caused any audio/video streams to studder slightly, which was rather annoying. I uninstalled all PulseAudio packages and started using Alsa Mixer instead. Unfortunately, I no longer have function key volume control, or a volume applet in the taskbar. I've Googled the problem and found fixes, but they don't seem to work for me. I'm running UNR 10.10, any ideas?

---

### Post by Eternal_Light on 2011-01-11
Try uninstalling/reinstalling the alsa packages with an asterisk following right after the name of the package :

sudo apt-get install example*

this will download and install all needed AND recommended packages, which is a lot of packages. It may work i have no idea but I guess its worth the try.

Reboot after the installation and search in the menu>multimedia. The tray program might exist and have autolaunch turned off so you will have to manually launch it.

GoodLuck

---

### Post by DanPiazza on 2011-01-11
The asterisk tip is pretty helpful in general. Thanks.

---

