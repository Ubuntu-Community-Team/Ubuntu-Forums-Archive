---
title: "weird bug"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by bijak_riyandi on 2010-11-23
hello all
I'm just converted from Windows to Ubuntu

I got some weird bug when playing movies with Totem (enchanced with totem-xine, btw)

when I start playing the movie, it doesn't run smoothly. but it'll run smooth if I move the mouse or press a button on the keyboard.

minutes after that, the player run smooth, and minutes later the bug came again.

weird isn't?

I'm using Ubuntu 10.10 on acer 4736 (Core2 Duo 2.2 GHz processor, 3 GB RAM on two channels)

any ideas what to do?

---

### Post by wishyjr on 2010-11-23
hmmm seems strange, perhaps it might be an idea to make sure that you have all of the various codecs etc. 

try entering this into a terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

some more info on this can ben found here:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

or perhaps you have visual extras on? this sometimes effects video playback depending on the driver installed. what video card are you using?


cheers
wishy

---

### Post by bijak_riyandi on 2010-11-23
Intel GMA 4500MHD video card

well, I found the bug not only when playing videos, but also when playing musics!

strange and annoying really...

btw, thanks for the help
I'll try it today, and see if it works

---

### Post by bijak_riyandi on 2010-11-24
worked a little bit
but at least, when the bug comes, media player plays smoother than before I installed ubuntu-restricted-extras

thanks

---

