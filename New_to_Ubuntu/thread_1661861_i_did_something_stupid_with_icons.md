---
title: "i did something stupid with icons"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by Arthur Millar on 2011-01-07
hi 
I was installing a new set of icons with terminal to 
/usr/share/icons 
(buuf 1.6)the icon theme was outdated so i wanted to replace it with the new one.
in my haste i typed

pc1@pc1:~S sudo rm  -r buuf /usr/share/icons
which deleted the whole /usr/share/icons folder *smacks himself
i have tried to reinstall the missing icon themes but some of my applications have lost there icons even tho i reinstalled them

what can i do to reset this 
i thought of installing gnome but i dont know
please help

---

### Post by thameera on 2011-01-07
Did you try changing the theme? Or installing a new theme? It will restore the icons I guess.

---

### Post by coffeecat on 2011-01-07
Try booting up from the live CD and copying from the live session /usr/share/icons/ folder whatever is missing from your hard drive install. Take care with /usr/share/icons/default/. It contains a single symlink called index.theme linking to /etc/alternatives/x-cursor-theme which you may have to re-create. I'm not sure it will copy correctly. Also there are the cursor themes but a copy from the live session should fix this.

---

### Post by Arthur Millar on 2011-01-07
> **thameera said:**
> Did you try changing the theme? Or installing a new theme? It will restore the icons I guess.

yeah i tried that but it seems that there are a few programs that store their icons somewhere else 

Brasero
Agave 
Shotwell
AWN
Rythembox
Empathy
screenlets 
Virtualbox 
and a whole lot more (Sh*t)#-o

---

### Post by Arthur Millar on 2011-01-08
> **coffeecat said:**
> Try booting up from the live CD and copying from the live session /usr/share/icons/ folder whatever is missing from your hard drive install. Take care with /usr/share/icons/default/. It contains a single symlink called index.theme linking to /etc/alternatives/x-cursor-theme which you may have to re-create. I'm not sure it will copy correctly. Also there are the cursor themes but a copy from the live session should fix this.

well i managed that but it didn't seem to make any difference 
its a pitty that root has no trash bin cause then i could have restored stuff 
i have reinstalled a whole stack of the programs that missed icons and the icons are all inplace so its probably a file in which these icons are listed.
has to be done manually i guess.
may as well just reinstall my system *sigh probably would be faster

---

### Post by thameera on 2011-01-08
Check the following links. May be of some help.

[http://www.uluga.ubuntuforums.org/showthread.php?t=845210](http://www.uluga.ubuntuforums.org/showthread.php?t=845210)
[https://launchpad.net/ubuntu/+source/human-icon-theme/](https://launchpad.net/ubuntu/+source/human-icon-theme/)

---

