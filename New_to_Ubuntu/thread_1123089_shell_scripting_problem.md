---
title: "shell scripting problem"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by KCormier on 2009-04-11
Hey all.  I have a little shell script I wrote to open a program with a few things preconfigured.  My only issue is that when I click on it, it opens up a dialog that asks if I want to display it, run it, run it in terminal, or cancel.  In order to add it as an application I need it to just run automatically.  Anyone know how to fix this?

-Kevin

---

### Post by arsenic23 on 2009-04-11
I think all you have to do is make a launcher that runs it.

---

### Post by KCormier on 2009-04-11
Got it.  I thought I knew what you meant so I did a little research.  I just realized the bug wasn't in the launcher, it was in my script.  I had used a relative path instead of a full path and thus one call wasn't working and my script would die.  Got it fixed now.  Thanks for the help!

-Kevin

---

