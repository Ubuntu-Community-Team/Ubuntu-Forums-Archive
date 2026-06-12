---
title: "Text to speech on demand"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Kangarooo on 2010-12-01
Theres festival but it works only with pidgin plugin festival or with comand line.
Also would be good a programm that for blind peaple helps navigate
But what i want now is on click selected text to be festivaled..
i found in [http://ubuntuforums.org/showthread.php?t=602298](http://ubuntuforums.org/showthread.php?t=602298)
command ```
echo "(SayText \"`xsel -o`\")" | festival
``` witch worked sometimes after installing xsel. also found somewhere that needed is xsel -p not -o in [http://stackoverflow.com/questions/1857287/send-selected-text-to-a-command-line-argument](http://stackoverflow.com/questions/1857287/send-selected-text-to-a-command-line-argument) and also sometimes worked but only in terminal. Then tryd to make keyboard shortcut and Launcher witch didnt worked.. Why?
Maybe better command witch works allways? Also tryd command sleep 1 && that command and still worked only in terminal..
Using ubuntu 10.10

---

### Post by cariboo on 2010-12-01
Have a look at [Orca]("http://live.gnome.org/Orca"), it's installed by default. You also may want to have a look at the [Assistive Technology & Accessibility]("http://ubuntuforums.org/forumdisplay.php?f=145") sub-forum.

---

