---
title: "Can't get rid of launched app on desktop"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by texpat on 2009-04-21
I made a launcher on my desktop (right clicked desktop, selected 'create launcher...' etc) so that cairo-clock would start up on login. Now I can't get rid of it anymore.

Even if there is a GUI way of doing this, can someone tell me where this sort of thing is stored, i.e. I suppose there must be some sort of start-desktop config file or so.

Many thanks

Texpat

---

### Post by marshall.robert on 2009-04-21
If you are trying to delete something just right click on it and select delete, or press the delete key after selecting it.

---

### Post by texpat on 2009-04-21
Hmmm... I can't seem to do this. 

I can close the application all right by right clicking the icon on the panel and selecting 'close', but it'll come back on the next login.

Any ideas?

Thanks.

texpat

---

### Post by CatKiller on 2009-04-21
> **texpat said:**
> cairo-clock would start up on login.

System -> Preferences -> Sessions

The files are stored in ~/.config/autostart.

---

### Post by texpat on 2009-04-21
Thanks CatKiller.

System -> Preferences -> Sessions worked fine, but ~/.config/autostart is an empty directory on my machine.

texpat

---

### Post by red_Marvin on 2009-04-21
I don't know a specific answer to this, but I would suggest poking around in the hidden files/directories in your home directory. User specific settings are often stored there.

> Open nautilus file manager.
> Press Ctrl+H

The hidden files/directories are the ones prefixed by a dot.

---

