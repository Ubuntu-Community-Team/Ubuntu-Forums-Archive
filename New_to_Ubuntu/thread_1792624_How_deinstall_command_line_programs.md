---
title: "How deinstall command line programs"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by z5um on 2011-06-28
hi

i want to deinstall the standard netcat programm. 

What i tried so far

sudo aptitude remove netcat
used the graphical package manager to locate and remove
delete the netcat, nc directories from /bin and usr/bin

but still i can call netcat. Nc seems to be removed. What is the general approach when uninstalling command line programs ?!

---

### Post by mcduck on 2011-06-28
Same as with any other package, "sudo apt-get remove *packagename*".

If your command failed, it's probably because netcat isn't actually included in a package called "netcat".

A quick apt-cache search shows the package "netcat" being a transitional dummy package, and the actual program is provided in the "netcat-openbsd" or "netcat-traditional". (netcat-openbsd is the one that's installed by default)

---

### Post by dFlyer on 2011-06-28
from a terminal enter:

dpkg -l netcat-openbsd

This will show you if it's installed you should also do it for

dpkg -l netcat-traditional

to see if it's also installed.

to remove a program.

sudo apt-get remove "name of package" without the quotes

---

### Post by z5um on 2011-06-28
thx i somehow managed to get what i want. But i think i wont be able to reproduce it -.-
Pretty confusing with all those package managers.

---

### Post by dFlyer on 2011-06-28
Over time you will pick them up. One suggestion I have is to get a small note book and write them down for quick ref. You could also do the same with Note Editor and just keep it on your desktop for ref.

---

### Post by nomko on 2011-06-28
What you also can do the next time, go to synaptic and check left below under **Origin** and then under **All** (left top of main screen) in the list click on **Local**. Mostly i find the programs there which i installed manually.

---

