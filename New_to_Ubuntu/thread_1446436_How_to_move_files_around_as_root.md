---
title: "How to move files around as root?"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-04-04
Hi Ya'll,
 Okay I am used to using Linux Mint, which allows me to right click on a folder and open as root, put in my password and drag something into that folder. 
I am using Lucid at the moment. I have dockbarx running and want to drag one of the tar.gz themes into usr/share/dockbarx/themes but I do not know how to open it as root. I think I have to do this in the terminal, but I am not even sure where to begin.
Thanks

---

### Post by Naggobot on 2010-04-04
In Ubuntu Gnome i use

Applications -> Accessories -> Terminal 

And then in the terminal I type

```
gksudo nautilus
```Which gives me file manager with root priviledges

Edit: And be extremely careful with this

---

### Post by abeisgreat on 2010-04-04
Hit Alt+F2 and type 
```

gksudo nautilus

```
This will open up a file browser as root.

Edit: Dangit, I was beaten to it while typing.

---

### Post by byStanderone on 2010-04-04
...drag and drop is supported in karmic, and i suppose lucid supports it,too. you can drop the theme.tar.gz onto a blank space within the theme window...click on system > preferences > appearance select the tab for 'theme'. the system will automatically install that tar.gz that you dropd within the theme window.

---

### Post by AndyP79 on 2010-04-04
Thanks ya'll that worked perfect. nice and simple easy to use. Much apperciation

---

### Post by AndyP79 on 2010-04-04
> **byStanderone said:**
> ...drag and drop is supported in karmic, and i suppose lucid supports it,too. you can drop the theme.tar.gz onto a blank space within the theme window...click on system > preferences > appearance select the tab for 'theme'. the system will automatically install that tar.gz that you dropd within the theme window.

Yes, that does work for themes, but just to clarify, this is for dockbarx, not a theme. it would be nice if dockbarx got an install button. one day, until then, this works.

---

### Post by byStanderone on 2010-04-04
andyp79...got one from you, dockbarx, something to search on..lol

---

### Post by AndyP79 on 2010-04-04
> **byStanderone said:**
> andyp79...got one from you, dockbarx, something to search on..lol

Glad to hear something I asked about was something new for someone to check out. It is a window button bar, kinda like the Windows 7 taskbar feature. It has been around for a moment, find in best in Ubuntu Tweak for no hassels. You might have to activate the source ppa in Ubuntu Tweak first, then add it. Go to your panel,, add to panel, and it is listed just as Dockbarx, no need to add the regular dockbar, they almost look like two different items now.
Good luck

---

### Post by byStanderone on 2010-04-05
...ok, thanks

---

