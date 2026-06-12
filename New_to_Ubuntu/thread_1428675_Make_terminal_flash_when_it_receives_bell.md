---
title: "Make terminal flash when it receives bell"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by harisund on 2010-03-13
How do I do this? 

I am using IRSSI under screen, and it sends out a bell when my nick is hilighted. When the terminal window is minimized, or out of focus or in another workspace (again, out of focus), it should alert me by repeatedly flashing on the taskbar. Putty is capable of it. 

Here are some relevant links - 
[http://mikelward.com/news/2008/11/terminal-that-tells-you-when-its-done.html](http://mikelward.com/news/2008/11/terminal-that-tells-you-when-its-done.html)
[https://bugzilla.gnome.org/show_bug.cgi?id=557593](https://bugzilla.gnome.org/show_bug.cgi?id=557593)
[https://bugs.launchpad.net/gnome-terminal/+bug/272749](https://bugs.launchpad.net/gnome-terminal/+bug/272749)

Is there a comprehensive guide to get it to working? 

1. Apparently xterm supports a -pob option, but doesn't work when minimized or in another workspace.
2. urxvt is supposed to support it, I have no idea how to get it work. 
3. eterm is supposed to support it too, but eterm doesn't work on Ubuntu. Wonder who packaged it. 

Any ideas?

---

### Post by victor.zamanian on 2010-03-13
There are a couple of entries in gconf-editor under /apps/metacity/general that deal with the type.

I'm not sure whether it will make the window flash though. It will definitely not do anything if screen is detached. Maybe you can read the descriptions of some of the bell settings in there and experiment with values. What do you think? Let me know if you need further assistance.

---

### Post by harisund on 2010-03-17
Yeah the visual bell helps, but at most it flashes it once. Doesn't have the steady flash that Putty does on Microsoft OS, for example. 

I decided to use a combination of tail -f, logging to the file and notify-send. 

Oh well. :)

---

### Post by itcotbtoemik on 2010-03-17
xterm's -pob option (see the manpage) "raises" the window,
which is a different feature than de-iconifying.  The
bellIsUrgent resource may be useful.

---

### Post by llamabr on 2010-03-17
you're using screen, right?  I believe the default for screen is to visually tell you which screen you're getting the bell, but to make no noise.

this is from the man page:

```
       C-a C-g     (vbell)       Toggles screen's visual bell mode.
```

it doesn't look like there's a flag to pass at startup, but there are some options to set in your screenrc, if you don't mind if I send you to the man page (I know some people get all bent out of shape around here for such advice).

---

