---
title: "gnome-terminal not respecting default shell"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by lamalex on 2009-11-06
I have my default shell set to zsh, my /etc/passwd lists zsh as my shell
> 
alex:x:1000:1000:Alex Launi,,,:/home/alex:/usr/bin/zsh

and when I hit ctrl-alt-fX to get to a tty, the login shell is zsh. The problem is gnome-terminal/other terminal emulators. They're spawning bash as their shell! I can't figure out why, this has never been an issue in the 5+ years I've been using Ubuntu and zsh. Can anyone help me figure out what's different in Karmic that this is happening?

---

### Post by _khAttAm_ on 2010-02-13
Had the same problem with Lucid. I logged out and logged back in and gnome-terminal now launches zsh with it.

---

