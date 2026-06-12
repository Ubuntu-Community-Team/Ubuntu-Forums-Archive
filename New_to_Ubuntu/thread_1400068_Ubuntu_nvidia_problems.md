---
title: "Ubuntu nvidia problems"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by hombrebeastia on 2010-02-06
I have an acer 5520 and I just put Ubuntu 910 on it, and my screen keeps splitting and breaking in full screen mode. I have configured and checked my screen settings, but every time I try to full screen anything I'm watching, the screen begins to flip and split down the middle horizontally.
Help please.

---

### Post by nhasian on 2010-02-06
open a terminal from applications->accessories->terminal

update your system with:

```
sudo apt-get update && sudo apt-get upgrade
```

you may need to reboot afterwards.  Then check to see if you can enable any hardware drivers for your nvidia card by pressing Alt-F2 and entering:

```
sudo jockey-gtk
```

---

