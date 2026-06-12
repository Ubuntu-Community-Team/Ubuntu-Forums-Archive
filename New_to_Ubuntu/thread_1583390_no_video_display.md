---
title: "no video display"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by nemodot on 2010-09-27
Hi, i'm having trouble playing video files.

Not only that, when i play mp3 files in the totem player there are no visualizations.

Aparentrly is not a lack in codecs or drivers. I have the latest nvidia driver. Videos play with a black screen, audio is fine.

How can I reinstall all video packages?

I'm sure its not a hardware problem because I have no problems watching videos on windows XP.

---

### Post by jtarin on 2010-09-27
I would highly recommend [VLC player]("http://www.videolan.org/vlc/download-ubuntu.html") for all audio and video files. It comes with most of the codecs you will ever need. Read the page thoroughly there are extras to be had.

---

### Post by nemodot on 2010-09-27
> **jtarin said:**
> I would highly recommend [VLC player]("http://www.videolan.org/vlc/download-ubuntu.html") for all audio and video files. It comes with most of the codecs you will ever need. Read the page thoroughly there are extras to be had.

Already tried VLC, the problem remains.

---

### Post by jtarin on 2010-09-27
Start Totem or VLC from the terminal and watch for probable error messages.

---

### Post by nemodot on 2010-09-27
> **jtarin said:**
> Start Totem or VLC from the terminal and watch for probable error messages.

Did that with totem, no error messages. Did the same with VLC. This showed up:

```
nemodot@nemodot:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x92f6148] main libvlc: Ejecutar vlc con la interfaz predeterminada. Usa «cvlc» para usar vlc sin interfaz.
[0x99feb90] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

```

---

### Post by jtarin on 2010-09-27
No clue....Google for "no visualizations totem player ubuntu".

---

### Post by nemodot on 2010-09-27
> **jtarin said:**
> No clue....Google for "no visualizations totem player ubuntu".

Maybe I could reinstall video packages and codecs, but I don't know how.

---

### Post by jtarin on 2010-09-27
> **nemodot said:**
> Maybe I could reinstall video packages and codecs, but I don't know how.Menu System>Administration>Synaptic Package Manager enter the name of the package you want to find in the search box. If it is installed it will show a green box. Left-click on the box and select remove everything. Click Apply from the menu bar. Then to reinstall left-click and select install.

---

### Post by nemodot on 2010-09-28
> **jtarin said:**
> Menu System>Administration>Synaptic Package Manager enter the name of the package you want to find in the search box. If it is installed it will show a green box. Left-click on the box and select remove everything. Click Apply from the menu bar. Then to reinstall left-click and select install.

I ment I don't know which packages to reinstall.

I'm thinking of reistalling ubuntu completely:confused:

---

### Post by jtarin on 2010-09-28
Reinstall for a Movie Player? You need to describe your problem in more detail, be specific.

---

