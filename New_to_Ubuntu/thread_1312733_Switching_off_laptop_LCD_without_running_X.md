---
title: "Switching off laptop LCD without running X"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by harisund on 2009-11-03
I recently received a laptop, and I installed Ubuntu on it. However, it's a slow machine and I will mostly be using command line apps, never the GUI (IRSSI, Torrents, apache, file server etc).

Therefore, I don't see the need to start Gnome up.

But the problem is, shutting the monitor down. If X is running, the screensaver shuts the monitor down, or I can do something like xset dpms force off, but if I login simply to the terminal and not start GDM, how do I turn off the monitor?

Any ideas? (I don't want to start Gnome for memory purposes)

---

### Post by LowSky on 2009-11-03
Use the server edition, it doesn't have a gui installed by default

---

### Post by sisco311 on 2009-11-03
```

sudo vbetool dpms off
sudo vbetool dpms on

```

i've found a useful script on the Arch forums: 
[http://bbs.archlinux.org/viewtopic.php?id=66169]("http://bbs.archlinux.org/viewtopic.php?id=66169") (post #12)

you can edit the sudoers file to allow your user to run the script without a password: 
[thread=1132821]HowTO: Sudoers Configuration[/thread]

---

### Post by pythonscript on 2009-11-03
If you just want to install a command line only version, just use the alternate install CD, press F4 at the start of the install and select "Install command line only version." Then, you can just manually install gnome (or lxde, if you're worried about memory consumption) and start is manually with startx.

---

### Post by alphaniner on 2009-11-03
In my experience the video signal will eventually 'shut off' even in text mode, but I don't know what the timeout is or how to configure it.  I'm fair sure I've seen this with a standard desktop install of Ubuntu, but it may have been another distro.

---

### Post by harisund on 2009-11-03
> **LowSky said:**
> Use the server edition, it doesn't have a gui installed by default

> **pythonscript said:**
> If you just want to install a command line only version, just use the alternate install CD, press F4 at the start of the install and select "Install command line only version." Then, you can just manually install gnome (or lxde, if you're worried about memory consumption) and start is manually with startx.

I don't think either of you got what I was trying to say. 

> **alphaniner said:**
> In my experience the video signal will eventually 'shut off' even in text mode, but I don't know what the timeout is or how to configure it.  I'm fair sure I've seen this with a standard desktop install of Ubuntu, but it may have been another distro.

From what I see, the screen "blanks out" but it doesn't "stop receiving power". The LCD screen is still lit. 

> **sisco311 said:**
> ```

sudo vbetool dpms off
sudo vbetool dpms on

```

i've found a useful script on the Arch forums: 
[http://bbs.archlinux.org/viewtopic.php?id=66169]("http://bbs.archlinux.org/viewtopic.php?id=66169") (post #12)

you can edit the sudoers file to allow your user to run the script without a password: 
[thread=1132821]HowTO: Sudoers Configuration[/thread]

YOU ARE AWESOME DUDE !

vbetool was just what I was looking for. Solves my problem perfectly. 

And so, Ubuntu forums continues its trend of never letting me down.

---

