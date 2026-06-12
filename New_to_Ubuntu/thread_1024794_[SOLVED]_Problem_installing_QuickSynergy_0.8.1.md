---
title: "[SOLVED] Problem installing QuickSynergy 0.8.1"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by AndrewS on 2008-12-29
Hello

I've been trying, without success, to get QuickSynergy 0.7 working (I have a  desktop running 8.10 and a laptop running 8.04; the desktop is connected to the router with a cat5 cable, the laptop has a wireless connection).  I downloaded the tarball, extracted it and ran ./configure.  I got the following (fatal?) error message:

[INDENT][/INDENT]configure: error: GTK+ >= 2.6.0 not installed

When I try to run make or make install, I get told there are missing arguments.

Any suggestions welcome.

Andrew

---

### Post by shearn89 on 2008-12-29
i think:
```

sudo apt-get install libgtk2.0-dev

```
should fix this.

---

