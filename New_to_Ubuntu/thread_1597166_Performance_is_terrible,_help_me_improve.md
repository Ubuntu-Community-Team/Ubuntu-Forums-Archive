---
title: "Performance is terrible, help me improve"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Luke M on 2010-10-15
I'm trying to run Ubuntu 10.10 on a Pentium II 400 with 512MB RAM. The GUI is really, really, slow. Painful. I don't expect Ubuntu to be as fast as Windows XP (which is zippy on the same machine), but I think Ubuntu can be tweaked to be faster.First problem is color depth. I assume it's using 32-bits by default. How do I change to 16-bits?Secondly, how do I find out what graphics card driver is being used and whether it is using hardware blitting, hardware cursor, and so forth?On the positive side, Ubuntu did auto-detect my monitor and used the native LCD resolution. So that worked nicely.

---

### Post by Sef on 2010-10-15
With your specs, I would specs, I would use Xbuntu. With your processor, I doubt it would be that much faster, even if you added more ram.

---

### Post by lorderico on 2010-10-15
Hello Luke,

I would not expect Ubuntu to run very fast on a Pentium 2 simply because its designed to run on descent computers.  If I were you, I'd try a variety of distros such as puppy linux, fedora, etc... to see what works best.  Also, you may want to go to system->preferences->appearance->visual effects and make sure those are off.  For drivers, do to system->administration->hardware drivers.  I think the biggest indicator of performance is free ram.  Go to system->administration->system monitor and see how much free ram you have.  If it is not much, then it probably won't ever be fast.

Eric

---

### Post by mastablasta on 2010-10-15
switch to clear looks theme and remove and background picture. that should also give some speed.
 
also have you considered Lubuntu? It's much more lightweight than ubuntu.

---

### Post by HermanAB on 2010-10-15
Howdy,

On a machine like that, you have to use Lubuntu or Xubuntu.

---

### Post by NightwishFan on 2010-10-15
I agree. Ubuntu despite being fairly good for legacy machines is getting to the age where the default desktop is too much for old machines. If you are really interested you may even be able to use the alternate cd to install a command line system and build up to a lightweight system from there (pick only what you need). It isn't complicated especially if you understand apt-get and the debian installer.

Simply choose command line only install from the alternate cd options menu (press f4 and choose command line only) Please note you will need a wired internet connection to do this. Ubuntu will install a basic command line system and when installed all you have to do is apt-get the basics. Example:
```
sudo apt-get upgrade && sudo apt-get install xorg synaptic xterm slim icewm midori
```

If you know what packages you need you can replace any of those except for xorg and xterm.

---

### Post by Sealbhach on 2010-10-15
Lubuntu.

.

---

### Post by ibizatunes on 2010-10-15
Lubuntu is the way forward

---

### Post by adwhitenc on 2010-10-15
Lubuntu and/or a new computer(or to be specific, motherboard processor, and ram)

I think you could also install the flux version at [http://fluxbuntu.org/js.html](http://fluxbuntu.org/js.html) my dad got it and now that's virtually all he uses.

---

### Post by Luke M on 2010-10-15
I took the suggestion to try Lubuntu, but it crashes and burns on boot. Doesn't anyone know how to set the color depth? That alone would more than double graphics performance (more than double because the display refresh is using most of the [single ported] video memory bandwidth on the nvidia TNT2-64).

---

### Post by ibizatunes on 2010-10-15
Did you you a check on the CD, maybe the iso your burnt is corrupt?
Did you get 10.10 or 10.04?

---

### Post by NightwishFan on 2010-10-15
First run:
```
sudo Xorg -configure
```

Then press alt+f2 and type:
```
gksudo gedit /etc/X11/xorg.conf
```

Edit the part like this, just change the depth to 16 (i believe)
```
SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection

```

---

