---
title: "Wine"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by anirup on 2009-04-07
**can virus affect a wine installation.is there any way of repairing it other than by completely removing and then reinstalling.**

---

### Post by linux_lover69 on 2009-04-07
I think I read somewhere that viruses could hurt it. If I can find the thread I'll post it.

---

### Post by linux_lover69 on 2009-04-07
Found it.

[http://ubuntuforums.org/showthread.php?t=1083222&highlight=viruses+wine](http://ubuntuforums.org/showthread.php?t=1083222&highlight=viruses+wine)

---

### Post by Hospadar on 2009-04-07
It's *extremely* unlikely.  Maybe if you were using internet explorer in wine (which for the life of me I can't imagine why you would want to do that other than for website compatibility) then maybe maybe you might get something that might compromise only internet explorer.

Most viruses attach themselves to a low level of the system so they can operate independently, and be started up on boot.  Wine is just a program loader, it doesn't have any of the same low-level components and windws.  So while it's hypothetically possible that a virus might be able to copy itself into your wine system directory (the .wine directory in your home directory that mimics the c drive), wine would never run it, and nothing bad would ever happen.

The bottom line is,
you have absolutely nothing to worry about in this departement.  A virus would have to be very specially crafted to infect through wine, and it would have to be very different from a windows virus.  If I was a malware writer, I would certainly want to target a larger audience than the (probably) <.5% of computer users who use a certain windows application through wine in linux.

---

