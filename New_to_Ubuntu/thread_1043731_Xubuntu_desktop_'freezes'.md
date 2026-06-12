---
title: "Xubuntu desktop 'freezes'"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by POWMS on 2009-01-18
Hello
I may have 'broken' my Xubuntu Heron installation.
I thought I would try and install MPlayer thru a downloaded .deb file. When I double clicked on it the package installation window opened then reported an installation error.
Since then I can boot Xubuntu but if I try to run any applications the desktop freezes and the hard drive light is flashing furiously.
I have to turn off the laptop as all commands are frozen. I have left the laptop on for several hours in the 'frozen' mode with no improvements.
Any Ideas?
Should I try and reload Xubuntu from the original iso file (CD)?
Thanks.

---

### Post by yeats on 2009-01-19
You can drop to a login shell by typing Ctrl-Alt-F1, which will at least allow you to get in and troubleshoot.  You might try

```
sudo dpkg-reconfigure mplayer
```

you could also check the dpkg logs:

```

less /var/log/dpkg.log
 
```

which shows a step-by-step of how each package has been installed.

Post back if that doesn't help . . .

---

### Post by POWMS on 2009-01-20
Chris
I tried gdebi-gtk for an error report. This is what I got in Terminal:

/usr/lib/python2.5/site-packages/apt/_init_init_.py:18: futurewarning:apt api not stable yet
warnings.warn ("apt api not stable yet", futurewarning)
/usr/lib/python2.5/site-packages/gdebi/gdebi.py:93: gtkwarning: gdk_window_set_cursor:assertion 'gdk_is_window (window)' failed
self.window_main.set_sensitive (false)

I had to type this as most applications are frozen. Some letters are in capitals but I didn't note which ones.
hope this helps.

---

### Post by POWMS on 2009-01-21
No takers?
Since it looks like Python 2.5 is unstable, should I attempt to load 2.6.1 which I downloaded (at work)? Or is that not a good idea?
Is there a way to fix/make stable 2.5?
Thanks.

---

### Post by EnGorDiaz on 2009-01-21
nope it looks like a dependancy error

what you do is

```
sudo synaptic
```

in terminal and check the broken package filter and completely remove it

---

### Post by cardinals_fan on 2009-01-21
In the future, you should install packages through the Synaptic Package Manager or apt-get, the command-line application that works behind the scenes.  These tools will automatically handle dependencies and security updates.

---

### Post by POWMS on 2009-01-22
cardinals
yes, I've learnt my lesson! I won't do that again.

---

