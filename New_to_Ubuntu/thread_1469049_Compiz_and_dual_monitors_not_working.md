---
title: "Compiz and dual monitors not working"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by cjnkns on 2010-05-01
Hey all - 

I am running Ubuntu 10.04 and having issues with dual monitors.
When I use Metacity dual monitors are fine but, when I try to use compiz I can't drag my windows to the second screen.

I did the 'sudo nvidia-settings' and it is still set to twin view so that should be good...

Another interesting thing is if I am using Metacity everytime I reboot my title bars are gone. I have to go to Visual Effects and select normal or something to get them to appear again.

Does anyone know of a fix for this?

---

### Post by madjr on 2010-05-01
maybe you could use basic metacity effects rather than compiz, till you find a better solution

---

### Post by GSF1200S on 2010-05-01
> **cjnkns said:**
> Hey all - 

I am running Ubuntu 10.04 and having issues with dual monitors.
When I use Metacity dual monitors are fine but, when I try to use compiz I can't drag my windows to the second screen.

I did the 'sudo nvidia-settings' and it is still set to twin view so that should be good...

Another interesting thing is if I am using Metacity everytime I reboot my title bars are gone. I have to go to Visual Effects and select normal or something to get them to appear again.

Does anyone know of a fix for this?

It works fine for me (Compiz+dual-screens+9800GTX+), but then Im using seperate X sessions so I cant drag between screens even if I wanted to (I prefer screens to be seperate). What happens when you drag a window to the edge of a screen (flips the cube, initiates some action)? 

I dont know why your titlebars are disappearing on boot, but I can tell you a dirty hack to fix it (its how I start compiz with XFCE). Create a file in home called compiz.sh and place the following text in it:
```
#!/bin/bash
sleep 2
compiz --replace
```
save the file, make it executable (right click>properties>permissions>Allow file to run as a program), and add the file in System>Administration>Startup Programs. It should run when gnome starts, and you should at least have titlebars.

---

