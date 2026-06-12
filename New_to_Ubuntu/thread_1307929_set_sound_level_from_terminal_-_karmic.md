---
title: "set sound level from terminal - karmic"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Flynsarmy on 2009-10-31
In jaunty and earlier you could set the volume level (and unmute) with the following command
```
amixer set 'Master' 95% unmute > /dev/null
```

however this no longer works in karmic. I figured out to unmute you can go:
```
amixer set 'Master' 75% unmute
amixer set 'Headphone' 75% unmute
amixer set 'Speaker' 75% unmute
```
This unmutes but doesn't set the speaker volume to 75%...Is there something i'm missing here? How do I set volume to a specific % from the terminal in karmic?

To mute my laptop i used the media key on the front (Dell Inspiron 1520). In Karmic this is different from a simple
```
amixer set 'Master' mute > /dev/null
```

---

### Post by Liolikas on 2009-10-31
alsamixer then move bars with arrows ok or you want command for script?

---

### Post by Flynsarmy on 2009-10-31
It's for a script.

---

### Post by Liolikas on 2009-10-31
Now set is separated into cset and sset as I understand. Depending on what you want to do.
amixer -h for info.

---

### Post by Flynsarmy on 2009-10-31
Yes i've read the man page for amixer and fiddled with commands for a while but couldn't find a simple way to unmute my PC and set to a specific volume. It'd be great if you could do it in a single command like in all previous versions of ubuntu but not essential. As i've said I got unmuting working...just need to set to a specific volume now

---

### Post by Liolikas on 2009-10-31
You can join commands with && it will be just longer you can shorten them in .bashrc with alias. Simply if you looked over man and do not find what you want so there is no what you want. Maybe add this as bug.

---

### Post by Flynsarmy on 2009-11-01
bump. Anyone know how to do this? Is it even possible in Karmic?

---

### Post by Flynsarmy on 2009-11-04
Upon further experimenting I discovered just setting a really high value works. On previous kernels, dell inspiron 1520's had an audio issue where you had to set the volume to 70% to get 0% volume, 80% to get 33% volume, 90% for 66% and 100 for 100... It would appear in the latest kernel the 'fix' for this was to simply fix up the ratios however this broke the terminal method of setting the volume - essentially reversing the way it used to be between GUI volume and amixer.

---

