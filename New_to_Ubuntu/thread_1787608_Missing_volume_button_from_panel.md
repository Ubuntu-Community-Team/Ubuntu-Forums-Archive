---
title: "Missing volume button from panel"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by chitragurung on 2011-06-21
I lost volume adjustment button from panel. when I try to adjust from key board, it does not work. I can not adjust volume. How to fix it ?

I have been using ubuntu 10.04 at dell mini 10

---

### Post by pqwoerituytrueiwoq on 2011-06-21
did you accidental remove it?
if so right click the panel
add to panel
indicator applet

did it not not appear when you logged in?
[alt]+[f2]
killall gnome-panel
run

---

### Post by disabled20191128 on 2011-06-21
Hello, you could try resetting your panels

gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
gnome-panel &


hope this helps

---

### Post by chitragurung on 2011-06-22
I do not know how I disabled this. But I try to add from click panel or sound I got error message as follows 
 
 
[http://postimage.org/image/2ocfws9d0/](http://postimage.org/image/2ocfws9d0/)

---

### Post by dcsoldschool53 on 2011-06-22
In Synaptic package manager type in```
alsa
```look for```
alsa-utils
``` to see if it is installed, and maybe```
alsa-base
``` too. I am not sure if you need to have alsa-base installed.

---

### Post by vivek.pandey on 2011-06-23
system->preferences->sound right click add to panel... is this too not working? i guess this is a really simple way

---

### Post by BeeDee on 2011-06-23
CHeck this thread: [http://ubuntuforums.org/showthread.php?t=1333661&highlight=gnome+volume+applet](http://ubuntuforums.org/showthread.php?t=1333661&highlight=gnome+volume+applet)

---

### Post by chitragurung on 2011-06-24
I did try all methods as advised but nothing happened.

---

