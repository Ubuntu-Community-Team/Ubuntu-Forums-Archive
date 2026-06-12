---
title: "Gnome terminal problems"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by kogger on 2009-02-14
I had another topic about [this problem](http://ubuntuforums.org/showthread.php?p=6728740#post6728740), although I think I may have isolated the problem a little more.

My original problem was trying to launch a custom script with an application launcher (using gnome-terminal -e "command"). It would work with commands like "man" for some reason, but anything else would either get a child process error (if I tried to use the java or javac command, for example), or the window would immediately close (even if I appended "read" to the end of it).

I've also tried  launching a command window through jEdit, so basically what I've found is that trying to execute a command through a terminal window, unless you physically type the command into the terminal, doesn't work unless it's a man command.

Is this a bug, or is there actually a way to fix this?

---

### Post by llamabr on 2009-02-14
Sorry.  I don't think this is absolute beginner problem.  Maybe you'll have better luck searching out the correct forum?

---

