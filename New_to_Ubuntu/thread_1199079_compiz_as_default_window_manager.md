---
title: "compiz as default window manager"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by tessk on 2009-06-28
Hi. I'd like to set Compiz as my default window manager. Am I right in thinking I can do this through        the file                    /etc/X11/default-display-manager ? Right now that file contains /usr/sbin/gdm . What can I change the file to so that it's Compiz?

I'm on Jaunty

Thanks!

---

### Post by mikewhatever on 2009-06-28
No. GDM is a login manager. The default window manager in Ubuntu/Gnome is metacity. You can change is to compiz using **compiz --replace** command. There is also a GUI option under System->Preferences->Appearance, Visual Effects tab.

---

### Post by tessk on 2009-06-28
thanks mikewhatever. the compiz --replace i would like to run at startup though, and putting that in my Startup Apps doesn't seem to work on startup. also, when i set the Visual Effects, it defaults back to 'none' on startup.

---

### Post by tessk on 2009-06-28
ps i have setup a keyboard shortcut to load compiz, but i'd rather have it load it automatically at startup.

---

### Post by starcraft.man on 2009-06-28
Do you have your display driver installed? That's usually the reason it defaults to nothing? Please don't be in a rush, patience is the key with Linux.

If you didn't install your driver, go System > Admin > Hardware Drivers. If it's installed and configured properly, you shouldn't have trouble with the visual effects tab.

Edit: Misread, rewrote.

---

