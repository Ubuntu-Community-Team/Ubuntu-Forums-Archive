---
title: "annoying splash screen at startup"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by libihero on 2009-12-11
i downloaded "xscreensavers", and i love the screensaver im using.
the only problem is every time i start up my computer, there is this annoying splash that says "xscreensavers" and all this other stuff.  is there any way to get rid of that?

---

### Post by joes7 on 2009-12-11
Right click and select Desktop Settings. Select "Splash" and select "None".

---

### Post by libihero on 2009-12-12
right click where? im on ubuntu, when i right click i dont see desktop settings anywhere

---

### Post by bacardiandwatermelon on 2009-12-12
this may help..

[http://www.linuxforums.org/forum/linux-desktop-x-windows/38731-how-do-i-stop-xscreensaver-splash-displaying-after-starting-x.html](http://www.linuxforums.org/forum/linux-desktop-x-windows/38731-how-do-i-stop-xscreensaver-splash-displaying-after-starting-x.html)

or this..

[http://www.jwz.org/xscreensaver/man1.html](http://www.jwz.org/xscreensaver/man1.html)

---

### Post by 73ckn797 on 2009-12-12
Try startupmanager from Synaptic and see if switching off the splash will do the trick.

---

### Post by MooPi on 2009-12-12
I imagine it depends on what system you are using. My Openbox system I had to append the autostart script.>  xsceensaver --nosplash. It's been a while since I've used xscreensaver and it may have been >  xscreensaver -nosplash

---

### Post by libihero on 2009-12-12
thanks! i found it in the .xscreensaver file and changed "splash=true" to "splash=false"

---

