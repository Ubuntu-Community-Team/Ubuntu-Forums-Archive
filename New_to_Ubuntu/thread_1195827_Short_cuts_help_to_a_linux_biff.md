---
title: "Short cuts help to a linux biff"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by onespeed on 2009-06-24
Hello all.
Got fed up with vista crashing every other boot and staring at the boot screen, thought I'd give Ubuntu a go.
Its GOOD!

Up and running and my only problems are a lack of knowledge.

At the moment, i can't figure out how to set up an old style dos batch command, like startmyprogram.bat

How do I set up a short cut in linux to start wow with wine? At the moment, I'm opening a terminal and typing 

wine "home/onespeed/world of warcraft/wow.exe" -opengl

every time I want to join in the Ubergeekfest that is wow. Its getting a little annoying!

Thanks in Advance!:P

---

### Post by kpkeerthi on 2009-06-24
Right-click Applications on the top panel, choose Edit menus. It should be easy going from there on.

---

### Post by onespeed on 2009-06-24
Love it! 

Thanks for that.:D

---

### Post by Cheesemill on 2009-06-24
The equivalent of DOS batch files are shell scripts.
You can open a text editor and type:
```
#!/bin/bash
wine "/home/onespeed/world of warcraft/wow.exe" -opengl
```
Save it as whatever you wish, ie /home/onespeed/wow.sh
Unlike DOS the file extension doesn't matter (I've just used .sh for clarity), we set a file as being executable by doing:
```
chmod +x /home/onespeed/wow.sh
```
You can now run your batch script by either typing the full path:
```
 /home/onespeed/wow.sh
```
or if you are already in your home directory you can simply do
```
 ./wow.sh
```

---

