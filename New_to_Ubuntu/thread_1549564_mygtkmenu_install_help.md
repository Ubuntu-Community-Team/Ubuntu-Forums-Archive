---
title: "mygtkmenu install help"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by il-luzhin on 2010-08-09
Hey folks,

After following the oh so simple instructions of basically unpacking the tarball, renaming files, and checking permissions I can't get the program to start.  when I type 

myGtkMenu TestMenu.txt

from the containing directory I get command not found.  Could I please get some help?

Thanks

---

### Post by bprins on 2010-08-10
thread already marked as solved. is it solved?

if not, does something like following work from your terminal:
./myGtkMenu TestMenu.txt (note the ./ in front of myGtkMen) 

if not, mark the myGtkMenu as executable:
sudo chmod +x myGtkMenu

---

