---
title: "Logged into tty8"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-03-15
I ran the uptime command and wondered why it said there was 2 users logged in, i turned to good ol' google and its because one login is for the gui and one login is for the terminal im using to run the command, to test this i logged out and switched to tty2 and ran uptime again, hey excellent, 1 user, case closed. However when i switched back to tty7 it was blank, huh??? i switched around and found my desktop had moved to tty8, why would this happen, its always been tty7?

Also can someone please explain exactly what the tty's are, ive often wondered, are they like different virtual machines?? could you run 2 or more desktops on different tty's, if not what else are they for because i cant imagine people regularly need 7 different terminals???

---

### Post by r-senior on 2011-03-15
TTYs date back to the days when computers were large expensive beasts that sat in locked rooms. Dumb, 80x24, monochrome, character-mode terminals were strung into them with cables and each user had their own. Switching TTYs on your machine is a bit like moving from a terminal on one desk to another terminal on another desk.

Then Windows 3.1 came along and terminals were sacrificed en masse as everyone got PCs ...

---

### Post by CaptainMark on 2011-03-16
Good history lesson, so they are more or less obsolete, thanks

---

### Post by cguy on 2011-03-16
Actually they aren't.
You could use them to organize your work.

---

