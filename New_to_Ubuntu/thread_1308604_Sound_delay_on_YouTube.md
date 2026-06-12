---
title: "Sound delay on YouTube"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by jfloydb on 2009-10-31
I've installed 9.10, along with the restricted extras, on an Acer Aspire One netbook. As far as I can tell, everything is working. However, when I try to watch a video on YouTube, there is a one second delay before the audio starts. Is anybody else having this problem? Does anybody know how to fix this problem? Or do you think that somebody at Canonical will fix this "bug" in an update? Thanks.

---

### Post by fjsimpkins on 2009-10-31
Im having a similar problem. Youtube will start a video and the sound is fine for a minute but then just cuts out completely. I have to restart firefox to get audio again from youtube but the same thing happens again. Hopefully it gets fixed in an update.

---

### Post by jfloydb on 2009-11-02
The sound delay occurs with any video file that I play, on YouTube or any vid from my hard drive . The picture/video starts, one second later the audio starts. Audio and Video are in sync, however.

I have read on this forum that it could be an Adobe flash problem, but I'm beginning to think it's related to the Totem player; but I really don't know. Any suggestion?

---

### Post by smallandy on 2009-11-16
I had the same problem with VLC and Wine (might have affected other applications, but I don't remember).
I fixed it by adding the following lines to /etc/modprobe.d/alsa-base.conf
 
options snd-hda-intel power save=0
options snd-hda-intel model=acer-aspire enable=1 index=0
 
I think it's the power management in alsa. It takes a couple of seconds to "turn on" your sound once it's gone into power save mode. I'm only a linux beginner myself so that's just an educated guess :)
 
Edit: Oh and I had to restart Ubuntu as well. Doing an alsa restart didn't fix the problem.

---

