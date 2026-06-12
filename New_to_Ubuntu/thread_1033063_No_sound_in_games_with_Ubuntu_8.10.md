---
title: "No sound in games with Ubuntu 8.10"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by cmsimike on 2009-01-07
Hello all.

I just build up a new computer and everything seems to work well. I get sounds when I play mp3s and through virtual machines, flash, etc. But I get NO sounds at all when trying to play a game like ManiaDrive or My Tribe. I really don't know where to go searching for an answer. I've tried sound preferences but nothing. Help!

---

### Post by linux_tech on 2009-01-07
Open a terminal window and type:

```
sudo apt-get install gnome-alsamixer
```
then type: ```
gnome-alsamixer
```
launch gnome alsamixer then make sure sound is unmuted and that the volume is turned up.

---

### Post by cmsimike on 2009-01-07
the problem, as it turns out, has something to do with having a youtube video up in firefox paused then trying to start a game. if i completely exit out of firefox then the game sounds work.

however i can have the same video open and paused but still play mp3s. will the mixer fix this?

---

### Post by linux_tech on 2009-01-07
probably not, gnome alsa mixer is just a little easier to use 
than alsamixer. 
Try installing alsa-oss
```

sudo apt-get install alsa-oss 
```

---

