---
title: "Totem Replacement"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Red Rebel on 2008-12-05
Is there a way to remove Totem and install a better video player? 

Totem has been giving me trouble. I have installed all of the codecs it has asked me to install. When I play a video it plays, but if i click on the screen, black blocks form on the screen obstructing the video, or the video goes out completely. I am looking for something much better, and that may already have the codecs for most popular video formats. Any help in this regard would be greatly appreciated.

---

### Post by taurus on 2008-12-05
```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by Red Rebel on 2008-12-05
Just installed it and like it. Is there a way to make it my default movie player now?

thanks again...

---

### Post by tjwoosta on 2008-12-05
vlc is good

or there is mplayer, which i think is equally as good if not better

---

### Post by miniyak on 2008-12-05
good question, how do you make vlc the default player for videos? (under preferred applications there is only a option for music in hardy) more importantly is there a plug in for it to replace flash in firefox and if so how do you implement it?

---

### Post by bryncoles on 2008-12-05
good choice on vlc. i use it for all my files, and i like gxine for dvds. 

to set as a default player, open a folder (any folder will do) and click edit->preferences->media. 

you can set all sorts of global defaults from here. 

you can also play with control centre, preferred applications. finally, you can try just right clicking a file and selecting 'open with' and then choosing vlc from that menu. vlc will then become the default application for that file type.

---

### Post by Dr Small on 2008-12-05
+4 for VLC

---

### Post by Titan8990 on 2008-12-05
+5 for VLC, use it on all OSes.

---

### Post by philinux on 2008-12-05
Intrepid:

System>prefs>preferred app>multimedia> custom
use
/usr/bin/vlc

---

### Post by mc4man on 2008-12-05
> just installed it and like it. Is there a way to make it my default movie player now?

For 8.10

Open nautilus (or home folder) and in upper panel -> edit -> preferences -> media.

You'll see all the currently available choices.
If something you want isn't there go 'open with other application' (or something to that effect, not using 8.10 atm.

For 8.04
Several ways, easiest method for vlc is this (for other apps see link at bottom of post (use vlc %f instead of vlc %m

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by philinux on 2008-12-05
I must admit though I've removed totem-gstreamer and installed totem-xine.

i was getting stuttering in vlc but now really smooth with xine backend for totem.

Totem now has access to the dvd menu system too.

---

