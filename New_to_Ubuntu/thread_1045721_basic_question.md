---
title: "basic question"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by tongueman on 2009-01-20
Is there an equivalent of the 'ctrl alt del' for ubuntu/linux?

Or some kind of task manager if all is not responsive?

---

### Post by perlluver on 2009-01-20
> **tongueman said:**
> Is there an equivalent of the 'ctrl alt del' for ubuntu/linux?

Or some kind of task manager if all is not responsive?

Ctrl+Alt+Backspace will restart the xserver, there is a task manager, under System>Administration>System Monitor.  If all else fails, a light restart of the system can be done via Ctrl+Print Screen+Alt+REISUB.  That will make the machine shutdown and restart gently.

---

### Post by goinglinux on 2009-01-20
If you are looking for a way to kill a single application that has become unresponsive, this article gives a few options:

[http://goinglinux.com/articles/KillRunawayProcess.html]("http://goinglinux.com/articles/KillRunawayProcess.html")

---

### Post by donkyhotay on 2009-01-20
Depends what you're trying to do. If the system becomes completely unresponsive then you generally want to use ctrl-alt-f# (where # is any number between 1 and 6) and it will (hopefully) take to the CLI where you can try to repair the problem. Once you've killed the process or otherwise fixed the problem you press ctrl-alt-f7 to return back to the GUI.

---

