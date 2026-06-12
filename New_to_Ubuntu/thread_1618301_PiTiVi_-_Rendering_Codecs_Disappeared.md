---
title: "PiTiVi - Rendering Codecs Disappeared"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by jdixon567 on 2010-11-10
I'm trying to get PiTiVi to render my project with the x264 video codec, and lame mp3 audio codecs.  The option to use these codecs from "Render Project" -> "Modify" have disappeared.  Now all I have to work with is:

Video Codec
------
Theora 
Dirac
Smoke

Audio Codec
-------
Vorbis
Celt
Speex
FLAC

Does anyone know how to get my installed codecs appearing in these lists again?  Thanks!

---

### Post by jdixon567 on 2010-11-10
I tried encoding with Theora and Vorbis, but the speech is way too fast and it doesn't show the desktop capture portion of the video.  I lost all the ffmpeg codec options too for some reason.

---

### Post by jdixon567 on 2010-11-10
Ooh I found a sweet thread with which codec's to pick to get videos working on Youtube.  Unfortunately none of the ones I have available are listed:

[http://ubuntuforums.org/showthread.php?t=1483636](http://ubuntuforums.org/showthread.php?t=1483636)

I'm starting a weekly Drupal how-to series, but it's half a week behind because I'm a video production noob.

---

### Post by jdixon567 on 2010-11-10
Wow I'm being a n00b, All I had to do was change the Container to avi muxer, and I get the codecs back.  Hopefully this helps someone else.

---

### Post by hugmenot on 2010-11-10
Don’t use avi, use matroskamux. Or mp4mux. x264 is most naturally contained in mp4

---

