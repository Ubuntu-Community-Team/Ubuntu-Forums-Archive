---
title: "Gnome-shell and Do"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by susanpenter on 2010-02-05
I have recently altered a command to have gnome-shell launch at startup which I really like. However Gnome Do also auto launches and sits in the middle of all my screens and I can't shift it. I am having to scroll up or down to see what I am typing below it. When I had the standard tool bar across the top I would use the kill function to get rid of this but within Gnome-shell I can't find how to do this (and in desperation I can't remember what was written in the command line before Gnome-shell to revert back to keep using kill (not that I want to do that!)

Very grateful for any advice,

Susan

---

### Post by nhasian on 2010-02-05
isnt there a setting in gnome-do to tell it to startup in hidden mode where it doesnt put its splash window on the screen?

also you might like to try docky.  i'm quite happy with it :)

you can also press Alt-F2 and type:

```
xkill
```

or 

```
killall gnome-do
```

---

### Post by susanpenter on 2010-02-05
killall gnone-do has got rid of it thanks. I worried it may stop the search part of gnome-shell working but they must be independant of each other.

Many thanks, I'll try and find a way to tell it to start hidden (or not at all!)

Many thanks

---

