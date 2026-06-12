---
title: "Lubuntu network manager"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by CheeseEatingBulldog on 2009-09-23
I have installed the LXDE window manager package, and I must say it works 200% faster than ubuntu or even xubuntu on my Gf's acer netbook. Only thing is....I can't seem to find anyway of connecting to anything, as there is no network manager. Any pointers as to where I can find that?

---

### Post by mac9416 on 2009-09-23
Hit <alt><f2> and run
```
nm-applet
```
The connection applet will show up in the panel's system tray.

To make nm-applet run at startup, add "nm-appet &" to ~/.config/openbox/autostart.sh.

---

### Post by meditatingfrog on 2009-09-28
> **mac9416 said:**
> Hit <alt><f2> and run
```
nm-applet
```
The connection applet will show up in the panel's system tray.

To make nm-applet run at startup, add "nm-appet &" to ~/.config/openbox/autostart.sh.

I put nmapplet in ~/.config/openbox/autostart.sh and that didn't work.  I just appended the ' &' to the end of the nm-applet.  If this doesn't work, I'll try nm-appet.

Thanks for this.

---

### Post by meditatingfrog on 2009-09-29
I wish I had better news regarding nm-applet.  Tried nm-applet & but that didn't work in the file.  I must've done something wrong.  I'll try other suggestions if anyone is interested in seeing what will end up working :o.

Otherwise...

I gave up on LXDE, and moved back to Gnome.  I originally moved to LXDE for two major reasons: the hope of better performance, and to get away from a problem in Gnome of apps starting up without me wanting them to.  I solved the 2nd problem, and performance, well, I don't really want to get into that quagmire.  

But in the end, I'm keeping LXDE as a backup (I think it's good to have for troubleshooting), and knowing about nm-applet (via alt-f2) makes it even more useful to have installed.  I've tried installing kubuntu-desktop, but that's a whole 'nother thread.

---

### Post by kerry_s on 2009-09-30
> **meditatingfrog said:**
> I wish I had better news regarding nm-applet.  Tried nm-applet & but that didn't work in the file.  I must've done something wrong.  I'll try other suggestions if anyone is interested in seeing what will end up working :o.

Otherwise...

I gave up on LXDE, and moved back to Gnome.  I originally moved to LXDE for two major reasons: the hope of better performance, and to get away from a problem in Gnome of apps starting up without me wanting them to.  I solved the 2nd problem, and performance, well, I don't really want to get into that quagmire.  

But in the end, I'm keeping LXDE as a backup (I think it's good to have for troubleshooting), and knowing about nm-applet (via alt-f2) makes it even more useful to have installed.  I've tried installing kubuntu-desktop, but that's a whole 'nother thread.

nm-applet is set to only show in gnome, visit the lxde site for instructions.
[http://wiki.lxde.org/en/LXSession](http://wiki.lxde.org/en/LXSession)

---

### Post by meditatingfrog on 2009-09-30
> **kerry_s said:**
> nm-applet is set to only show in gnome, visit the lxde site for instructions.
[http://wiki.lxde.org/en/LXSession](http://wiki.lxde.org/en/LXSession)

The instructions in this site worked fine, except for one caveat, the location of nm-applet.desktop was in /etc/xdg/autostart.  Once I added lxde to the OnlyShowIn line, nm-applet started up in LXDE automatically.

---

