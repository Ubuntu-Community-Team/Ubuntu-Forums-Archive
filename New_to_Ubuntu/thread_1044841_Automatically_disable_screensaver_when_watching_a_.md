---
title: "Automatically disable screensaver when watching a video"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by h2o4444 on 2009-01-19
Is there a way to automatically disable screensaver when watching a video full screen? XP didn't have this problem and there are no controls in the Screensaver program that does it. I would like the screensaver to be on at all times except when I'm watching an online video, a movie, or a DVD.

Thanks!

---

### Post by x33a on 2009-01-19
if you are viewing the movie offline, then vlc and mplayer have this option to disable screensaver while playing video.

---

### Post by h2o4444 on 2009-01-24
I see, but does Ubuntu itself have a global option to do that? Most of the time I'm watching videos on the internet like [hulu.com]("http://hulu.com") or [casttv.com]("http://casttv.com")

---

### Post by diablo75 on 2009-01-24
If you go to System>Preferences and the RIGHT-click on Screensaver, you can add a shortcut/launcher for it to your upper panel so if you head to Hulu or something you can turn the screensaver off manually with a couple clicks.  I don't think there's any global setting for disabling your screensaver while a flash video is playing.

---

### Post by h2o4444 on 2009-01-24
I just submitted this idea to the Ubuntu Brainstorm and hopefully someone can include it in the 9.04 version.

---

### Post by gjoellee on 2009-01-24
If you abselutely want screensver on just rember to move your cursor 1mm or more once in a while

---

### Post by jkernsjr on 2009-03-08
I happen to come across another post concerning the same sort of thing. ([http://ubuntuforums.org/showthread.php?t=428967](http://ubuntuforums.org/showthread.php?t=428967)) While I hope Adobe comes up with some sort of way they automatically tell Gnome to disable the screensaver while in use, this can be a workaround until then.

What I did is just create two Custom Application Launchers and put them on the panel. One named Screensaver Enable with the following command:

```
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool true
```

and the other named Screensaver Disable with the following command:

```
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false
```

Works like a charm to enable/disable the screensaver with a single click!

---

### Post by rafac24 on 2009-03-08
> **jkernsjr said:**
> I happen to come across another post concerning the same sort of thing. ([http://ubuntuforums.org/showthread.php?t=428967](http://ubuntuforums.org/showthread.php?t=428967)) While I hope Adobe comes up with some sort of way they automatically tell Gnome to disable the screensaver while in use, this can be a workaround until then.

What I did is just create two Custom Application Launchers and put them on the panel. One named Screensaver Enable with the following command:

```
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool true
```

and the other named Screensaver Disable with the following command:

```
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false
```

Works like a charm to enable/disable the screensaver with a single click!

Cool !

---

### Post by rburkartjo on 2009-03-08
raf tks for that last post will try that

---

### Post by sdennie on 2009-03-08
It should be possible to completely automate this (screensaver automatically turns off whenever firefox is using flash) using /proc, a daemon and the gconf settings above.  I'll write a HOWTO later today and post a link to it in this thread.

---

### Post by sdennie on 2009-03-08
As promised: [http://ubuntuforums.org/showthread.php?t=1090393](http://ubuntuforums.org/showthread.php?t=1090393)

---

### Post by h2o4444 on 2009-03-18
Thank you for your help. I'm going to wait until Ubuntu 9.04 to come out and see if the problem still persists.

---

### Post by CCC999 on 2010-06-13
just install Caffeine - works well to temporarily disable screensaver with one click.

---

