---
title: "Why does this program open in wine?"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by boblettoj99 on 2009-02-01
Ok i recently downloaded the pSX emulator and was trying to make a shortcut on the games menu.
however the program needs 2 commands to start:
killall pulseaudio (for some reason if pulse is running the emulator wont start...)
gksu /home/emud/Desktop/pSX/pSX

im not sure of the right way to do this but i thought i did it right, i made a script called pSX-start with those two commands in it. However when i run it it brings up a window in the taskbar saying "launching wine wind..." and then closes, nothing happens....

It runs perfectly when i type the commands into the terminal so what have i done wrong??

please help!

---

### Post by boblettoj99 on 2009-02-01
aha, i just ran chmod +x pSX-start.sh and it works :D:D:D:D
solved!

---

### Post by damis648 on 2009-02-01
You will want to do open the file and in it at the very top put
```
#!/bin/bash
```
and save and close. Now, open a terminal and:
```
chmod +x /path/to/file
```
and then it should work.

EDIT: Great! Never mind then! :popcorn:

---

