---
title: "path??"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by LinLou on 2009-12-24
Any advice on how i can find the path of a file? I want to turn an .flv to an .mp3 but i have tried the $whereis and $which commands but these seem not to work..

Thanks..

---

### Post by minsf on 2009-12-24
if you want to search your entire system for files that contain "minsf" in their name, you can try:
```
sudo find / -name "*minsf*" >results
```
this should produce a file "results" in the current directory containing all files that were found (+paths).
however, it may take a while to search the entire system.
so if you just want to search subdirectories of your home you can try:
```
find /home/linlou -name "*minsf*" >results
```
of course there are many patterns you can look for, other than name, so take a look at the manpage of find.

---

### Post by LinLou on 2009-12-24
Does this print out the path of e.g. Play.flv ??

---

### Post by 3rdalbum on 2009-12-24
If you can see it in your file browser, you can drag it into the terminal and it will print the file path.

---

### Post by minsf on 2009-12-24
let's make this thread a bit more clear:
1. do you know the location of the Play.flv or are you trying to find it?
2. do you know how to convert flv to mp3? or is it what you are trying to figure out?

---

