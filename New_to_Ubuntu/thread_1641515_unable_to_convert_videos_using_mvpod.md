---
title: "unable to convert videos using mvpod"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by ankur89 on 2010-12-09
i have been a windows user for all my life and have installed ubuntu 10.10 only a week back. now i'm struggling to find a way to convert videos for my ipod 5g.
mvpod seems to be the best option and appears to work but the converted videos dont play on the ipod.
i ran mvpod on the terminal and it said, warning output file is of avi format.

can this be fixed? if not what do i do to install mvpod, mplayer & mencoder correctly from a fresh ubuntu 10.10 install?

---

### Post by nothingspecial on 2010-12-09
This is going to look really complicated but it`s just a matter of copying and pasting.

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Then install winff or use the example commands at the bottom of the thread.

---

### Post by Jahid65 on 2010-12-09
Or you can use Handbrake. Open terminal & type these command one after one.
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk
```

---

### Post by ankur89 on 2010-12-10
handbrake is just wonderful. thanks a ton. :D

---

