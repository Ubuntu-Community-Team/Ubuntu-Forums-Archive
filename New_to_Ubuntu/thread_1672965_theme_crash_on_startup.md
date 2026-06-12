---
title: "theme crash on startup"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by DMKryl on 2011-01-21
Hi recently i'm having trouble with the theme of my system, everytime i shutdown and start again the system takes the default theme, i have enter to a terminal and this was the output

```
kryl@Sasha:~$ killall gnome-settings-daemon
kryl@Sasha:~$ gnome-settings-daemon
** (gnome-settings-daemon:2597): WARNING **: Grab failed for some keys, another application may already have access the them.
kryl@Sasha:~$ 
** (gnome-settings-daemon:2597): WARNING **: Got less number of items in credentials hash table than expected!
```

---

### Post by justincwatt on 2011-02-06
Same here. Just started happening within the last week, triggered I assume by one of the recent system updates. I'm also noticing that my computer takes a lot longer to boot, and when the desktop is finally displayed, the default gnome window manager is displayed. When I run gnome-settings-daemon from the command line, the window appearances change to my settings in Preferences > Appearance (Radiance) though the desktop icons do not change. I also get the following output on the command line:

```

$ gnome-settings-daemon
$ Unable to find a synaptics device.

** (gnome-settings-daemon:2530): WARNING **: Got less number of items in credentials hash table than expected!

```

When I reboot, it reverts back to the default "chunky" appearance. So far I have not found any combination of fixes that stick.

---

### Post by speakman on 2011-02-28
I've got this problems as well. See my reply in another thread: [http://ubuntuforums.org/showpost.php?p=10503926&postcount=6](http://ubuntuforums.org/showpost.php?p=10503926&postcount=6)

Why you get that error messages is probably because you don't really kill the gnome-settings-daemon.

In this state, it does not listen to the SIGTERM signal (which is sent by default with killall). You will have to kill it with "killall -KILL gnome-settings-daemon", and then re-starting it.

---

