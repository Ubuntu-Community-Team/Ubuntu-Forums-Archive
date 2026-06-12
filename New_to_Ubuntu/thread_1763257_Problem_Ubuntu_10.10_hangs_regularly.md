---
title: "Problem: Ubuntu 10.10 hangs regularly"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by Asger17032 on 2011-05-20
Hi!
A few months ago I installed ubuntu 10.10 on my laptop, and have had no problems with it at all until a few weeks ago, when it started to hang with regular intervals.
It doesnt become completely unresponsive, I can still move between workspaces, and minimize windows, but all open programs becomes completely unresponsive (goes grey).
I cant even open the terminal.
Any help would be greatly appreciated!!! :)

---

### Post by dargaud on 2011-05-20
Try pressing Alt-Ctrl-F2 to drop to a text console, then login and use the usual diagnostics tools to see if you can kill an unresponsive app: top, "ps -ef", kill, "kill -9"...

Then go back to X with Ctrl-Alt-F7

---

