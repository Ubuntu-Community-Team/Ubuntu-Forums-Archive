---
title: "copy and paste - drag drop folders, need root permission"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by jotto! on 2009-12-04
Just want to copy some folders into another folder owned by root...
Can I type a simple command in the terminal to temporarily give me root permissions to do this or do I need to gain permission and specify exact folder and move etc.

---

### Post by halitech on 2009-12-04
you can do this 2 ways

```
sudo cp /path/to/file/location /path/to/new/location
```
or
```
gksudo nautilus
```

the second will open nautilus as root and allow you to do anything to the system. [color="red"]be VERY careful when using nautilus as root as you can bork your system[/color]

---

### Post by Miljet on 2009-12-04
It is generally not a good idea to be moving files/folders belonging to root. But if you know what you are doing, you can open a terminal and type
```
gksudo nautilus 
```

After you enter your password, it will open the nautilus file browser with root permission. Be sure to close it when you are done.

---

### Post by jotto! on 2009-12-04
Thanks guys!
gksudo nautilus

worked a treat!

---

### Post by dca on 2009-12-04
You can also install from Synaptic *'nautilus-gksu'* which adds a right-click menu add-on to elevate privileges but I don't recommend it because it defeats the purpose of securing the system...

---

