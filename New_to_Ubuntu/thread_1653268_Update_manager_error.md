---
title: "Update manager error"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by cazador31 on 2010-12-26
When I use the update manager I always get this message.

"The action would require the installation of packages from not authenticated sources"

I cannot download any update lately. Looking forward for the solution

---

### Post by wojox on 2010-12-26
What does it say when you click on Details? Does it show the opposing packages or ppa?

---

### Post by davidmohammed on 2010-12-26
clicking the details should give you more info - its likely a key needs to be added to your software sources.  You are probably using an untrusted ppa (software source).  

Alternatively - untick the offending software source ppa and update again.

---

### Post by candtalan on 2010-12-26
> **cazador31 said:**
> When I use the update manager I always get this message.

"The action would require the installation of packages from not authenticated sources"

I cannot download any update lately. Looking forward for the solution
I got exactly the same problem the other day, and it was essential to me to download a lot of updates. I was using the UK server for updates (as usual) and so I tried changing my settings in Software Sources (updates) to Main Server.

I then found the the problem simply disappeared.....

(After the heavy update session, I later changed the server back to UK, fwiw).

---

