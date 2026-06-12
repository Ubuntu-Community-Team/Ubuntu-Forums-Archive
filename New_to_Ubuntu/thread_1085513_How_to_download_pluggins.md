---
title: "How to download pluggins"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by msidhard on 2009-03-03
How to download pluggins for totem movie player . And i cannot get sound for 3gp format in vlc

---

### Post by x33a on 2009-03-03
```
sudo aptitude install totem-plugins
```

---

### Post by obaid on 2009-03-03
i think when you try to play something whose codecs is not present in Mplayer, it will automatically ask you to download the codec.

---

### Post by msidhard on 2009-03-03
Yes yes but i need that gui window without putting the song file .

---

### Post by Cresho on 2009-03-03
I thought totem runs on gstreamer.

open up your software sources and put it in main instead of the states.  then in terminal you do a "sudo apt-get update"  Then you open up your add and remove program and search for gstreamer and install..its like 7 of them.

---

