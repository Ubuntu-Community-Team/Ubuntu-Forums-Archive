---
title: "Rhythmbox in Jaunty - asking for add'l codecs"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by jazzybob on 2009-07-25
In jaunty, everytime I open Rhythmbox, a message pops up to find codecs (I have installed all the codecs I need and everythinig works great, this is just annoying.  It happens on all the computers I have Ubuntu 9.04 installed on (6) regardless of the playlist.

"The required software to play this file is not installed. You need to install suitable plug-ins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported."

It's looking for a SQL application.  Any ideas?  Known bug or some file I have in the music folder that promts this message???

---

### Post by vinutux on 2009-07-25
i think this is a known bug...just avoid it or using another player like banshee, listen,or exaile.....banshee is best among them...better than rhythmbox (for me)```
sudo apt-get install banshee
```

---

### Post by kostkon on 2009-07-25
Try removing from your music library any files that aren't images or songs. That should fix the codec problem in Rhythmbox.

---

### Post by kellemes on 2009-09-27
Guess this is the relevant bug-report..
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/343707]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/343707")

Not sure what to do, purging folders of non-supported files is just no option since that is a hell of a job and a mediaplayer should be able to handle this itself.

---

