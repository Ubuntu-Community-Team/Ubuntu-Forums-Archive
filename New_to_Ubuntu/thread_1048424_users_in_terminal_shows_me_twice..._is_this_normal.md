---
title: "users in terminal shows me twice... is this normal?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by sum janus on 2009-01-23
Hi,

Just trying to get a bit more acquainted with my terminal :-) .  When I give the "uptime" command in bash it tells me that there are two users running.  When I put in "users", it lists my username twice.

Is this normal, and if not, is this bad slash how do I fix it?

Thanks,
Eric

---

### Post by drs305 on 2009-01-23
Yes, it is normal. Run 'users', then open 2-3 more terminals and run "users" again. You will see it increases by the number of terminals you opened, since you are essentially 'logging in' each time you open a terminal.

---

### Post by taurus on 2009-01-23
In other words, when you log in, there is one user.  And when you open a terminal, that is another user.

---

### Post by sum janus on 2009-01-23
Ok.  So if I understand it right, should the command be run when I'm not in the terminal, I would only show up once -- likewise, it would only show up once if I was only in the terminal, not in GNOME?

---

### Post by northern lights on 2009-01-23
> **sum janus said:**
> Ok.  So if I understand it right, should the command be run when I'm not in the terminal, I would only show up once -- likewise, it would only show up once if I was only in the terminal, not in GNOME?
The terminal is a GUI shell emulator. If you were to boot to the shell only, yes, you'd only show up once.

---

