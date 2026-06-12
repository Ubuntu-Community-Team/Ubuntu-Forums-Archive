---
title: "vncserver - how do I change resolution?"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by BikeHelmet on 2009-10-12
Hi. :) I followed this article to get my headless NAS working properly:

[http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx](http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx)

Unfortunately, I set the geometry to 800x600, which is too small. How do I find where the resolution is stored, to change it?

I tried following articles with other ways to get vnc plus a gnome desktop started, but those other methods just leave me with more and more headless desktops running. I need to find wherever the geometry is stored for :0 to change it.

Thanks. :D

---

### Post by s.fox on 2009-10-13
Hello.

I believe that you specify the wanted resolution on the command line when you run it:

```
vncserver :2 -geometry 1024x768 -depth 24
```

I do hope this helps,

-Silver Fox

---

### Post by BikeHelmet on 2009-10-13
Yes, I'm aware of that.

Now how do I find what starts it?

I don't start vncserver; it's always running after a reboot. Since Ubuntu doesn't seem to have an msconfig equivalent, I'm at a loss as to where to look for whatever starts it.

It just magically starts, and all the methods I searched on google are empty files, so anyone know where the geometry command is, and where to change it?

---

### Post by s.fox on 2009-10-13
Hello,

Ubuntu does have the option to autostart programs.  It can be found here:

Go to System > Preferences > Session,Select Startup Programs

-Silver Fox

---

### Post by BikeHelmet on 2009-10-13
Remote Desktop is set to start.

"/usr/lib/vino/vino-server"

I find that strange, because I'm using TightVNCserver, but maybe one depends on the other.

That doesn't tell me anything about where to change resolution? I did track down a %gconf.xml file which has vino settings, but none of them are anything to do with resolution or geometry.

So what's the best way to do this? Turn Remote Desktop off after setting up a script to start vncserver with the right resolution?

---

### Post by BikeHelmet on 2009-10-18
Just posting an update:

I still can't find where the resolution is set, to change it. Every time the computer reboots, it removes my extra vnc desktops except :0

I could set a script to kill :0 and create a new desktop and gnome session, but that seems rather sloppy?

The resolution/geometry settings have to be stored somewhere, right? It doesn't just magically start X and the gnome desktop at 800x600 without following some startup command, right? :P Surely this is findable?


Edit: I clued in that if vino is running, I should try working within X11/Gnome. A thread saying vino's default res is 800x600 tipped me off that it might be a coincidence.

I edited xorg.conf with new resolutions, and it seems to be working. I still don't understand where TightVNCServer fits into all this, but oh well.

Edit2: If xorg.conf resolutions are being ignored over VNC, put refresh rates in for your monitor.
```
Section "Monitor"
	Identifier	"Configured Monitor"
	Option          "DPMS"
	HorizSync	31-95
	VertRefresh	50-60
EndSection
```

---

