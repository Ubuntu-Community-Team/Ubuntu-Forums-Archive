---
title: "Panel Problem"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by ThrashInvasion on 2009-09-14
Hey,i was customizing,in the Main menu tab when i saw the left area turning grey.
I closed the window and i noticed that  in the application tab,was absolutely nothing!
I closed my pc and when i was writing my user name,and i saw a weird font.
now the panel is only the half shown and all the texts can be hardly read.
i took a shot with the keyboard shortcut,but it isn't what i really see.
Please i need your help

---

### Post by NightwishFan on 2009-09-14
Go to System -> Preferences -> Appearance, and go to the Desktop Effects tab. Set effects to none. Does this fix your problem?

---

### Post by ThrashInvasion on 2009-09-14
well i restarted my pc and it came back to normal,except that there is nothing under application tab and i can't open Main menu in preferences.

---

### Post by NightwishFan on 2009-09-14
So the main menu is blank? Try removing it, and re-adding it. It is called custom menu I believe.

If all else fails reset your panel configuration. I think this command should do it. (In terminal)
```
gconftool --recursive-unset /apps/panel
```

---

### Post by ThrashInvasion on 2009-09-14
stil..i put the command on the terminal and the shuted it down.Nothing under application tab and main menu does not show up...

---

### Post by NoaHall on 2009-09-14
try - 
```
/etc/init.d/gdm force-reload
```

---

### Post by ThrashInvasion on 2009-09-14
* Stopping GNOME Display Manager...                                     [ OK ] 
 * Starting GNOME Display Manager...                                     [fail]

thats what i got...

---

### Post by NoaHall on 2009-09-14
Try - 
```
 /etc/gdm/failsafeXinit 
```

---

### Post by ThrashInvasion on 2009-09-14
what should i press?

---

### Post by NoaHall on 2009-09-14
Erm, fail safe graphics (or something along that lines) or maybe it's called "low graphics mode"

---

### Post by ThrashInvasion on 2009-09-14
nothing..THIS SUCKS...none else had the same problem?

---

### Post by NoaHall on 2009-09-14
Well, you could try reinstalling it, but I'll only tell you how if you promise not to be mad at me if it doesn't work xD

---

### Post by ThrashInvasion on 2009-09-14
i promise :p (took me while to think about it)

---

### Post by NoaHall on 2009-09-14
Haha.


ctrl + alt + F1

sudo apt-get remove gdm

sudo apt-get install gdm

---

### Post by ThrashInvasion on 2009-09-15
well now,when i turn on my pc, it directs me to a black screen(terminal like).
I put my username and pass and then does nothing..i can only run comand as in terminal.I runned the command 'sudo apt-get install gdm' but it comes up with an error..

---

### Post by ThrashInvasion on 2009-09-15
should i re install ubuntu? Please prove me wrong..

---

### Post by ThrashInvasion on 2009-09-15
i runned startx and signed in..What should i do?

---

### Post by ThrashInvasion on 2009-09-15
ok back to the first problem..When i click applications tab there is nothing under it..

BTW thanks for helping me..132 views but only few  tried..

---

### Post by ThrashInvasion on 2009-09-15
solved thanks to this 
[http://ubuntuforums.org/showthread.php?p=7783930:lolflag::P](http://ubuntuforums.org/showthread.php?p=7783930:lolflag::P)

---

