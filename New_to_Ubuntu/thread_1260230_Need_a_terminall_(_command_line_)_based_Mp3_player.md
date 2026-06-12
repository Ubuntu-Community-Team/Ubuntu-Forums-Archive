---
title: "Need a terminall ( command line ) based Mp3 player ( ncurses ? )"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by credobyte on 2009-09-07
So far I've tried mp3blaster and it's too messy for me ( menu is kind a weird and it can be used only from tty's ).
Does anybody know a good, command line / terminal based mp3 player ( no need for playlists, etc. - just browse / select all / play / next-previous ... ) ?

---

### Post by ChrT on 2009-09-07
mplayer

---

### Post by plade on 2009-09-07
> **gunitzpqm said:**
> Ok, this one's solved... I found commands for rhythmbox. Here they are:

rhythmbox-client --previous
rhythmbox-client --play-pause
rhythmbox-client --next

Just make custom panel launchers and put those in the fields of the corresponding buttons to make media controller buttons. You can get some glossy blue buttons here: [http://www.gnome-look.org/CONTENT/content-files/63457-gnome-media-panel-icons.tar.gz](http://www.gnome-look.org/CONTENT/content-files/63457-gnome-media-panel-icons.tar.gz)


I found this solution in another thread : [http://ubuntuforums.org/newreply.php?do=newreply&p=4944830](http://ubuntuforums.org/newreply.php?do=newreply&p=4944830)

:) Hope this helps.

---

### Post by credobyte on 2009-09-07
> **plade said:**
> I found this solution in another thread : [http://ubuntuforums.org/newreply.php?do=newreply&p=4944830](http://ubuntuforums.org/newreply.php?do=newreply&p=4944830)

:) Hope this helps.

I believe there's no way I could see the file list ( eg., #1 song is playing, I need to be able to see what's the #2 and #3, otherwise, Next/Previous would act like shuffle ) ?

---

### Post by pythonscript on 2009-09-07
mocp is a very nice, low resource footprint player. It's in the repositories. 

```
sudo apt-get install mocp
```

---

