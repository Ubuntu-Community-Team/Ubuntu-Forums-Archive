---
title: "Logitech USB Headset just NOT working"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Alateriel on 2011-04-26
I'm sorry in advance for posting another thread about this, but I've been searching for almost an hour now and just **cannot** find a solution to my problem.

I just recently reinstalled kubuntu (10.10) and just can't get my headset to play sound (except for system sounds, which doesn't really do me much good...)

I've been pointed towards downloading gnome-alsamixer which didn't work; I've also been told to download pulseaudio (which I don't even know how to RUN, let alone use to solve my problem).

Can someone just give me a step by step and hold my hand through this?  Because I'm about ready to throw my headset against a wall.

---

### Post by spikoley on 2011-04-27
It sounds like an [issue]("http://ubuntuforums.org/showpost.php?p=7839421&postcount=7") I had with my Logitech USB Headset.

I was having issues with Totem.  This is what worked for me.

```
sudo apt-get install padevchooser
```

> 1.  Open Totem
2.  Alt + F2 and enter padevchooser to open PulseAudio Device Chooser utility
3.  Left click on the system tray icon
4.  Volume Control
5.  Playback tab
6.  Click the down arrow for Totem
7.  Move Stream
8.  Select USB Audio and test it

---

