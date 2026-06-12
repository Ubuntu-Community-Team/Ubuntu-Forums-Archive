---
title: "compiz - any way to hide the mouse?"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2009-04-11
So since flash in fullscreen sucks so much for linux, I've basically just used compiz to zoom in on the video instead and that's worked fine for the last few years.  

But I'm getting sick of the mouse being there.  Is there any way or command to make the mouse disappear?

---

### Post by UbuntuNerd on 2009-04-16
Try Unclutter: it hides the mouse in X after a period of inactivity it runs permanently in the background of an X session. It checks on the X mouse pointer position every few seconds, and when it finds it has not moved (and no buttons are pressed on the mouse, and the cursor is not in the root window) it hides the mouse cursor. It restores the mouse cursor when the mouse is moved or when a mouse button is hit. 
```
apt-get install unclutter
```

also check this link: [http://ubuntu-tutorials.com/2008/07/07/auto-hide-your-mouse-pointer-when-idle-with-unclutter/](http://ubuntu-tutorials.com/2008/07/07/auto-hide-your-mouse-pointer-when-idle-with-unclutter/)

---

### Post by CryptiniteDemon on 2009-04-29
Thanks a lot.  That's perfect.

---

