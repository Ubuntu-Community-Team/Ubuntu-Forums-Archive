---
title: "How to uninstall after compile"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Biddlesby on 2010-08-10
Hello all, I downloaded a source code version of qtpfsgui and compiled it with qmake. But I did it in the downloads directory. Now I want to uninstall it...can I just delete all the files or has it woven itself into my system??

Thanks!

Harry

---

### Post by adwhitenc on 2010-08-10
I would suggest going into synaptic package manager (accesable through System-> administration) and uninstalling it there, if that dosent work, i would try using the terminal command

sudo apt-get remove <program-name>

or 

sudo aptitude remove <program-name>

---

### Post by oldos2er on 2010-08-10
Go back into the qtpfsgui directory and run **sudo make uninstall**

---

### Post by -kg- on 2010-08-10
> **adwhitenc said:**
> I would suggest going into synaptic package manager (accesable through System-> administration) and uninstalling it there, if that dosent work, i would try using the terminal command

sudo apt-get remove <program-name>

or 

sudo aptitude remove <program-name>

That won't work.  The OP didn't install using Aptitude/Apt-Get, so he can't uninstall it that way.

> Go back into the qtpfsgui directory and run sudo make uninstall

Right method, but:

> Hello all, I downloaded a source code version of qtpfsgui and compiled it with qmake. [COLOR="Red"]But I did it in the downloads directory.[/COLOR]

Wouldn't the makefile be in the downloads directory instead of the gtpfsgui directory?

---

### Post by oldos2er on 2010-08-10
> **-kg- said:**
> Wouldn't the makefile be in the downloads directory instead of the gtpfsgui directory?

I assumed the OP meant ~/Downloads/gtpfsgui

---

### Post by jtarin on 2010-08-10
I got it....how about the makefile directory.Go there and run sudo make uninstall

---

