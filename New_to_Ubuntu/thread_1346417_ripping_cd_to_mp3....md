---
title: "ripping cd to mp3..."
date: 2009-12-05
forum: New to Ubuntu
---

### Post by melrokz on 2009-12-05
plz tell me how to write a gstreamer pipeline to encode mp3 at 192kbps?

I have sound juicer, but to encode mp3 at different bitrates is rather difficult. plz help me...

---

### Post by hansdown on 2009-12-05
Hi melrokz.

Stchman says it better than I can.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

---

### Post by Linuxforall on 2009-12-05
sudo apt-get install ripperx 

Pretty close to the Windows front end for lame and other codecs. Also features CD Paranoia for extraction like EAC.

---

### Post by 3rdalbum on 2009-12-05
There should already be a pipeline present for MP3 at 128kbps. Just edit that and change the number "128" to "192".

---

