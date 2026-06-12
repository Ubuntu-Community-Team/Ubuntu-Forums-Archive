---
title: "Need Project ideas"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by navaneethan on 2009-07-12
Hi all,

       I am studying B.tech[IT] ..Final year .Now i ve planned to do my project in opensource

       So i need the problems in open source..I want to explore it..It may possible to create a package

       So i need your help regarding the needs or problems in open source

       If you va any idea regarding that i glad to share with you



   Thanks

---

### Post by nhasian on 2009-07-12
we need a voice dictation program for linux like dragon naturally speaking is for windows.

---

### Post by earthpigg on 2009-07-14
i remembered this thread from 2 days ago, and just had an idea:

are you familiar with top?

```
top
```

are you familiar with htop?

```
sudo apt-get install htop
htop
```

nifty lil app to see what is taking up all your RAM and processor power.

are you familiar with gnome-system-monitor?

right click on panel -> add to panel -> system monitor -> click on it


the problem with gnome system monitor is that it is a resource hog. if you don't believe me: open gnome system monitor -> processes -> sort by % CPU -> observe that gnome system monitor is almost always likely to be somewhere in the top 3.

i believe there is a bit of a gap between lightweight and efficient htop and the super easy graphical resource-hog gnome system monitor.


make a simple and lightweight GTK+ front end for htop that is _not_ a resource hog.

the niche use: Ubuntu, other GNU/Linux, and BSD users that are afraid of the command line and config files, but still want to see/know/monitor where their system resources are going.



this is currently possible with htop, *but that involves the command line.*

this is currently possible with gnome system monitor, *but that is a resource hog thus making it impractical for 24/7 on use to _monitor_ their system.*

this is currently possible with conky, *but that involves manually editing config files.*



i myself would likely not use this package, as the command line and editing config files does not scary.... but there are plenty who would, i'd recommend it to others if i knew of it, and it is not beyond the pale of reason that something like this would be installed by default by Ubuntu in the future.

---

