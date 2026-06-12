---
title: "Two Questions For Ya!"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Bullfrog110MB on 2009-02-19
First, when I go to shutdown Ubuntu 8.04 it hangs for about 5 minutes. I can move the mouse, but can't open anything.

Why this lag?

Second, how do I make GRUB splash screens? I noticed it is a weird file like .os or something like that.

---

### Post by gackt on 2009-02-19
Ok i dont now the first one. For your second question, try to look it here 
[http://www.tldp.org/LDP/LG/current/jayanth.html](http://www.tldp.org/LDP/LG/current/jayanth.html).

---

### Post by mikechant on 2009-02-19
The shutdown problem:

To diagnose this, I would try shutting down from a terminal.
Use CTRL-ALT-F1 to get a terminal.
Log in with your usual id and password.
Type

sudo shutdown -h now

Hopefully, the messages you get should give a clue as to what is hanging up the shutdown process.

Incidentally, if you have more than one problem, it's best to open a thread for each problem with a meaningful title for each rather than lump them together. Otherwise one of the problems may not get any answers.

---

### Post by Bullfrog110MB on 2009-02-19
Thanks!
Seems there was a problem with my startup manager.

All fixed!


I also thank you for I have now created my own splash just the way I want it!

---

