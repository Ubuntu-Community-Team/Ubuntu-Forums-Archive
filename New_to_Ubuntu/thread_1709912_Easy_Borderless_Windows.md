---
title: "Easy Borderless Windows?"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by Jedcurtis on 2011-03-19
Hi all, and thanks for the help.
Just wondering if there is an easy way to set up the terminal to not have borders.  I've done some searching and no luck.  I'm using Gnome, compiz, the elementary borderless theme on Ubuntu 10.10, Maverick Meerkat. (gtk window decorator)

Jed

---

### Post by HermanAB on 2011-03-19
Well, the easy way is to stop the windows manager gdm.  Then you won't have any borders at all.

---

### Post by BrandonC19 on 2011-03-19
Hi there. The only "easy" way that Iknow of (or can find, for that matter) is to install Screenlets [sudo apt-get install screenlets] and open a "Terminal" Screenlet. You would then right-click on the Terminal screenlet and go to Properties >> Options and configure it. Here's a screenie of my borderless terminal screenlet. [http://i279.photobucket.com/albums/kk140/BassistBoy17/Screenshot3.png](http://i279.photobucket.com/albums/kk140/BassistBoy17/Screenshot3.png)

---

### Post by chrinabuntu on 2011-03-19
FYI, your screenshot doesn't work. 

> **BrandonC19 said:**
> Hi there. The only "easy" way that Iknow of (or can find, for that matter) is to install Screenlets [sudo apt-get install screenlets] and open a "Terminal" Screenlet. You would then right-click on the Terminal screenlet and go to Properties >> Options and configure it. Here's a screenie of my borderless terminal screenlet. [http://i279.photobucket.com/albums/kk140/BassistBoy17/Screenshot3.png](http://i279.photobucket.com/albums/kk140/BassistBoy17/Screenshot3.png)

---

### Post by stinkeye on 2011-03-19
> **Jedcurtis said:**
> Hi all, and thanks for the help.
Just wondering if there is an easy way to set up the terminal to not have borders.  I've done some searching and no luck.  I'm using Gnome, compiz, the elementary borderless theme on Ubuntu 10.10, Maverick Meerkat. (gtk window decorator)

Jed
In ccsm > effects > window decoration 
Change **Decoration windows** to...
```
(any) & !(class=Gnome-terminal)
```

---

### Post by mcduck on 2011-03-19
> **HermanAB said:**
> Well, the easy way is to stop the windows manager gdm.  Then you won't have any borders at all.

That would work, although GDM is not a widnow manager, so it has has nothing to do with drawing of windows ... ;) But yes, stopping it would indeed remove windo borders. And all windows & running graphical applications as well... :D

If you use Gnome desktop, your window manager is either Metacity or Compiz.

Anyway, stinkeye provided the best solution, allowing you to remove borders from whatever program/widnow you choose without messing with anything else on the system.

---

### Post by BrandonC19 on 2011-03-19
> **chrinabuntu said:**
> FYI, your screenshot doesn't work.

It works just fine for me.

---

### Post by Jedcurtis on 2011-03-20
Thanks everyone! Nice screenshot Brandon! Cool looking desktop.  It is working!  Doesn't Ubuntu rock?  Again, thanks all...

Jed

---

### Post by mikee55 on 2011-03-20
Didn't work for me:(

Mike

---

