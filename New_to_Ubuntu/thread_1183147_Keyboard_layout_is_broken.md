---
title: "Keyboard layout is broken"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by AndrewYY on 2009-06-09
My fresh installation of ubuntu 9.04 has a broken keyboard layout. Whenever I try to type the @ symbol (shift-3) it ends up turning into " and when I try to type ?, it ends up being É, and so on.

I guess it pays to say I installed ubuntu via the downloadable version of wubi.

Im not having problem with most of the other keys, but what the heck is wrong... Its hard to even type this post with proper punctuation :P

---

### Post by dioltas on 2009-06-09
Try typing 
> sudo setxkbmap uk
in a terminal.

If that fixes it add the command to your .xinitrc file.
The easiest way to do that would probably be to open a text editor, browse to your home folder and open .xinitrc. Then just add 

> setxkbmap uk &
on a line on it's own before the last line (which is probably something like exec gnome-session)

Hope that works.


**Edit: **Oh ya, for the console you might have to change the line KEYMAP="whatever" to KEYMAP="uk" in /etc/rc.conf
you'll need root privileges for that mind! Also, it doesn't have to be uk, depending on where you are. For me it's ie :)

---

