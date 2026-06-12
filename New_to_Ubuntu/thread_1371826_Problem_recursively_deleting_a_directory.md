---
title: "Problem recursively deleting a directory"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by akelsall on 2010-01-03
I'm having a problem deleting a folder named "personal" off of root. When I try, I get the following error:

[INDENT][COLOR="Blue"]
user@host:/$ sudo rm -R /personal/
rm: cannot remove directory `/personal': Device or resource busy[/COLOR][/INDENT]

I tried closing all terminal windows and jumping to the shell (Ctrl+Alt+F1) with the same result. Any ideas?

Thanks,

Andy

---

### Post by dwasifar on 2010-01-03
Does the problem survive a reboot?

---

### Post by mkoehler on 2010-01-03
Do any background applications require use of the data within this directory?  If so, that's probably your problem.  Otherwise, logging out and going to a shell (tty1) [then carrying out your operation] should solve your problem.

---

### Post by Some Penguin on 2010-01-03
Is /personal a mount point?

---

### Post by akelsall on 2010-01-04
> **Some Penguin said:**
> Is /personal a mount point?

BINGO! That's it. It IS a mount point. Thanks for pointing me in the right direction. I even pulled up Gparted last night and saw it, but no light bulb went off haha. 

Thanks again,

Andy

---

