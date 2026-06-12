---
title: "List all installed window managers"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by melopsittacus on 2008-12-20
Hi!

Is there a way to get a list of the window managers actually installed on the system (for instance metacity, compiz, ...)?

---

### Post by Malta paul on 2008-12-20
You might like to check out: [http://wiki.hardinfo.org/HomePage](http://wiki.hardinfo.org/HomePage)

or perhaps the simpler 'Sysinfo' from 'add/remove'

Have fun :)

---

### Post by snova on 2008-12-20
You could look in /usr/share/xsessions, but this doesn't include compiz, and does include several things that are not window managers.

Each file in there represents another kind of X session, such as KDE, wmii, and so on.

It's only an approximation...

---

### Post by melopsittacus on 2008-12-27
Malta Paul, Snova: thanks for help, I am going to have a look at those locations

---

### Post by sdennie on 2008-12-27
Not really, no.  You can get an approximation as stated above but, to put a different spin on your question, how would one query for all possible editors on the system?  You can't.

---

