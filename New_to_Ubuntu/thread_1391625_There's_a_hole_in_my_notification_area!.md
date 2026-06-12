---
title: "There's a hole in my notification area!"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2010-01-27
Files this under "petty annoyances".

About half of the time when I start up my computer, there is a blank space in my notification area.  When I right-click it, I get options for the notification area.  I can't move anything into that space, and if I remove the notification area applet and add it again, the space it still there.

Some things that may be related.

1) I think this may have started around the same time I started using a delay script to start conky.  Prior to that I was just using the command "conky".

2) Sometimes right when I start up there will be two volume control icons, and then one will disappear, leaving the blank space.

3) Sometimes when I start up there will be a minimized "Untitled Window" in my Window List.  It disappears before I can figure out what it is.


Obviously, this isn't an important issue, but if someone knows a fix, it would sure give me peace of mind.

Thanks.

---

### Post by blazemore on 2010-01-27
Yes, that is an important issue. Ignoring papercuts (A bug which isn't major, but negatively impacts usability) can make a distro look amateur.

The simplest thing to do is reset the panel back to their "out of the box" state.
Run the following commands
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by stoogiebuncho on 2010-01-27
> **blazemore said:**
> Yes, that is an important issue. Ignoring papercuts (A bug which isn't major, but negatively impacts usability) can make a distro look amateur.

The simplest thing to do is reset the panel back to their "out of the box" state.
Run the following commands
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

So far so good.  I'll have to restart a couple times before I know for sure if it worked, but it looks good right now.  Thanks for the help.

---

### Post by llawwehttam on 2010-01-27
I thought this was the case but the Ethernet symbol there was exactly the same as the panel color in a badly designed theme. Guess this was not your problem though?

---

### Post by stoogiebuncho on 2010-01-27
> **llawwehttam said:**
> I thought this was the case but the Ethernet symbol there was exactly the same as the panel color in a badly designed theme. Guess this was not your problem though?

Nope, I'm using a different icon set.  Plus, right-clicking on the blank space didn't bring up any program options, only notification-area options.

Hopefully resetting everything fixes it for good.

---

