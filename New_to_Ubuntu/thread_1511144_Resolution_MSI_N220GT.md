---
title: "Resolution MSI N220GT"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by Piripe on 2010-06-16
Hi, im from chile, and starting with linux, on ubuntu 10.04
i got a graphic card of the model MSI N220GT, running with nvidia drivers, that ubuntu get me, my screen is a LG Flatron L194wt-bf 19'', i have seen some helps that says "use ctrl+alt+f1 and this comands", the first time, i press ctrl+alt+f1, and dont have any idea of how to come back, now i know that is with ctrl+alt+f7, and get stucked on terminal1. Also i was unable to introduce any comand, the screen, says "username-desktop login:", so a introduce my username and pasword, but oh. it says wrong pasword, so i introduce my pasword 2 times, and same again, i introduce my nick, same, and so on. as you can probably realice this is my first time with linux, also i try with etc/x11/xorg.conf but i was unable to change it, as i was no root, and cannot active the root, again, without using comands. so i guess i need a little tutorial from 0 to how to use terminals on ubuntu 10.04

edit: (problem with video card: can't get 1440*900)

Edit 2: Problem Solved at [http://ubuntuforums.org/showthread.php?t=1512084](http://ubuntuforums.org/showthread.php?t=1512084)

---

### Post by cariboo on 2010-06-16
To log in from a prompt you need to use the same user name and password as you do to log in to your desktop. You shouldn't need to edit /etc/X11/xorg.conf. If you want to change the monitor resolution, press alt-F2 and type:

```
gksu nvidia-settings
```

The above command will run nvidia-settings as root, allowing you to change the resolution and save the changes.

---

### Post by Piripe on 2010-06-16
indeed, it work to change the resolution, but the trouble is that nvidia does not give me the option of 1440*900, and the monitor is show as unknown

---

