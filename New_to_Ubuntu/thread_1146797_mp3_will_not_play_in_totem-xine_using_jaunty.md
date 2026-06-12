---
title: "mp3 will not play in totem-xine using jaunty"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by orwellus on 2009-05-02
Hello I'm using Ubuntu Jaunty, and I tried to play an mp3 file today using totem-xine, and got an error message. The error message said something like totem cannot find the plugin to play this file. I thought I had all the various codecs installed, and mp3 files play fine when I use VLC, mplayer, Gnome player, and audacity. Any suggestions?

---

### Post by llamabr on 2009-05-02
would  be more helpful to see the actual error.

run it from the terminal, and post the error and output.

---

### Post by logos34 on 2009-05-03
> sudo apt-get install [COLOR="Red"]libxine1-ffmpeg[/COLOR]

maybe that's missing

---

### Post by orwellus on 2009-05-03
No I have that codec installed, and it is the newest version. 

I'm not sure how to run totem-xine from the terminal. 

The error message I have when I try to play the mp3 file says:

"There is no plugin to handle this movie". 

So maybe totem is trying to play the mp3 file as a dvd? I don't know.

---

### Post by mc4man on 2009-05-03
libxine1-ffmpeg is what handles .mp3's for xine based players.
One possibility is the catalog.cache has been corrupted. (other than an issue with the .mp3 or not restarting totem-xine since installing libxine1-ffmpeg - those seem unlikely

To check, navigate to home folder -> .xine and inside will be a file "catalog.cache. (.xine is a 'hidden' folder

Delete it and restart totem-xine or any other xine player and the file will be rebuilt

---

### Post by orwellus on 2009-05-03
Deleting catalog.cache fixed it. Thank you.

---

