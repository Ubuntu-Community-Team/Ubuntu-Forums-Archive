---
title: "force quit keyboard shortcut?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-23
is there one or a way to assign one?  it's cool that i can use the force quit icon in the panel but what if the mouse freezes which occasionaly happens and i have to restart the entire computer

---

### Post by DGortze380 on 2009-01-23
> **mamamia88 said:**
> is there one or a way to assign one?  it's cool that i can use the force quit icon in the panel but what if the mouse freezes which occasionaly happens and i have to restart the entire computer

ctrl+alt+bckspace

will restart X. that's generally enough, in two years I've only frozen up once so bad that didn't even work.

---

### Post by mamamia88 on 2009-01-23
thanks that should work just fine

---

### Post by yeats on 2009-01-23
You can also open a terminal and do either:

```
top
```

to see the programs running the most resources (often "frozen" programs fall into this category) or

```
ps ax | grep *program name*
```

where "program name" is the program you'd like to kill

Either way, there is a process id (pid) that is listed to the left of the process name and you can press k in top and then type the pid or you can:

```
kill *pid*
```

where pid is the process id number.  If the program is really nasty, you can do 

```
kill -9 *pid*
```

to kill it completely dead, but that should be a last resort.  It's also a good idea to use "kill" with caution - it's always better to shut down normally.

---

### Post by mrsudo on 2009-01-24
clicking the 'X' in the window decoration will usually bring up a prompt to kill the unresponsive window.

ctrl+alt+bckspace also works too :) but this will kill x along with all open graphical apps

---

### Post by mrsudo on 2009-01-24
sorry, didnt really catch the 'no mouse' part the first time.  you could always navigate into your menu (default is ctrl+f1 im pretty sure)  and shutdown through the menu if your keyboard still works.

---

### Post by dnRoyston on 2009-01-24
Or press CTRL+ALT+Escape for xkill
EDIT: 'Just tried it, it didn't work. Maybe it's for Xfce?

---

### Post by Michael.Godawski on 2009-01-24
hi,

[http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)

This tool let's you customize every possible command to a shortcut.
Some tweaking required but it works quite well.

---

