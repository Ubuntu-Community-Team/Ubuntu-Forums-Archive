---
title: "Would you have any idea how to stream your website, without running Apache?"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-28
Hello,

I would like to stream my webcam for a friend that windows xp. I wouldnt like to install an Apache on 8080 / 80.

The idea would be to stream the /dev/video0 to a port >5000. Then with wmplayer he could see the webcam. Is that possible somehow with Linux? 


:KS:KS

---

### Post by juancarlospaco on 2010-01-28
VLC can do that...

---

### Post by spiderbatdad on 2010-01-28
[http://www.linuxjournal.com/article/6720](http://www.linuxjournal.com/article/6720)
[http://www.videolan.org/](http://www.videolan.org/)

---

### Post by frenchn00b on 2010-01-28
> **juancarlospaco said:**
> VLC can do that...

well it is for an headless computer, the ssh server. Is there any non X11 possibilities?

darwin [http://www.techgalaxy.net/blog/playlists.jpg](http://www.techgalaxy.net/blog/playlists.jpg) looks cool but it is only of mp3 &/ mp4 ... format, not from /dev/video0 right? but still, it is non-X11. :)

---

### Post by marshmallow1304 on 2010-01-28
> **frenchn00b said:**
> well it is for an headless computer, the ssh server. Is there any non X11 possibilities?


[vlc-nox]("apt://vlc-nox")
> This package contains a version of VLC that does not require X and that is
thus suitable for headless servers.

---

