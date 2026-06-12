---
title: "Permanent Keyboard Modifaction"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by xi11 on 2011-03-01
Hello,

I'm new, so hi everyone! I hope I found the right place to ask this question.

I have been following the instructions in this 

[http://art.ubuntuforums.org/showthread.php?p=7462971 ]("http://art.ubuntuforums.org/showthread.php?p=7462971")

thread to **permanentely make the CapsLock key work like a BackSpace key**. 

I set up a .xmodmap file in my home folder as instructed and put the following lines in it 

```
keycode 66 = BackSpace
clear Lock
```The script works fine when I call it with "xmodmap .xmodmap" in the Terminal, however when it is loaded on Ubuntu start up, only the first line seems to be read, that is, I can delete with CapsLock key however I will get capslocked everytime I press the key.

Thank you for any insight you may be able to offer!

xi11

---

### Post by turtle153 on 2011-03-01
You might see it as a quick fix but you can run that command at startup if you want. Go to system > Preferences > Startup Applications and Add a new one. Give it a name and set the command to ```
xmodmap ~/.xmodmap
``` or ```
xmodmap .xmodmap
```
When you login it should automatically run.

---

### Post by xi11 on 2011-03-01
Hello turtle153,

thank your for your suggestion. Sadly, the outcome from above remains unchanged :(

xi11

---

