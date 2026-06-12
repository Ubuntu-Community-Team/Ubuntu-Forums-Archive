---
title: "make a short cut/launcher using terminal"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by imortalninja161 on 2011-08-12
hay guyz i want to make a short cut for openarea.exe

```
ln -s /tmp/openarena-0.8.1/openarena-deprecated.exe /home/ninjalo161/Desktop
```

i did this and it worked fine and placed the .exe short cut on the desktop but it would not work 

what commands do i use to make that a launcher instead of shortcut because i make that with GUI and it worked fine but for learning purposes i would like to do it from terminal thanks

---

### Post by Ozymandias_117 on 2011-08-12
The easiest way to make a launcher would be to create a text file with the contents of something like this:
```
#!/bin/bash
cd /path/to/folder/with/executable/
./executable
```

Then make it executable with ```
chmod +x launcher
```

Depending slightly on what you're running, you may have to add a little bit more to tell it to run the program through WINE or change /bin/bash to /usr/bin/python if it's a python script etc.

---

### Post by CatKiller on 2011-08-12
A link is not the same as a launcher. A link is essentially the same as a copy. You can create a launcher in any text editor.

Why are you trying to run an .exe file?

---

### Post by imortalninja161 on 2011-08-12
a ok thanks ill try those commands out guys Thanks

i want a launcher for open arena then to lunch it u have to execute the exe then wine takes over.

---

### Post by CatKiller on 2011-08-12
OpenArena is in the repositories, isn't it?

If you want to use a launcher to run a command you'll want to create a .desktop file. Dragging-and-dropping from a menu to the Desktop will let you see the format.

---

