---
title: "media player closet to windows media player 11"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by termin on 2010-09-19
hi, even though totem is a good player, its missing alot of the features in windows media player. i tried google searching, but got no answer. i also tried mplayer and VLC but none of them came close. 
thanks! closest is spelled wrong, sorry.

---

### Post by dfreer on 2010-09-19
VLC has a ton of features, more so than windows media player 11. I use it on windows 7 as my default player because it just works better. What features are you looking for?

---

### Post by lkjoel on 2010-09-19
> **termin said:**
> hi, even though totem is a good player, its missing alot of the features in windows media player. i tried google searching, but got no answer. i also tried mplayer and VLC but none of them came close. 
thanks!
You can run Windows Media Player 10 under linux.
Open up a Terminal (Applications->Accessories->Terminal/K->Applications->Utilites->Terminal) window and type in:
```
sudo wget http://deb.playonlinux.com/playonlinux_karmic.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux
playonlinux
```
On the window that opens up, click on Install->Search: windows
Windows Media Player should pop up.
Click on it, and click on Apply.
Then follow the instructions.

---

### Post by Cowboybebop79 on 2010-09-19
You don't say what features it is you are looking for but the closest thing to wmp11 on Ubuntu would be Banshee as it has the capability of dealing with video and audio. Audio and video podcasts, radio, last fm, sync to ipod or other player etc etc... the only thing I think isn't perfect is the video options but there is a lot of heat and money going in to its development at the mo so check it out.

---

### Post by termin on 2010-09-19
thanks guys for the quick responses, i just installed windows media like ikejoel said. thanks!

---

