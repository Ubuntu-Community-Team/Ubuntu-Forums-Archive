---
title: "Sound stops working after being on for 10 hours"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by MillionFlame on 2009-10-26
hey everybody sorry if this topic has been done before but ive done searches and found nothing lol.

any way just as the topic suggests every time i leave my machine longer than 10 hours or so the sound shoots out and i need a reboot. not only that, any program that uses sound tends to not work. mplayer freezes up
and streaming vids tends to act funny.

accually oddly i switched to kde gui(only cause i wanted a nicer looking interface not cause i thought it would solve the problem), and it made the problem weirder. not worse just odd. flash vids used to work accually before getting kubuntu. now they just play for 3 seconds and stop when the issue comes up.


usually a reboot solves the problem again for another series of hours. its no HUGE issue but when im downloading large files and need a reboot to use it tends to become a pain lol 

any suggestions?

---

### Post by ScarySquirrel on 2010-04-23
Welcome to Ubuntu. 
Check out this post: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1460560](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1460560). 

Do you still have this problem? 

What are your computer's specs?

---

### Post by Vistz on 2010-04-24
```
sudo alsa force-reload
```

---

### Post by lidex on 2010-04-24
You may want to try disabling power-saving in alsa-base.conf
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Find the line that looks something like this:
```
options snd-hda-intel power_save=10 power_save_controller=N
```
Now comment it out (place a # in front of it) or delete it. Save. Close. You'll need a reboot or alsa reload to see if it works.

---

