---
title: "Tomatoes just installed, doesn't work"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by dwiedenfeld on 2009-02-27
I just installed tomatoes ("I Have To Tomatoes") and it doesn't work. It appears in the Applications > Games menu, Synaptic says it's installed, but when I try to start it, the screen sort of briefly flashes, then nothing. Doesn't seem to appear in the list of processes, either.

By the way, Iu just tried to install and run TORCS; same thing. 

Any ideas?

---

### Post by snova on 2009-02-28
Try running it from a terminal, and post the output:

```
tomatoes
```

---

### Post by dwiedenfeld on 2009-02-28
```
Error appeared:
 - Unable to set the OpenGL video mode 800 x 600 (32 bit)!
Couldn't find matching GLX visual
```

This is all I get.

---

### Post by snova on 2009-02-28
Perhaps OpenGL isn't working?

```
glxinfo | grep direct
```

What kind of video card do you have?

Try it with TORCS too (might get a different error):

```
torcs
```

---

### Post by dwiedenfeld on 2009-03-01
When I run the "glxinfo | grep direct", I get this (although it repeats the first line several times):

```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
```

When I run "torcs" I get this:

```
TORCS location not found
```

Doesn't mean much to me.

---

### Post by dwiedenfeld on 2009-03-01
Oh, and the video card is something nVidia, using the "nv" driver in xorg.conf.

---

### Post by bwang on 2009-03-02
You have to use the "nvidia" driver. Look under System>Administration>Hardware Drivers.

---

### Post by dwiedenfeld on 2009-03-02
Oh--bad news. The nvidia driver crashes this machine. That's why I have to use nv.

Any other solution?

---

