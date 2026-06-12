---
title: "Need help gaining permission to something! Plz help"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by mag1strate on 2009-01-08
Hey guys, i need to gain permission to a file called q3config.cfg because I want to save my quake 3 options and i heard that was the solution. the problem is that i do not have permission to access it. They told me to use chown command but i don't know how to do it. plz help.:confused:

---

### Post by x22 on 2009-01-08
sure: try "sudo chown <username>: <filename>"

or you could make it world-executable like this:

"sudo chmod a+rwx <filename>"

in line 1, the colon ':' also changes the group

---

### Post by DGortze380 on 2009-01-09
> **x22 said:**
> sure: try "sudo chown <username>: <filename>"

or you could make it world-executable like this:

"sudo chmod a+rwx <filename>"

in line 1, the colon ':' also changes the group

This is potential a problem... you shouldn't have to change permissions to access the file. Use sudo + your favorite command line editor, or gksudo + your favorite graphical editor.

---

### Post by mag1strate on 2009-01-09
Thanks alot guys for the help!!! It work! Thank you again
:D

---

