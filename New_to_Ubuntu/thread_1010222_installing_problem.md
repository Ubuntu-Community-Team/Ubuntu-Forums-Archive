---
title: "installing problem"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Nemix on 2008-12-13
im trying to install a game Wolfentien:Enemy Territory and i got a linux version for it, im still new to Linux and Ubuntu and not sure how to install it. I went to properties and set the permission to allow executing file as program. when i click on it and a box says comes up and i select run. 
i try installing and then i get an error:
error while loading shared libraries: Libgtk-1.2.so.0: cannot open shared object file: no such file or directory
The setup program seems to have failed on x86/glibc-2.1

i just got ubuntu up last night and haven't installed anything beside the up dates and gfx driver. Thanks in advance for any help =D

---

### Post by Daveth on 2008-12-13
this

[http://gaming.gwos.org/doku.php/guides:32bit:et_wolfenstein#enemy_territory_wolfenstein](http://gaming.gwos.org/doku.php/guides:32bit:et_wolfenstein#enemy_territory_wolfenstein)

points out where you get the missing library files that give you that 1st error. Following the rest of the guide should sail you through.

---

### Post by Nemix on 2008-12-13
no one ??
i really need help :confused:

oh lol must of posted while i was typing, ill check it out ty =P

---

### Post by Nemix on 2008-12-13
i got the same error again it looks like i need Libgtk-1.2.so.0 any idea where i could get that?

---

### Post by Daveth on 2008-12-14
try

```
sudo apt-get install libgtk1.2
```

in a terminal (under the accessories tab), enter your password, and it should install that file. Then try your game.

---

