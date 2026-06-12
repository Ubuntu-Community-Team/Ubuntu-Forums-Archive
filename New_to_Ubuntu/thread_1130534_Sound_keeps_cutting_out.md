---
title: "Sound keeps cutting out"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by domeboy on 2009-04-19
My sound keeps cutting out, sometimes it is resolved by a reset. One time I had to reset and and reinstall all of my packages and that worked out as well.  

(When it occurs, I get no sound on sites such as Hulu.com, and my audio player crashes (Listen).  Nothing happens in VLC or any other player.  The mute button is not on.)

Has this happened to anybody else?

---

### Post by gackt on 2009-04-21
Alsa? Pulse audio? What are you using? here is what i ussualy do when sound crashes:
1. sudo alsa force-reload
2. Pulseaudio

Thats it.

---

