---
title: "major problems with any audio or video programs"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by rwltrz4 on 2009-01-09
installed banshee, crashes, wont import my mp3 files
installed kino, wont reckonize dv files for dv files and has no options for export, the output selections for export under other are simply not there
installed open movie, wont even open
installed kdenlive, same deal opens and crashes
installed pitivi movie, stops on exports halfway then crashes
vlc will not play movies
mplayer opens and crashes
avidmux, major file errors then crashes (lib-errors?)

this is a new install, only added these programs , I really have a need for multimedia and have a bunch of home movies i need to edit,

oh i also installed all the gstreammer plugins from add/remove

---

### Post by Crafty Kisses on 2009-01-09
Try running the following command:
```
sudo apt-get install ubuntu-restricted-extras
```
I'd also like you to run Banshee in the Terminal and see what errors you get, so just go in the Terminal and run the following:
```
banshee
```

---

### Post by rwltrz4 on 2009-01-09
I am now getting an error saying something was interupted and to: dpkg --configure -a, however when i try i am denied and says i dont have super user status

synaptic,add remove no longer work, says something is/was running and was interupted

---

