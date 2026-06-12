---
title: "&quot;Run&quot; does not work"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by racie on 2010-11-20
Pressing alt+f2 and clicking "run" from the menu does nothing.  Does anyone have a clue how to fix this?

---

### Post by kerry_s on 2010-11-20
what are you running in the command?

---

### Post by racie on 2010-11-20
> **kerry_s said:**
> what are you running in the command?

Oh sorry.  I meant the box doesn't even appear so I cannot run any commands in it.

---

### Post by lmarmisa on 2010-11-20
Select System -> Preferences -> Keyboard Shortcuts and check if the shortcut for Alt+F2 is defined.

---

### Post by kerry_s on 2010-11-20
> **racie said:**
> Oh sorry.  I meant the box doesn't even appear so I cannot run any commands in it.

are you using gnome-panel?

the run command is tied to the panel. you can setup a separate run command so it doesn't depend on the panel.

my current fav is "gexec". if you want to use alt+f2 you need to disable the original first, just click on it & backspace.

---

### Post by racie on 2010-11-20
> **lmarmisa said:**
> Select System -> Preferences -> Keyboard Shortcuts and check if the shortcut for Alt+F2 is defined.
Yup, it's there.  I haven't really played with keyboard shortcuts.

> **kerry_s said:**
> are you using gnome-panel?

the run command is tied to the panel. you can setup a separate run command so it doesn't depend on the panel.

my current fav is "gexec". if you want to use alt+f2 you need to disable the original first, just click on it & backspace.
Ah ha!  This must be the culprit.  I disabled the panel and replaced it with AWN.  How would I go about making a "separate run command" for it?

---

### Post by kerry_s on 2010-11-20
install gexec from synaptic.
then create the shortcut, see the post above

---

### Post by racie on 2010-11-21
> **kerry_s said:**
> install gexec from synaptic.
then create the shortcut, see the post above

Oh thanks.  Works great. :D

---

