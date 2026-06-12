---
title: "record high definition screencasts in ubuntu linux"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by phoda on 2010-04-07
hi!

how can i record high definition screencasts (at least 720p) in my ubuntu system?

---

### Post by HDave on 2010-04-07
Check out the package "gtk-recordmydesktop" you can install from Synaptic or the command line via:

```
sudo aptitude install gtk-recordmydesktop
```

Works great.

---

### Post by pranavnatu on 2010-04-08
When i installed 'Record my desktop, it works only when the desktop effects are set to 'none' if i set them to normal or extra it do not capture any window it just shows the wallpaper.
Any pointer on how to get the things like 'zoom in' 'zoom out' on perticular text/screen area getting captured with recordmydesktop application.?
 
ciao,
Pranav

---

### Post by HDave on 2010-04-09
Compiz breaks tons of stuff...including opengl games, skype, virtual machines, etc.  I love it, but I frequently find myself disabling it.

In terms of dynamically zooming in and out...i don't know of anything that does that while you are recording...you do that afterwards in video editing.

In terms of zooming in to capture just one window...it does that...check the settings -- it'll give you a red rectangle that shows what you are recording.

---

### Post by verb3k on 2010-04-09
High Quality screencasting on Linux:
[http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)

---

### Post by pranavnatu on 2010-04-10
> **HDave said:**
> 
In terms of dynamically zooming in and out...i don't know of anything that does that while you are recording...you do that afterwards in video editing.


Thanks, that is an ultimate option of editing the video after recording... buts on youtube there are many videos where the compiz fusion effects are recorded using recordmydesktop... 
its not working on my machine though... Any idea if running Ubuntu on virtual box is limiting the full capacity of recordmydesktop?

---

### Post by pranavnatu on 2010-04-10
> **verb3k said:**
> High Quality screencasting on Linux:
[http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)

Thanks .. but I am kind of newbie yet, and the tutorial has got too much of commands/parameter passing.. I will definitely use this when I become comfortable with command line options.

:)

---

### Post by 3rdalbum on 2010-04-10
There is an option in 'recordmydesktop' that is designed for use with Compiz - in fact, I believe it should be enabled automatically when it detects a composited window manager. Maybe check the man page?

```
man recordmydesktop
```

---

### Post by Skidbladnir on 2010-04-11
> **HDave said:**
> Compiz breaks tons of stuff...including opengl games, skype, virtual machines, etc.  I love it, but I frequently find myself disabling it.

In terms of dynamically zooming in and out...i don't know of anything that does that while you are recording...you do that afterwards in video editing.

In terms of zooming in to capture just one window...it does that...check the settings -- it'll give you a red rectangle that shows what you are recording.
Super + Scroll zooms in and out in Ubuntu, I believe.  By the way, Super is the same as Command on a Mac and the Windows key on, what else, Windows.

---

### Post by nehaljwani on 2012-10-09
You can see a tutorial on how to use ffmeg to do screencasts on linux here: [https://www.youtube.com/watch?v=B-ry-f3Mpx4](https://www.youtube.com/watch?v=B-ry-f3Mpx4)

---

### Post by lisati on 2012-10-09
Old thread closed

---

