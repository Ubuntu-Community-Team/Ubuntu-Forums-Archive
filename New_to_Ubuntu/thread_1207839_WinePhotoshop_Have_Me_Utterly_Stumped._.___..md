---
title: "Wine/Photoshop Have Me Utterly Stumped. .___."
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-07-08
I tried installing Photoshop this morning on my computer, but forgot to click "Finish" before I restarted my computer (just...don't ask... ><).  This screwed up the install, so that Photoshop won't work.  I tried to uninstall then reinstall it, but I kept getting a message that says that the uninstall was interrupted before it could finish and that nothing was changed.  So I searched out all of the Photoshop files by hand and, using "gksudo nautilus" shift+deleted them.  That still didn't get rid of the PS icon and issues, even after restarting, so I then uninstalled the Wine emulator (since I only installed it for PS).  Well, uninstall was "successful" but Wine is still an available option under Applications.  I open my terminal and type "sudo apt-get remove wine" and, to my dismay, my terminal tells me that it doesn't exist, so it wasn't removed.  Okay.  So I then search my drives for "Wine" and again use "gksudo nautilus" to shift+delete them into oblivion.  BUT WINE AND PHOTOSHOP ARE STILL UNDER APPLICATIONS.  I don't know how to get rid of them!!!  I'm fresh out of ideas.  What am I doing wrong?

---

### Post by wojox on 2009-07-08
In the terminal try

```
apt-get --purge remove wine
```

And then do photoshop

---

### Post by Wataru8675 on 2009-07-08
> **wojox said:**
> In the terminal try

```
apt-get --purge remove wine
```And then do photoshop

For Wine it says it's not installed and thus couldn't be removed.

For Photoshop, it says it couldn't find the package.

They are both, however, still under Applications.  But after my "gksudo nautilus" maneuvers, Wine's icon is a plain file folder and Photoshop's icon is the glass of wine...  I'm not sure if that has any significance or tells you about any sort of progress, but...  Here, I'll just upload a screencap quick.

---

### Post by wojox on 2009-07-08
Go into Applications > Add/Remove 
and search for them in there.

---

### Post by Wataru8675 on 2009-07-08
> **wojox said:**
> Go into Applications > Add/Remove 
and search for them in there.

I've done this already.  Wine has been unchecked and uninstalled.  It is currently not checked.

---

### Post by wojox on 2009-07-08
Oh

Right click Applications and choose Edit Menus.

---

### Post by Wataru8675 on 2009-07-08
> **wojox said:**
> Oh

Right click Applications and choose Edit Menus.

...it really was that easy. ><;
Thank you much wojox. -_-;

---

### Post by Sealbhach on 2009-07-08
Try Playonlinux for installing stuff on Wine. It handles a lot of the gnarly stuff for you.

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

.

---

### Post by mattbutsko on 2009-07-08
You could try GimpShop.

it's a modified version of gimp made in the layout of photoshop. I haven't personally tried it but it's made for linux so you know it'll work, plus they say you can follow most photoshop tutorials in gimpshop without any confusion because it changes terminology and menu layouts to perfectly replicate photoshop.

---

