---
title: "Some stuff"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by -Root- on 2009-05-13
Hello guys i am an new to linux but looks awesome i am trying to install adobe flash player when i dl it from adobe i get this wrong architecture 'i386'. Any help? Also does anyone have a tutoiral on how to install gfire for pidgin.

---

### Post by lavinog on 2009-05-13
Welcome to Ubuntu.
It's funny that your name is Root, and you are new to linux. (Root is the super user account)

Try installing adobe-flashplugin in synaptic (System>administration>synaptic package manager)
or you can open a terminal and type:
```
sudo apt-get install adobe-flashplugin
```

This is a good place to get some info also:
[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

---

### Post by Apollo87 on 2009-05-13
Heres a nice little gfire tutorial:

[http://ubuntuforums.org/showthread.php?t=226456](http://ubuntuforums.org/showthread.php?t=226456)

---

### Post by presence1960 on 2009-05-13
> **-Root- said:**
> Hello guys i am an new to linux but looks awesome i am trying to install adobe flash player when i dl it from adobe i get this wrong architecture 'i386'. Any help? Also does anyone have a tutoiral on how to install gfire for pidgin.

for 64 bit Flash : [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

worked for me on hardy, Intrepid and now jaunty flawlessly.

P.S. awesome screen name -Root-...very cool!

---

### Post by kevCast on 2009-05-13
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by Mortus Pryde on 2009-05-13
KevCasts is likely the best piece of guidence so far. This will not only install Flash, but Java and a number of restricted codec as well you may find you need. May as well get them all out of the way at once instead of one at a time.

---

### Post by misfitpierce on 2009-05-13
The restricted extras will install 32 bit flash inside the 64 bit architecture using nspluginwrapper automatically setting everything up, you can get a 64 bit version beta I believe also which is simple also, I had lag in 64 bit full screen flash player and its smooth with the restricted extras package that auto set everything up so I'd go 32 bit with nspluginwrapper from the restricted extras auto setup... :)

---

