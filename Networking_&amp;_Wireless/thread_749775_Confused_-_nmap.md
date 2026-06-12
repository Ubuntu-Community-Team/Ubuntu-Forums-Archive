---
title: "Confused - nmap"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by DGortze380 on 2008-04-08
I hope this is in the right section, couldn't decide between Beginner and Networking.

Anyways... I'm working on another lab for a shell scripting class. The script is relatively easy, but I'm having trouble with nmap (never used it before, still confused after reading the man pages and tutorials)...

I have firestarter install and working.  From firestarter I know (for example) ports x y and z are open on various services.  But when I run: nmap localhost  it only returns port x open.  what am I doing wrong here?

---

### Post by pytheas22 on 2008-04-08
Are you positive the ports are open, and you're not doing anything to try to conceal that?  When I scan localhost with nmap it identifies the open ports correctly.  Also make sure you're running nmap with the correct arguments; it will give different results depending on how you tell it to scan.  If you've never used it before, you might benefit from nmapfe, a decent GUI that also clearly shows you what command-line options it's using for each type of scan.  To install it:

```

sudo apt-get install nmapfe
```

---

