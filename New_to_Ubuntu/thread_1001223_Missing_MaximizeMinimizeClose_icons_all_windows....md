---
title: "Missing Maximize/Minimize/Close icons all windows..."
date: 2008-12-03
forum: New to Ubuntu
---

### Post by trooperchix on 2008-12-03
I noticed that my maximize / minimize / close icons/buttons are gone.  No idea why.  Any ideas?

---

### Post by nhasian on 2008-12-03
see if this command will fix it:

```
metacity --replace
```

---

### Post by m_duck on 2008-12-03
Failing that, press alt F2 and type```
gconf-editor
```Navigate to Apps -> Metacity -> General, and check in the pane on the right hand side the option "button_layout". Its value should be```
menu:minimize,maximize,close
```to be the same as standard.

---

### Post by trooperchix on 2008-12-03
> **nhasian said:**
> see if this command will fix it:

```
metacity --replace
```

This works until I close the terminal, then it all disappears again..

> 
m_duck  	
Re: Missing Maximize/Minimize/Close icons all windows...
Failing that, press alt F2 and type
Code:

gconf-editor

Navigate to Apps -> Metacity -> General, and check in the pane on the right hand side the option "button_layout". Its value should be
Code:

menu:minimize,maximize,close

to be the same as standard.


The values match.  Any other ideas?

---

### Post by trooperchix on 2008-12-03
At this juncture, I did a clean reinstall of Intrepid and all is happy in Ibexland again.  I will leave this thread open though, because I know I'm not the only one who ran into this same issue...

---

### Post by perlluver on 2008-12-03
The real way to fix this is: press Alt+F2 then type this in the box ```
gtk-window-decorator --replace
``` that will leave compiz alone, and bring back the title bar.

---

### Post by newbie02 on 2009-01-04
I posted the solution that worked for me here

[http://ubuntuforums.org/showthread.php?t=833582&highlight=no+minimize+maximize+OR+close+icons+in+upper+right&page=4](http://ubuntuforums.org/showthread.php?t=833582&highlight=no+minimize+maximize+OR+close+icons+in+upper+right&page=4)

Regards
Newbie02

---

