---
title: "having conky on desktop at start up"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-08-10
Hi
I have installed conky
when I run it from the terminal I gat this message:
richard@richard-laptop:~$ conky
Conky: desktop window (65) is root window
Conky: window type - normal
Conky: drawing to created window (1000002)
Conky: drawing to single buffer

my question is how do I get conky to run whenever I start open box
I know it got something to do with the etc/xdg/openbox/startup

but I don`t know what the correct instruction is
does anyone know?

---

### Post by distortedecho on 2009-08-10
Does this help?

```
http://ubuntuforums.org/archive/index.php/t-386078.html
```

---

### Post by laurielegit on 2009-08-10
Just shove this on top of ~/.xinitrc
```

(sleep 10 && conky) &

#... rest of xinitrc...

```I don't know if you know about this, so I'll go on.

The ~/.xinitrc is a file that is executed every time Xserver (graphical interface) is started. The above command does two things. It waits for ten seconds, and then starts conky. The ten seconds is to give X time to start, and for the rest of your gui to load. It's in brackets to show that the two commands are linked together, and so that when they are executed in the background (indicated by the "&"), it dosn't go like this:

start the X server
execute ~/.xinitrc
wait for 10 seconds
start conky
load the rest of the gui

instead, it is:

start the Xserver
execute ~/.xinitrc
wait for 10 seconds       | start loading the gui
still waiting             | finish loading the gui
load conky

Sorry if you already know that.

---

### Post by Duke Togo on 2009-08-10
good explanation - thanks
one more thing though where is the .xinitrc file?
I tried cd / sudo .xinitrc and it doesn`t exist
should I make a file?

---

