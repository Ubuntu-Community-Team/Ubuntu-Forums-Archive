---
title: "Minitube has no sound, plays no Youtube"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-12-21
I have [Minitube]("http://www.ubuntugeek.com/minitube-slimline-youtube-client.html") installed via Ubuntu Geek's post.

It installed without reporting errors.

It calls the Youtube videos, but cannot play them nor is there sound. 

It says: "Cannot find plugin for MRL" and never plays a video.

Minitube is a Youtube client that works without Flash.

---

### Post by Mark_in_Hollywood on 2009-12-21
The GetDeb server that gave me the .deb has gone bye-bye. It seems the package needed phonon-gstreamer-backend, which Minitube needed but didn't package. Meanwhile that fixed it enough.

---

### Post by kut77less on 2009-12-28
Install phonon-backend-gstreamer, gstreamer-ffmpeg and gstreamer-plugins-bad.


Then 


> sudo ln -s /usr/lib/kde4/plugins/phonon_backend /usr/lib/qt4/plugins/phonon_backend

---

### Post by simpleblue on 2010-02-08
> sudo ln -s /usr/lib/kde4/plugins/phonon_backend /usr/lib/qt4/plugins/phonon_backend 			 		
Worked like a charm for me! :P

---

### Post by Geronimo1067 on 2010-07-23
i tried it.  Now I get the message   "could not open media sourxe"

---

### Post by olygoalie on 2012-06-24
Tried the same thing and get message in terminal that file already exists, but still no sound or video from minitube.  It just cycles through the available videos and give the "missing MRL plugin" message for every one.

---

### Post by howefield on 2012-06-24
Feel free to start a new thread.

Thread closed.

---

