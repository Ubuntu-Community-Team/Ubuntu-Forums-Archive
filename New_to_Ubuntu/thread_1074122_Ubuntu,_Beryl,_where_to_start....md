---
title: "Ubuntu, Beryl, where to start..."
date: 2009-02-18
forum: New to Ubuntu
---

### Post by Stevo0687 on 2009-02-18
Hey all!

I used to run Ubuntu, then tried Mint, both with a triple-boot XP Pro/Vista Business/Linux.  I ran out of HDD space and had to got down to just Vista (needed something that was compatible with my software for school).  Anyway, I've got the space again (bought an external drive) and want to install Linux again.  

So I've got a few questions. I've seen some awesome videos of Ubuntu Beryl.  What exactly is Beryl?  
It seems to be behind the GUI of the OS, but I'm not exactly sure what it is.  

Will the latest Ubuntu come with Beryl or will I have to install or enable it?

How do I know if my laptop can handle the graphics. My laptop normally doesn't handle things that require a good graphics card. Here are my specs:
Dell Inspiron E1405
Intel Centrino Duo T2300 @ 1.66 GHz
Over 3GB RAM 
Integrated Graphics :(

Any help would be greatly appreciated.  I like an OS that looks cool, as well as being fast and not too hard to use.  I like what I've seen of Beryl, but want a better understanding of it and to know whether it will work for me or not.  Thanks in advance.

---

### Post by konqueror7 on 2009-02-18
it doesn't come by default, to install...
```
sudo apt-get install emerald
```

download some themes in [http://gnome-look.org]("http://gnome-look.org")
and again in the terminal, after you added the theme in the emerald theme manager...
```
emerald --replace
```

if your card supports 3d acceleration, it would be fine...
(you could also install fusion-icon, this will enable you to control your settings more easily)

---

### Post by gackt on 2009-02-19
1. Beryl is a combined window manager and composite manager written in C using OpenGL to provide acceleration. ITs makes your desktop look cool but at the same time provide you with some tools to help you increase you level of interaction with your desktop.
2. download it here [http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php)
3. The processor and the memory is ok, what is the integrated video?. Mine is x3100 and it works (i'm not saying super smooth but it works)
4. The super standar package for cool desktop is : AWN or cairo for docking, compiz, emerald and screenlets (like side bar in vista).

---

### Post by igknighted on 2009-02-19
Beryl was a fork of Compiz that was merged back to the original project some time ago.  I would forget beryl, and focus on Compiz.  This is installed by default.  If you use KDE, the default window manager (kwin) can do many of the same effects, so compiz would be unneeded.

If you're graphics card is supported (almost all are once you install the proper drivers), compiz should be enabled automatically.  You may want to install the compizconfig-settings-manager package in order to have a control panel to configure it to your liking.

---

### Post by konqueror7 on 2009-02-19
isn't somehow beryl = emerald nowadays? after compiz-fusion was made? because i think, compiz is already enabled by default, you only need to install proper video drivers, whats missing is the emerald window manager, making my conclusion that it is beryl... ;) 

am i right? correct me if i'm wrong...

---

### Post by igknighted on 2009-02-19
> **konqueror7 said:**
> isn't somehow beryl = emerald nowadays? after compiz-fusion was made? because i think, compiz is already enabled by default, you only need to install proper video drivers, whats missing is the emerald window manager, making my conclusion that it is beryl... ;) 

am i right? correct me if i'm wrong...

Nope, emerald is still emerald like it always has been.  Beryl used to need emerald, as it could not use GTK's window decorations.  But compiz has no such restriction.  Emerald could do some neat theming stuff and hence it is still around (and in some ways is a remnant of beryl), but all emerald does is draw the window decorations, it is not the whole window manager.

---

### Post by konqueror7 on 2009-02-19
> **igknighted said:**
> Nope, emerald is still emerald like it always has been.  Beryl used to need emerald, as it could not use GTK's window decorations.  But compiz has no such restriction.  Emerald could do some neat theming stuff and hence it is still around (and in some ways is a remnant of beryl), but all emerald does is draw the window decorations, it is not the whole window manager.

ah okay, so beryl is not emerald only that beryl and emerald are related? thanks for the clarifications...:D

---

