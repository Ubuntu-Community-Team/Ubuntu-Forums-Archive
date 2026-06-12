---
title: "Play on linux"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by shawnic on 2011-07-29
Playonlinux won't run from the application menu and when i run from the terminal I get this:
```
Traceback (most recent call last):
  File "/usr/share/playonlinux/python/mainwindow.py", line 23, in <module>
    import wxversion
ImportError: No module named wxversion

```
I installed WXpython and i still get the same thing.
What am I doing wrong?

---

### Post by ubudog on 2011-07-29
Did you install it from the repos, a ppa, .deb, or what?

---

### Post by shawnic on 2011-07-29
Playonlinux from the software center and wxpython from a tarball.

---

### Post by GWBouge on 2011-07-29
```
sudo apt-get install python-wxversion
```

... or search for wxversion in either Synaptic or the Software Center and install through those.

---

### Post by shawnic on 2011-07-29
```
python-wxversion is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

then what's wrong?

---

### Post by GWBouge on 2011-07-29
Umm ... might be a little beyond me, lol.  Since apt knows it's there, but Python can't find it, I'm going to guess PATH issue?  I'm pretty surprised PlayOnLinux didn't install it automagically when you got that.  Have you tried to purge/reinstall python-wxversion?

---

### Post by shawnic on 2011-07-29
that was the first thing I thought to do.

---

### Post by darkknight85 on 2011-07-29
Hey I had play on linux working grate with Ubuntu10.04 and Elder Scrolls IV: Oblivion. All I did was go to this site [http://www.ubuntugeek.com/howto-install-playonlinux-in-jauntyintrepidhardy.html](http://www.ubuntugeek.com/howto-install-playonlinux-in-jauntyintrepidhardy.html) I copied and pasted the commands and about a half an hour later I installed Oblivion and had lots of fun playing the game. PC version much better then the Xbox360 version

---

