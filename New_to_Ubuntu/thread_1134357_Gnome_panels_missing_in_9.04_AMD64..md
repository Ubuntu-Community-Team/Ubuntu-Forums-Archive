---
title: "Gnome panels missing in 9.04 AMD64."
date: 2009-04-23
forum: New to Ubuntu
---

### Post by seattle vic on 2009-04-23
I upgraded to 9.04-64 several weeks ago and have been keeping up with the updates.  When I restarted after the latest, Gnome came up as usual, but there are no panels, and thus no way to launch an application, except for those that I'd moved to the desktop (not many).  I've tried unloading compiz.  I notice that on the log-in screen, there's no longer an option to try another window manager such as xfe.

In any event, I'm stuck.  Anybody else see this?

---

### Post by cariboo on 2009-04-23
If you can get to a console, press Ctrl-Alt-F1 type gnome-panel at the prompt, then press Ctrl-Alt-F7 to get back to the desktop.

---

### Post by seattle vic on 2009-04-23
> **cariboo907 said:**
> If you can get to a console, press Ctrl-Alt-F1 type gnome-panel at the prompt, then press Ctrl-Alt-F7 to get back to the desktop.

That did it.  Turned out it was not installed, which is odd, since I guess it was before.

Anyway, thanks!

---

### Post by evolx10 on 2009-04-25
I am having the same problem, (not using 64 ver though). 
When i jump to the terminal and type 
 
gnome-panel  
--it returns
Cannot open display

im panel less 

--i did just upgrade from 8.04-->8.10-->9.04 , and my prev desktop setup from 8.04  at one time was setup with dual displays, it might be confusing things. maybe?

---

