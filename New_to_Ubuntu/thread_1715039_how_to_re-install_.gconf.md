---
title: "how to re-install .gconf"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by seattle vic on 2011-03-26
So in trying to figure out why my mouse was not working, I came across a post that suggested to eliminate .gconf.  I renamed it and when I rebooted the desktop came up like a new install.

I solved the problem and then renamed the directory back to .gconf, but nothing happened; it's still like day one.  How to I get gnome to look for this directory and all the config info inside it?

Thanks in advance...

---

### Post by Mr Stoozer on 2011-03-26
> **seattle vic said:**
> So in trying to figure out why my mouse was not working, I came across a post that suggested to eliminate .gconf.  I renamed it and when I rebooted the desktop came up like a new install.

I solved the problem and then renamed the directory back to .gconf, but nothing happened; it's still like day one.  How to I get gnome to look for this directory and all the config info inside it?

Thanks in advance...

If i understand correct, just move the **current** .gconf folder and then move the old one back in, restart X and you should be good (i only did this today with a horrid Windows 7 theme i installed).  Any issues, just swap them around again.
Hope this helps.

---

