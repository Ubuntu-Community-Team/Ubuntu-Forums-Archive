---
title: "Nvidia drivers acting strange on laptop"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by Miles Paulson on 2010-01-19
Hello, ive been running ubuntu for a while on my laptop but im still a greenhorn noob when it comes to linux, but i learn something new everyday. Let me tell you about my problem im having. When i first installed ubuntu on my laptop i installed the 64bit of 8.10, i have since upgraded to 9.10 64bit. Since day one with the nvidia drivers everytime i drop into a console (alt+f2) or initiate a shutdown/restart i get a extremely slow refresh rate and blue specs all over the screen. its not bad enough that i cant work, its just really annoying. Now ive tried alot of different versions of the nvidia driver, and am currently running the most current version 190.42. I have a HP DV9268NR, it has a gforce go 7150m graphics card, 4 gigs of ram, 2 320 gig hdd. I have other questions for everyone, but i will leave those to other posts.

---

### Post by cariboo on 2010-01-20
Open a terminal and type:

```
sudo nvidia-xconfig
```

the above command will create a new /etc/X11/xorg.conf, that may solve your problem.

---

### Post by Miles Paulson on 2010-01-20
Sorry to say that didnt work. Its still doing it when i drop to the console. Its only doing it after the nvidia drivers are loaded, because durring the initial boot before the nvidia logo pops up there isnt a problem, once your in gnome its not a problem either unless you need to drop to console. Its been doing this since day one, and im starting to just get used to it, although i would like to just get it fixed. Anyone else have any ideas?

---

### Post by Miles Paulson on 2010-01-20
Bump

---

### Post by Miles Paulson on 2010-01-22
Nobody has any more ideas?

---

### Post by Miles Paulson on 2010-01-22
Beuler.... Beuler... I find it hard to believe nobody else has any ideas.

---

